#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： xdebug
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && yes '' | pecl install xdebug && docker-php-ext-enable xdebug
