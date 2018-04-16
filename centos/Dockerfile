FROM centos:7
MAINTAINER Takamasa Kan
ARG username="kan"
ARG password="kankan"

# system update
RUN yum -y install git apt && yum -y update && yum clean all
RUN yum -y install wget epel-release
RUN wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum -y install http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

# kubernetesのインストール
#RUN yum -y install etcd kubernetes flannel
# phpインストール
RUN yum -y install --enablerepo=remi-php70 php
RUN yum -y install --enablerepo=remi-php70 php-devel php-pear
RUN yum -y install --enablerepo=remi-php70 php-mysqlnd php-mbstring
RUN yum -y install --enablerepo=remi-php70 php-fpm
RUN rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
RUN yum -y install nginx
RUN nginx
#RUN mkdir /home/$username
RUN useradd -s /bin/bash -d /home/$username $username && echo "$username:$password" | chpasswd
#RUN chown -R $username:$username /home/$username

# editor install
RUN yum install -y vim

# busybox用
# mysql用
RUN mkdir /var/lib/mysql
# PHP用
# RUN mkdir /usr/local/etc/php/
# ADD setting/php7/php.ini /usr/local/etc/php/
# RUN chmod 755 /usr/local/etc/php/php.ini
# web用
#RUN mkdir /var/www && mkdir /var/www/html
# nginx用
ADD setting/nginx/server.conf /etc/nginx/conf.d/
RUN chmod 755 /etc/nginx/conf.d/server.conf
RUN mv /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf_bk
CMD ["nginx", "-g", "daemon off;"]
RUN chmod 755 /var/log/nginx/

# port解放
EXPOSE 80