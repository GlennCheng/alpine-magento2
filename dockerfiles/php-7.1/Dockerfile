FROM alpine:3.6

RUN apk --update --no-cache add \
	shadow \
	curl \
	vim \
	git \
	tree \
	php7 \
	php7-bcmath \
	php7-cli \
	php7-ctype \
	php7-curl \
	php7-dom \
	php7-fpm \
	php7-gd \
	php7-iconv \
	php7-intl \
	php7-json \
	php7-mbstring \
	php7-mcrypt \
	php7-openssl \
	php7-pdo_mysql \
	php7-phar \
	php7-session \
	php7-simplexml \
	php7-soap \
	php7-tokenizer \
	php7-xml \
	php7-xmlwriter \
	php7-xsl \
	php7-zip \
	php7-zlib

RUN usermod -u 1000 nobody && \
	groupmod -g 1000 nobody

RUN curl --silent --show-error https://getcomposer.org/installer | php && \
	mv composer.phar /usr/bin/composer

COPY ./bin/startup.sh /usr/local/bin/startup.sh
COPY ./conf/php.ini /etc/php7/php.ini
COPY ./conf/www.conf /etc/php7/php-fpm.d/www.conf
COPY ./conf/aliases.sh /etc/profile.d/aliases.sh

EXPOSE 9000
WORKDIR /var/www/html
CMD [ "sh", "/usr/local/bin/startup.sh" ]
