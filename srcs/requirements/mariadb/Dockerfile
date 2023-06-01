FROM debian:buster

RUN		apt update -y
RUN		apt upgrade -y

RUN		apt-get install mariadb-server -y

COPY conf/mariadb.conf	/etc/mysql/mariadb.conf.d/50-server.cnf
COPY ./tools/start.sh /usr/local/bin/

RUN chmod 755 /etc/mysql/mariadb.conf.d/50-server.cnf
RUN chmod +x /usr/local/bin/start.sh

EXPOSE 3306

ENTRYPOINT [ "/usr/local/bin/start.sh" ]