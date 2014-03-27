# Dockerfile from tutorial http://docs.docker.io/en/latest/examples/nodejs_web_app/
FROM    centos

RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
RUN     yum install -y npm curl vsftpd git

ADD package.json /src/
RUN npm config set strict-ssl false
RUN cd /src; npm install
ADD index.js /src/
RUN mkdir /var/www/;
RUN cd /var/www/; git clone https://github.com/WordPress/WordPress 


EXPOSE  8080
CMD ["node", "/src/index.js"]
