# Dockerfile from tutorial http://docs.docker.io/en/latest/examples/nodejs_web_app/
#FROM    centos

#RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
#RUN     yum install -y npm curl vsftpd git

#ADD package.json /src/
#RUN npm config set strict-ssl false
#RUN cd /src; npm install
#ADD index.js /src/
#RUN mkdir /var/www/;

#RUN cd /var/www/; git clone https://github.com/WordPress/WordPress 
#RUN mv WordPress/* ./
#RUN rmdir WordPress/


#EXPOSE  8080
#CMD ["node", "/src/index.js"]


FROM ubuntu
MAINTAINER antoine.morbois@gmail.com

RUN echo "deb http://archive.ubuntu.com/ubuntu/ raring main universe" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y nano wget dialog net-tools
RUN apt-get install -y nginx git vsftpd curl npm

RUN rm -v /etc/nginx/nginx.conf
RUN cd /var/; git clone https://github.com/WordPress/WordPress 
RUN mv /var/WordPress/ /var/www/


ADD nginx.conf /etc/nginx/
#ADD upstream.conf /etc/nginx/

EXPOSE 80
CMD nginx -c /etc/nginx/nginx.conf
