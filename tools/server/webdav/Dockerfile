FROM httpd:2.4

ENV DAVLOCK_DIR /usr/local/apache2/var/DavLock
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data

RUN mkdir -p $DAVLOCK_DIR \
    && chown -R $APACHE_RUN_USER:$APACHE_RUN_GROUP $DAVLOCK_DIR \
    && chmod 755 $DAVLOCK_DIR

RUN mkdir -p /usr/local/apache2/uploads \
    && chown www-data:www-data /usr/local/apache2/uploads \
    && chmod 755 /usr/local/apache2/uploads

CMD ["httpd-foreground"]