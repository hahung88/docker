FROM centos:6.8
MAINTAINER nguyentoanit
#Update repository
RUN yum update --exclude=centos-release -y
RUN yum install -y http://rpms.famillecollet.com/enterprise/remi-release-6.rpm https://download.postgresql.org/pub/repos/yum/10/redhat/rhel-6-x86_64/pgdg-centos10-10-2.noarch.rpm epel-release crontabs yum-utils httpd git

#Install PHP repository
RUN yum-config-manager --enable remi,remi-php56

#Install neccessary packages
RUN yum install -y php php-common php-pgsql php-pdo php-mbstring php-xml postgresql10-server postgresql10

#Set service to start on server boot
RUN chkconfig postgresql10 on
RUN chkconfig httpd on

COPY scripts/start_service.sh /usr/local/bin/start_service.sh
ENTRYPOINT sh /usr/local/bin/start_service.sh;/bin/bash