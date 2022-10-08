FROM webdevops/php:8.1

# Packages
RUN apt-get update && apt-get install --no-install-recommends -y \
    libevent-dev \
    libssl-dev
    
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get update && apt-get install -y nodejs

WORKDIR /usr/src/php/ext

RUN wget http://pecl.php.net/get/event-3.0.8.tgz
RUN tar -zxvf event-3.0.8.tgz
RUN mv event-3.0.8 /usr/src/php/ext/event

RUN docker-php-ext-install event
RUN rm -rf /usr/local/etc/php/conf.d/docker-php-ext-event.ini
RUN docker-php-ext-enable --ini-name zz-event.ini event

WORKDIR /app
