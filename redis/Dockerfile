FROM redis:latest

RUN echo ========REDIS_INSTALLING================================================
MAINTAINER Mahmoud Zalt <mahmoud@zalt.me>

#COPY redis.conf /usr/local/etc/redis/redis.conf

VOLUME /data

EXPOSE 6379

#CMD ["redis-server", "/usr/local/etc/redis/redis.conf"]
CMD ["redis-server"]
