FROM php:7.0-alpine

MAINTAINER Len Lorijn <lenlorijn@gmail.com>

COPY ./mediact-standard /mediact-standard

ENV PHPCSPATH = /mediact-standard/vendor/squizlabs/php_codesniffer
ENV PATH $PHPCSPATH/scripts:$PATH

RUN /mediact-standard/vendor/squizlabs/php_codesniffer/scripts/phpcs --config-set installed_paths /mediact-standard/vendor/mediact/coding-standard/src \ 
   && /mediact-standard/vendor/squizlabs/php_codesniffer/scripts/phpcs \
     --config-set severity 1 \
   && /mediact-standard/vendor/squizlabs/php_codesniffer/scripts/phpcs --config-set default_standard MediaCT \
   && /mediact-standard/vendor/squizlabs/php_codesniffer/scripts/phpcs --config-set show_progress 1 \

WORKDIR /app

ENTRYPOINT ["/mediact-standard/vendor/squizlabs/php_codesniffer/scripts/phpcs"]

CMD ["--version"]
