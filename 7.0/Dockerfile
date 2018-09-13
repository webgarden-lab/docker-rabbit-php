FROM rabbitmq:3.7

# -----------------------------------------------
# Commons 
# -----------------------------------------------

RUN set -e && \
	apt-get update && apt-get install --no-install-recommends -y \
		wget \
		rsyslog \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        ssh \
        git \
        telnet \
        unzip \
        openssl \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        g++ \
        ssh

# -----------------------------------------------
# PHP 7.0
# -----------------------------------------------


RUN set -e && \
	apt-get update \
	&& apt-get install --no-install-recommends -y \
		php7.0-cli \
	&& rm -rf /var/lib/apt/lists/*


# -----------------------------------------------
# Composer
# -----------------------------------------------

RUN EXPECTED_SIGNATURE=$(wget -q -O - https://composer.github.io/installer.sig) \
    ; php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    ; ACTUAL_SIGNATURE=$(php -r "echo hash_file('SHA384', 'composer-setup.php');") \
    ; [ "$EXPECTED_SIGNATURE" != "$ACTUAL_SIGNATURE" ] && echo 'ERROR: Invalid installer signature' && exit 1 \
	; php composer-setup.php --quiet \
	; mv composer.phar /usr/local/bin/composer \
	; chmod +x /usr/local/bin/composer \
	; RESULT=$? \
	; rm composer-setup.php \
	; exit $RESULT



