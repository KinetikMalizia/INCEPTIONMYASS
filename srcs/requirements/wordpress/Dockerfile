FROM debian:buster

RUN		apt update -y
RUN		apt upgrade -y
RUN		apt-get -y install wget

RUN	apt-get install -y php7.3\
						php-fpm\
						php-mysql\
						mariadb-client

RUN	wget https://fr.wordpress.org/wordpress-6.0-fr_FR.tar.gz -P /var/www
RUN	wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN	chmod +x wp-cli.phar && mv wp-cli.phar /usr/local/bin/wp

RUN cd /var/www && tar -xzf wordpress-6.0-fr_FR.tar.gz && rm wordpress-6.0-fr_FR.tar.gz

RUN		chown -R root:root /var/www/wordpress

RUN	mkdir /run/php

COPY ./tools/config.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/config.sh
ENTRYPOINT ["/usr/local/bin/config.sh"]

WORKDIR /var/www/html/

EXPOSE 9000

CMD ["/usr/sbin/php-fpm7.3", "-F"]