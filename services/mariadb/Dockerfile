FROM debian:wheezy
MAINTAINER Tsong khapa <ztd811@yahoo.com>
ENV MARIADB_DB NONE
ENV MARIADB_USER docker
RUN apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xcbcb082a1bb943db && echo 'deb http://ftp.osuosl.org/pub/mariadb/repo/5.5/debian wheezy main' > /etc/apt/sources.list.d/mariadb.lis
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -yq procps mariadb-server
RUN sed -i -e "s/^bind-address/#bind-address/" /etc/mysql/my.cnf && \
        sed -i -e "s/^datadir.*=.*/datadir = \/data/" /etc/mysql/my.cnf && \
        sed -i -e "s/^innodb_buffer_pool_size.*=.*/innodb_buffer_pool_size = 64M/" /etc/mysql/my.cnf
ADD config /config
ADD supervisord.conf /etc/supervisor/conf.d/mariadb.conf
EXPOSE 3306