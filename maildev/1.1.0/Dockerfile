FROM djfarrelly/maildev:1.1.0

WORKDIR /usr/src/app
ENV NODE_ENV production

RUN set -xe \
    && apk add --update-cache --no-cache --virtual .builddeps \
        make \
        g++ \
        python \
    && npm install node-gyp -g \
    && npm install iconv \
    && npm audit fix \
    && npm prune \
    && npm cache clean --force \
    && apk del --update-cache --no-cache --purge .builddeps \
    && rm -rf /tmp/*
