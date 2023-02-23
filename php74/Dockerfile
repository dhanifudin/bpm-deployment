FROM php:7.4-fpm-alpine

RUN set -ex; \
  apk add --no-cache --virtual .build-deps \
		$PHPIZE_DEPS \
		freetype-dev \
		icu-dev \
		imagemagick-dev \
		libjpeg-turbo-dev \
		libpng-dev \
    libldap \
    openldap-dev \
		libwebp-dev \
		libzip-dev \
    postgresql-dev \
  ; \
  docker-php-ext-configure gd \
		--with-freetype \
		--with-jpeg \
		--with-webp \
  ; \
  docker-php-ext-install \
    gd \
    intl \
    ldap \
    pdo \
    pgsql \
    pdo_pgsql \
    zip

# RUN apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/3.13/community/ \
#       php7-opcache php7-pgsql php7-pdo_pgsql php7-pdo_mysql php7-json php7-openssl php7-curl \
#       php7-zlib php7-xml php7-phar php7-intl php7-dom php7-xmlreader php7-ctype php7-session \
#       php7-tokenizer php7-xmlwriter php7-pdo php7-fileinfo php7-simplexml php7-zip php7-iconv php7-ldap \
#       php7-mbstring php7-gd

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer
