FROM centos:7

#install base packages
RUN yum update -y \
    && yum install -y https://mirror.webtatic.com/yum/el7/webtatic-release.rpm \
    && yum install -y \
        php71w-cli \
        php71w-fpm \
        php71w-mcrypt \
        php71w-opcache \
        php71w-gd \
        php71w-json \
        php71w-mbstring \
        php71w-xml \
        php71w-process \
        php71w-pecl-memcached
    
#configure
COPY config/php/www.conf /etc/php-fpm.d/www.conf

#ElastiCache Memcached Cluster Client
COPY config/php/modules/memcached/memcached.so /opt/remi/php71/root/usr/lib64/php/modules/memcached.so
COPY config/php/modules/memcached/50-memcached.ini /etc/opt/remi/php71/php.d/50-memcached.ini

EXPOSE 9000

STOPSIGNAL SIGTERM

CMD ["php-fpm", "-F"]