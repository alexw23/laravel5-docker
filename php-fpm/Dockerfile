FROM php:5.6-fpm

RUN apt-get update && apt-get install -y \
    freetds-dev \
    libicu-dev \
    libpq-dev \
    libmcrypt-dev \
 && rm -r /var/lib/apt/lists/* \
 && cp -s /usr/lib/x86_64-linux-gnu/libsybdb.so /usr/lib/ \
 && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
 && docker-php-ext-install \
    intl \
    mbstring \
    mcrypt \
    mssql \
    pcntl \
    pdo_dblib \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    zip \
    opcache \
 && cd /usr/src/php \
 && make clean

ADD laravel.ini /etc/php5/fpm/conf.d/
ADD laravel.ini /etc/php5/cli/conf.d/

ADD laravel.pool.conf /etc/php5/fpm/pool.d/

RUN usermod -u 1000 www-data

CMD ["php-fpm"]

EXPOSE 9000