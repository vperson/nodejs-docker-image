FROM centos/nodejs-10-centos7

USER root

RUN rm -rf /etc/yum.repos.d/*.repo

COPY CentOS-Base.repo /etc/yum.repos.d/
COPY epel.repo /etc/yum.repos.d/
COPY timezone /etc/
COPY fonts  /usr/share/fonts

RUN yum makecache && \
yum install -y net-tools nmap-ncat telnet net-tools jq curl openssl wget openssl-devel kde-l10n-Chinese glibc-common  bzip2&& \
yum clean all && \
rm -rf /var/cache/yum && \
rm -rf /anaconda-post.log && \
localedef -c -f UTF-8 -i zh_CN zh_CN.utf8 && \
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
export LANG=zh_CN.UTF-8 && \
echo "export LANG=zh_CN.UTF-8" >> /etc/locale.conf

ENV LC_ALL zh_CN.utf8
ENV TZ Asia/Shanghai

WORKDIR /opt/app-root/src

USER default

CMD ["node", "--version"]
