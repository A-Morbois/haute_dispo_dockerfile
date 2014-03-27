# Dockerfile from tutorial http://docs.docker.io/en/latest/examples/nodejs_web_app/
FROM    centos

RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
RUN     yum install -y npm curl vsftpd git

ADD package.json /src/
RUN npm config set strict-ssl false
RUN cd /src; npm install
ADD index.js /src/
RUN mkdir /var/www/;

# RUN cd /var/www/; git clone https://github.com/WordPress/WordPress 

ADD http://wordpress.org/latest.tar.gz /usr/share/nginx/latest.tar.gz
RUN cd /usr/share/nginx/ && tar xvf latest.tar.gz && rm latest.tar.gz
RUN mv /usr/share/nginx/www/5* /usr/share/nginx/wordpress
RUN rm -rf /usr/share/nginx/www
RUN mv /usr/share/nginx/wordpress /usr/share/nginx/www
RUN chown -R www-data:www-data /usr/share/nginx/www


EXPOSE  8080
CMD ["node", "/src/index.js"]
