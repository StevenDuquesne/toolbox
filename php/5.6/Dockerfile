FROM php:5.6-cli

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libicu-dev \
        apt-transport-https \
        zlib1g-dev libicu-dev g++ \
    && docker-php-ext-install iconv mcrypt bcmath \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd mysqli pdo pdo_mysql exif mbstring opcache \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN curl -sL https://deb.nodesource.com/setup_6.x | apt-get install -y nodejs
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update && apt-get install -y zlib1g-dev libicu-dev g++ jpegoptim optipng curl git mysql-client vim zip unzip ruby ruby-dev nodejs npm
RUN npm install -g n && n stable && apt-get install -y yarn

RUN npm install -g less
RUN npm install -g bower
RUN npm install -g gulp
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN gem install --no-rdoc --no-ri sass -v 3.4.22
RUN gem install --no-rdoc --no-ri compass

WORKDIR /var/www/html

COPY php.ini /usr/local/etc/php/php.ini

RUN ln -s /usr/bin/nodejs /usr/bin/node