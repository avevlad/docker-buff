FROM php:5.6-fpm

ARG SSH_PRIVATE_KEY
ARG TIMEZONE

RUN  apt-get -yq update && \
     apt-get -yqq install ssh git

RUN mkdir /root/.ssh/ && \
    echo "${SSH_PRIVATE_KEY}" > /root/.ssh/docker_deploy_key && \
    echo 'eval $(ssh-agent)' >> /root/.bashrc && \
    echo 'ssh-add /root/.ssh/docker_deploy_key' >> /root/.bashrc && \
    chmod 600 /root/.ssh/docker_deploy_key && \
    eval $(ssh-agent) && \
    ssh-add /root/.ssh/docker_deploy_key && \
    ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

RUN echo ${TIMEZONE}
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone
RUN printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini
RUN "date"

RUN apt-get install -y --no-install-recommends \
        libmemcached-dev \
        zlib1g-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libssl-dev \
        libicu-dev \
        libzip-dev \
        unzip \
        zip \
        libbz2-dev \
        libssh2-1-dev \
        libgmp-dev \
        libpq-dev \
    && docker-php-ext-configure zip --with-libzip \
    && docker-php-ext-install zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && pecl install memcached-2.2.0 \
    && docker-php-ext-enable memcached \
    && pecl install mongo-1.6.16 \
    && docker-php-ext-enable mongo

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

#COPY docker-entrypoint.sh /
#RUN chmod +x /docker-entrypoint.sh
#ENTRYPOINT ["/docker-entrypoint.sh"]

#WORKDIR /srv/www/service-contest
#RUN ls -la
