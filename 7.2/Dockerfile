
FROM rabbitmq:3.7


# -----------------------------------------------
# Commons
# -----------------------------------------------

RUN set -e && apt-get update

RUN apt-get install --no-install-recommends -y curl ca-certificates
RUN apt-get install --no-install-recommends -y unzip
RUN apt-get install --no-install-recommends -y openssl
RUN apt-get install --no-install-recommends -y g++
RUN apt-get install --no-install-recommends -y ssh
RUN apt-get install --no-install-recommends -y wget
RUN apt-get install --no-install-recommends -y git


# -----------------------------------------------
# PHP 7.2
# -----------------------------------------------
RUN apt update
RUN apt install apt-transport-https lsb-release ca-certificates -y

RUN wget -O /etc/apt/trusted.gpg.d/php.gpg \
	https://packages.sury.org/php/apt.gpg

RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list

RUN apt update
RUN apt install php7.2 -y


# -----------------------------------------------
# Composer
# -----------------------------------------------
RUN EXPECTED_SIGNATURE=$(wget -q -O - https://composer.github.io/installer.sig) \
    ; curl -sS https://getcomposer.org/installer -o 'composer-setup.php' \
    ; ACTUAL_SIGNATURE=$(php -r "echo hash_file('SHA384', 'composer-setup.php');") \
    ; [ "$EXPECTED_SIGNATURE" != "$ACTUAL_SIGNATURE" ] && echo 'ERROR: Invalid installer signature' && exit 1 \
	; php composer-setup.php --quiet \
	; mv composer.phar /usr/local/bin/composer \
	; chmod +x /usr/local/bin/composer \
	; RESULT=$? \
	; rm composer-setup.php \
	; exit $RESULT


# -----------------------------------------------
# Clear
# -----------------------------------------------
RUN rm -rf /var/lib/apt/lists/*


RUN php -v
