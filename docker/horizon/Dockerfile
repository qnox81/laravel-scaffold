FROM app:local

LABEL MANGOdev <team@mangodev.pl>

USER root

RUN apk add --update --no-cache wget curl supervisor \
  && rm -rf /tmp/* \
  && addgroup laravel docker

ADD ./docker/horizon/supervisord.conf /etc/supervisor/supervisord.conf

RUN chown laravel:laravel /var/log -R \
    && chmod g+rwx /var/log

WORKDIR /etc/supervisor/conf.d/

USER laravel

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisor/supervisord.conf"]
