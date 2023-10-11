FROM httpd:alpine3.16

LABEL author="Wellington Ozorio"
LABEL version="1.0.0"

COPY ./public-html/ /usr/local/apache2/htdocs/
RUN chown 82:82 /usr/local/apache2/logs

EXPOSE 8080

# 82 is the standard uid/gid for "www-data" in Alpine
USER 82
