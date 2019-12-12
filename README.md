# docker-develop

個人で使用する為の開発用Dockerコンテナイメージ。

https://hub.docker.com/r/arielase/develop

## 一覧
| イメージ名 | 備考 |
|----------|-----|
| arielase/develop:nginx-1.17           | nginx 1.17 |
| arielase/develop:php-7.4-cli          | CLI版 PHP7.4 |
| arielase/develop:php-7.4-cli-dev      | CLI版 PHP7.4 (xdebug込み) |
| arielase/develop:php-7.4-fpm          | FPM版 PHP7.4 |
| arielase/develop:php-7.4-fpm-dev      | FPM版 PHP7.4 (xdebug込み) |
| arielase/develop:php-7.4-xdebug       | PHP7.4用 xdebugモジュール |
| arielase/develop:php-7.4-inspection   | PHP7.4 検査用 |
| arielase/develop:maildev-1.1.0        | SMTPテスト用 |

## xdebugモジュール
モジュールビルドのみ実行しているイメージとなる。
導入は実行用イメージの `Dockerfile` にコピーする

```
FROM arielase/develop:php-7.4-fpm

ARG PHP_EXTENSION_PATH="/usr/local/lib/php/extensions/no-debug-non-zts-20190902"
ARG PHP_CONFIG_PATH="/usr/local/etc/php/conf.d"

COPY --from=arielase/develop:php-7.4-xdebug ${PHP_EXTENSION_PATH}/xdebug.so ${PHP_EXTENSION_PATH}/xdebug.so
COPY --from=arielase/develop:php-7.4-xdebug ${PHP_CONFIG_PATH}/docker-php-ext-xdebug.ini ${PHP_CONFIG_PATH}/docker-php-ext-xdebug.ini
```
