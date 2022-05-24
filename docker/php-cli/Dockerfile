FROM php:8.0-cli

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libzip-dev \
        libxml2-dev \
        # libpng12-dev \
        mc \
        wget \
        zip \
        unzip \
        ssh \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd \
    #--with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install -j$(nproc) pdo pdo_mysql zip simplexml

RUN apt-get update && apt-get install -y \
    libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
	&& docker-php-ext-enable imagick

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /usr/share/nginx/html

CMD ["php-cli"]

