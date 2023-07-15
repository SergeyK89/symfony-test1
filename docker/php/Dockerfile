FROM php:7.4-fpm

WORKDIR /app

RUN apt-get update && apt-get install -y zlib1g-dev g++ git zip libicu-dev libpq-dev libzip-dev

RUN docker-php-ext-install intl opcache pdo pdo_mysql

RUN pecl install apcu xdebug

RUN docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

RUN curl -sL https://getcomposer.org/installer | php -- --install-dir /usr/bin --filename composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

CMD ["php-fpm"]