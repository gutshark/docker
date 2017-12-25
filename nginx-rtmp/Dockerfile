FROM centos
MAINTAINER centos-nginx-rtmp
ADD ./nginx /temp/nginx
ADD ./nginx-rtmp-module /temp/nginx-rtmp-module

RUN yum update -y
RUN yum install -y pcre-devel openssl-devel gcc make
WORKDIR /temp/nginx
RUN ./configure --prefix=/etc/nginx --sbin-path=/usr/sbin --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock --add-module=../nginx-rtmp-module --with-http_ssl_module
RUN make && make install

ADD nginx.conf /etc/nginx/nginx.conf

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80
EXPOSE 1935
