#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
# xdebug込みphp環境
#===+====1====+====2====+====3====+====4====+====5====+====6====+====7====+====8====+====9====+====0
FROM arielase/develop:php-7.4-cli

#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
# PHP拡張のパス・設定パスの定義（PHPバージョンによって異なる）
#---+----1----+----2----+----3----+----4----+----5----+----6----+----7----+----8----+----9----+----0
ARG PHP_EXTENSION_PATH="/usr/local/lib/php/extensions/no-debug-non-zts-20190902"
ARG PHP_CONFIG_PATH="/usr/local/etc/php/conf.d"

# 拡張モジュールインストール： xdebug
COPY --from=arielase/develop:php-7.4-xdebug ${PHP_EXTENSION_PATH}/xdebug.so ${PHP_EXTENSION_PATH}/xdebug.so
COPY --from=arielase/develop:php-7.4-xdebug ${PHP_CONFIG_PATH}/docker-php-ext-xdebug.ini ${PHP_CONFIG_PATH}/docker-php-ext-xdebug.ini

# xdebugの有効化設定
COPY xdebug.ini ${PHP_CONFIG_PATH}/xdebug.ini
