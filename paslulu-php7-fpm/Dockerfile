FROM php:7.1.1-fpm
RUN apt-get update
RUN docker-php-ext-install mysqli
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
RUN apt-get install git -y
RUN git --version
RUN apt-get install -y build-essential libmemcached-dev
RUN git clone https://github.com/php-memcached-dev/php-memcached.git
RUN cd php-memcached \
	&& git checkout php7 \
	&& phpize \
	&& ./configure --disable-memcached-sasl \
	&& make \
	&& make install