FROM mariadb:latest
RUN echo ========MARIA_DB_INSTALLING================================================
MAINTAINER Mahmoud Zalt <mahmoud@zalt.me>

ADD my.cnf /etc/mysql/conf.d/my.cnf

CMD ["mysqld"]

EXPOSE 3306
