FROM alpine:3.7

ADD https://repos.php.earth/alpine/phpearth.rsa.pub /etc/apk/keys/phpearth.rsa.pub
RUN apk update \
    && echo "https://repos.php.earth/alpine/v3.7" >> /etc/apk/repositories \
    && apk add --no-cache composer git openssh ca-certificates curl wget zlib-dev procps \
    php7.2              \
    php7.2-fpm          \
    php7.2-curl         \
    php7.2-zip          \
    php7.2-mbstring     \
    php7.2-pcntl        \
    php7.2-posix        \
    php7.2-iconv        \
    php7.2-pdo_mysql    \
    php7.2-tokenizer    \
    php7.2-mysqli       \
    php7.2-dom          \
    php7.2-redis        \
    php7.2-xml          \
    php7.2-simplexml    \
    php7.2-json         \
    php7.2-sodium       \
    php7.2-opcache      \
    php7.2-shmop        \
    php7.2-xmlwriter    \
    php7.2-common

RUN wget https://github.com/phpredis/phpredis/archive/4.0.2.tar.gz \
    && tar xfz 4.0.2.tar.gz \
    && rm -r 4.0.2.tar.gz \
    && ls \
    && mkdir -p /usr/src/php/ext/ \
    && mv ./phpredis-4.0.2 /usr/src/php/ext/redis && rm -Rf phpredis-4.0.2 \
    && update-ca-certificates \
    && echo 'memory_limit=1024M' > /etc/php/7.2/conf.d/memory_limit.ini \
    && echo '[global]' > /etc/php/7.2/php-fpm.d/zz-docker.conf \
    && echo 'daemonize = no' >> /etc/php/7.2/php-fpm.d/zz-docker.conf \
    && echo '[www]' >> /etc/php/7.2/php-fpm.d/zz-docker.conf \
    && echo 'listen=9000' >> /etc/php/7.2/php-fpm.d/zz-docker.conf \
    && composer global require hirak/prestissimo

RUN echo 'realpath_cache_size=2048M' > /etc/php/7.2/conf.d/pathcache.ini \
    && echo 'realpath_cache_ttl=7200' >> /etc/php/7.2/conf.d/pathcache.ini \
    && echo '[opcache]' > /etc/php/7.2/conf.d/opcache.ini \
    && echo 'opcache.memory_consumption = 512M' >> /etc/php/7.2/conf.d/opcache.ini \
    && echo 'opcache.max_accelerated_files = 1000000' >> /etc/php/7.2/conf.d/opcache.ini

ENV APPLICATION_ENV local

EXPOSE 9000

CMD ["php-fpm"]









