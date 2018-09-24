
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
# PHP 7.1
# -----------------------------------------------
# RUN apt-get install --no-install-recommends -y software-properties-common
# RUN add-apt-repository ppa:ondrej/php
# RUN apt-get update
# RUN apt-get install  --no-install-recommends -y php7.1 \
#     libapache2-mod-php7.1  \
#     php7.1-common  \
#     php7.1-mbstring  \
#     php7.1-xmlrpc \
#     php7.1-soap  \
#     php7.1-gd \
#     php7.1-xml  \
#     php7.1-intl \
#     php7.1-mysql \
#     php7.1-cli  \
#     php7.1-mcrypt  \
#     php7.1-zip  \
#     php7.1-curl 


RUN install ca-certificates apt-transport-https \
	; wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add - \
	; echo "deb https://packages.sury.org/php/ stretch main" | sudo tee /etc/apt/sources.list.d/php.list

RUN apt-get update
RUN apt install php7.1
RUN apt install php7.1-cli php7.1-common php7.1-curlphp7.1-mbstring php7.1-mysql php7.1-xml


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
