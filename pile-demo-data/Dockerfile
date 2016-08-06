FROM tutum/apache-php

# Install mysql-client
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        mysql-client \
        unzip \
    && rm -rf /var/lib/apt/lists/*

# Install wp-cli, configure Apache, & add scripts
COPY run.sh /run.sh
WORKDIR /app
RUN curl \
        -o /usr/local/bin/wp https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x /usr/local/bin/wp /run.sh \
    && sed -i "s/AllowOverride None/AllowOverride All/g" /etc/apache2/apache2.conf \
    && a2enmod rewrite \
    && service apache2 restart

# Run the server
EXPOSE 80 443
CMD ["/run.sh"]
