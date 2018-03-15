#FROM php:7.1-fpm
FROM laradock/php-fpm:2.0-71
#FROM php:7.1-alpine
RUN echo ========PLAYSTER_INTERFACE_INSTALLING================================================
USER root
ARG PHP_UPSTREAM=php-fpm
# Create app directory
RUN mkdir -p /app/

RUN apt-get update && apt-get install -y apt-utils
RUN apt-get install -y \
    vim \
    nano \
    nginx \
    supervisor \
    libmcrypt-dev \
    mysql-client \
    librabbitmq-dev \
    libxslt1-dev \
    libpq-dev \
    zlib1g-dev \
    bash \
&& docker-php-ext-install mcrypt mysqli xsl pdo pdo_mysql pdo_pgsql bcmath \
&& pecl install -o -f redis \
&& docker-php-ext-enable redis \
&& pecl install amqp \
&& docker-php-ext-enable amqp \
&& mkdir /conf \
&& mkdir /logs \
&& mkdir /shared \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer

COPY nginx.conf /etc/nginx/nginx.conf
COPY nginx-app.conf /etc/nginx/conf.d/nginx-app.conf
COPY supervisor.conf /etc/supervisor/conf.d/app.conf
#COPY . /app


ADD ./laravel.ini /usr/local/etc/php/conf.d
ADD ./laravel.pool.conf /usr/local/etc/php-fpm.d/

RUN usermod -u 1000 www-data

#RUN adduser -D -H -u 1000 -s /bin/bash www-data \
#    && rm /etc/nginx/conf.d/default.conf \
#RUN echo "upstream php-upstream { server ${PHP_UPSTREAM}:9000; }" >> /etc/nginx/nginx.conf

RUN chown www-data.www-data -R /app


WORKDIR /app/

EXPOSE 9999 80 443 8811

CMD ["supervisord", "--nodaemon", "-c", "/etc/supervisor/supervisord.conf"]

