FROM webdevops/apache:ubuntu-16.04
RUN echo ========APACHE_INSTALLING================================================
MAINTAINER Eric Pfeiffer <computerfr33k@users.noreply.github.com>

ARG PHP_SOCKET=php-fpm:9000

ENV WEB_PHP_SOCKET=$PHP_SOCKET

ENV WEB_DOCUMENT_ROOT=/var/www/

EXPOSE 80 443

WORKDIR /var/www/

COPY vhost.conf /etc/apache2/sites-enabled/vhost.conf

ENTRYPOINT ["/opt/docker/bin/entrypoint.sh"]

#CMD ["supervisord"]
CMD ["supervisord", "--nodaemon", "-c", "/etc/supervisor/supervisord.conf"]
