FROM ubuntu:16.04

MAINTAINER Chris Bogaards

RUN apt-get clean \
    && apt-get update \
    && apt-get install -y locales \
    && locale-gen en_US.UTF-8

ENV LANG='en_US.UTF-8' 
ENV LANGUAGE='en_US.UTF-8'
ENV LC_ALL='en_US.UTF-8'

RUN apt-get update \
    && apt-get install -y curl zip unzip git software-properties-common \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php7.0-fpm php7.0-cli php7.0-mcrypt php7.0-gd php7.0-mysql \
       php7.0-pgsql php7.0-imap php-memcached php7.0-mbstring php7.0-xml php7.0-curl \
       php7.0-intl php7.0-bcmath php7.0-soap php7.0-zip php7.0-redis \
       php7.0-xdebug \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && mkdir /run/php \
    && apt-get remove -y --purge software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ADD php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf
ADD www.conf /etc/php/7.0/fpm/pool.d/www.conf
ADD docker.ini /etc/php/7.0/fpm/conf.d/docker.ini

EXPOSE 9000

CMD ["php-fpm7.0"]