FROM debian:stretch
MAINTAINER libaishun libaishun007@gmail.com
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime
RUN apt-get update
RUN apt-get install -y php7.0 php7.0-mysql php7.0-mcrypt php7.0-gd php7.0-curl php7.0-common
RUN apt-get install -y mariadb-client
RUN apt-get install -y cron
RUN apt-get install -y ntpdate
RUN a2enmod rewrite
COPY apache2.conf /etc/apache2/
COPY 000-default.conf  /etc/apache2/sites-available/
#crontab
COPY ./cronfile /etc/crontab
RUN crontab /etc/crontab
#back up db
#COPY ./dbbk.sh /dbbk.sh
#RUN chmod +x /dbbk.sh
#checkapache shell
#COPY ./checkapache2.sh /checkapache2.sh
#RUN chmod +x /checkapache2.sh
#startup shell
COPY ./start.sh /start.sh
RUN chmod +x /start.sh
CMD ["bash","/start.sh"]
