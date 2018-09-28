
FROM webgarden/rabbit-php:7.1


# -----------------------------------------------
# Commons
# -----------------------------------------------

RUN set -e && apt-get update

RUN apt-get install --no-install-recommends -y mysql-client

RUN rm -rf /var/lib/apt/lists/*
