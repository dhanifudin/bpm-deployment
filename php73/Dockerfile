FROM php:7.3-fpm-alpine

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
		--with-freetype-dir=/usr \
		--with-jpeg-dir=/usr \
		--with-png-dir=/usr \
		--with-webp-dir=/usr \
	; \
  docker-php-ext-install \
    gd \
    intl \
    ldap \
    pdo \
    pgsql \
    pdo_pgsql \
    zip

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer
