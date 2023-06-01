FROM debian:buster

#update apt-get to have latest verions
RUN		apt-get update
#download nginx and openssl
RUN		apt-get install -y nginx openssl

#create a directory to store the ssl keys
RUN mkdir /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -out /etc/nginx/ssl/fmalizia.crt -keyout /etc/nginx/ssl/fmalizia.key -subj "/C=CH/ST=Lausanne/L=Lausanne/O=42 School/OU=fmalizia/CN=fmalizia/"

#get the nginx conf into the conatiner
COPY conf/nginx.conf /etc/nginx/nginx.conf

#open the port 443 so user can connect
EXPOSE	443

#make sure nginx can access the html files
RUN chmod 755 /var/www/html
#make sure the root user can access the html files
RUN chown -R www-data:www-data /var/www/html

#launch the nginx container
CMD ["nginx", "-g", "daemon off;"]