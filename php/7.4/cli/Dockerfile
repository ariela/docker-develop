#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： bz2
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-bz2
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && apk add --update-cache --no-cache bzip2-dev && docker-php-ext-install bz2

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： calendar
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-calendar
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install calendar

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： exif
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-exif
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install exif

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： gettext
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-gettext
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && apk add --update-cache --no-cache gettext-dev && docker-php-ext-install gettext

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： opcache
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-opcache
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install opcache

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： pcntl
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-pcntl
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install pcntl

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： pdo_mysql
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-pdo_mysql
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install pdo_mysql

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： sockets
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-sockets
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && docker-php-ext-install sockets

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 拡張モジュールビルドステージ： apcu
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM php:7.4-cli-alpine AS build-apcu
RUN set -xe && apk add --update-cache --no-cache autoconf dpkg-dev dpkg file g++ gcc libc-dev make pkgconf re2c
RUN set -xe && yes '' | pecl install apcu && docker-php-ext-enable apcu

#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# 軽量化php-fpm環境
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM alpine:3.10

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# composer の su実行を明示的に許可
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
ENV COMPOSER_ALLOW_SUPERUSER 1

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# PHP拡張のパス・設定パスの定義（PHPバージョンによって異なる）
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
ARG PHP_EXTENSION_PATH="/usr/local/lib/php/extensions/no-debug-non-zts-20190902"
ARG PHP_CONFIG_PATH="/usr/local/etc/php/conf.d"

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# PHP動作環境をコピー
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
COPY --from=php:7.4-cli-alpine /usr/local/etc /usr/local/etc
COPY --from=php:7.4-cli-alpine /usr/local/bin /usr/local/bin
COPY --from=php:7.4-cli-alpine /usr/local/include/php /usr/local/include/php
COPY --from=php:7.4-cli-alpine /usr/local/lib/php /usr/local/lib/php
COPY --from=php:7.4-cli-alpine /usr/local/php /usr/local/php
COPY --from=composer /usr/bin/composer /usr/bin/composer

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# PHP環境ビルドステージからPHP動作環境をコピー
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# 拡張モジュールインストール： bz2
COPY --from=build-bz2 ${PHP_EXTENSION_PATH}/bz2.so ${PHP_EXTENSION_PATH}/bz2.so
COPY --from=build-bz2 ${PHP_CONFIG_PATH}/docker-php-ext-bz2.ini ${PHP_CONFIG_PATH}/docker-php-ext-bz2.ini

# 拡張モジュールインストール： calendar
COPY --from=build-calendar ${PHP_EXTENSION_PATH}/calendar.so ${PHP_EXTENSION_PATH}/calendar.so
COPY --from=build-calendar ${PHP_CONFIG_PATH}/docker-php-ext-calendar.ini ${PHP_CONFIG_PATH}/docker-php-ext-calendar.ini

# 拡張モジュールインストール： exif
COPY --from=build-exif ${PHP_EXTENSION_PATH}/exif.so ${PHP_EXTENSION_PATH}/exif.so
COPY --from=build-exif ${PHP_CONFIG_PATH}/docker-php-ext-exif.ini ${PHP_CONFIG_PATH}/docker-php-ext-exif.ini

# 拡張モジュールインストール： opcache
COPY --from=build-opcache ${PHP_EXTENSION_PATH}/opcache.so ${PHP_EXTENSION_PATH}/opcache.so
COPY --from=build-opcache ${PHP_CONFIG_PATH}/docker-php-ext-opcache.ini ${PHP_CONFIG_PATH}/docker-php-ext-opcache.ini

# 拡張モジュールインストール： pcntl
COPY --from=build-pcntl ${PHP_EXTENSION_PATH}/pcntl.so ${PHP_EXTENSION_PATH}/pcntl.so
COPY --from=build-pcntl ${PHP_CONFIG_PATH}/docker-php-ext-pcntl.ini ${PHP_CONFIG_PATH}/docker-php-ext-pcntl.ini

# 拡張モジュールインストール： pdo_mysql
COPY --from=build-pdo_mysql ${PHP_EXTENSION_PATH}/pdo_mysql.so ${PHP_EXTENSION_PATH}/pdo_mysql.so
COPY --from=build-pdo_mysql ${PHP_CONFIG_PATH}/docker-php-ext-pdo_mysql.ini ${PHP_CONFIG_PATH}/docker-php-ext-pdo_mysql.ini

# 拡張モジュールインストール： sockets
COPY --from=build-sockets ${PHP_EXTENSION_PATH}/sockets.so ${PHP_EXTENSION_PATH}/sockets.so
COPY --from=build-sockets ${PHP_CONFIG_PATH}/docker-php-ext-sockets.ini ${PHP_CONFIG_PATH}/docker-php-ext-sockets.ini

# 拡張モジュールインストール： apcu
COPY --from=build-apcu ${PHP_EXTENSION_PATH}/apcu.so ${PHP_EXTENSION_PATH}/apcu.so
COPY --from=build-apcu ${PHP_CONFIG_PATH}/docker-php-ext-apcu.ini ${PHP_CONFIG_PATH}/docker-php-ext-apcu.ini

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# 基本設定の実施
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
RUN set -eux \
    # ユーザ / グループの作成
    && addgroup -g 82 -S www-data \
    && adduser -u 82 -D -S -G www-data www-data \
    # タイムゾーン設定
    && apk add --update-cache --no-cache tzdata \
    && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && echo "Asia/Tokyo" > /etc/timezone \
    && apk del --no-network tzdata \
    # パッケージインストール
    && apk add --update-cache --no-cache \
        ca-certificates \
        openssl \
    # PHP依存パッケージインストール
    && DEPS=$(scanelf --needed --nobanner --format '%n#p' --recursive /usr/local | tr ',' '\n' | sort -u | awk 'system("[ -e /usr/local/lib/" $1 " ]") == 0 { next } { print "so:" $1 }') \
    && apk add --update-cache --no-cache $DEPS \
    # composerの設定
    && composer config -g repos.packagist composer https://packagist.jp \
    && composer global require hirak/prestissimo \
    && composer global clear-cache

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# 停止時のシグナルをSIGQUITとする
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
STOPSIGNAL SIGQUIT

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# TCP/9000 ポートを外部公開
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
EXPOSE 9000

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# PHPの実行
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
ENTRYPOINT ["docker-php-entrypoint"]
CMD ["php", "-a"]
