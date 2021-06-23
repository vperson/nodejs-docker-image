FROM centos/nodejs-12-centos7:latest
ARG PYTHON_VERSION=3.8.1

USER root

RUN wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

RUN yum makecache && \
yum install -y net-tools nmap-ncat telnet net-tools jq curl openssl wget openssl-devel kde-l10n-Chinese glibc-common && \
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
yum clean all && \
rm -rf /var/cache/yum && \
rm -rf /anaconda-post.log && \
localedef -c -f UTF-8 -i zh_CN zh_CN.utf8

RUN yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel -y
ENV LC_ALL zh_CN.utf8
ENV TZ Asia/Shanghai

RUN npm install cnpm -g --registry=https://registry.nlark.com

WORKDIR /tmp/python
RUN wget https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tgz && \
tar -zxvf Python-${PYTHON_VERSION}.tgz && \
cd Python-${PYTHON_VERSION} && \
./configure prefix=/usr/local/python3 && \
make && make install && \
ln -s /usr/local/python3/bin/python3.8 /usr/bin/python3  && \
ln -s /usr/local/python3/bin/pip3.8 /usr/bin/pip3

CMD ["node", "-v"]
