FROM alpine:3.15

RUN apk --no-cache add \
    nginx \
    supervisor


COPY config/supervisord/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
# Configure nginx
COPY config/nginx/ /etc/nginx/


RUN mkdir -p /var/www/html

RUN chown -R nobody.nobody /var/www/html && \
  chown -R nobody.nobody /run && \
  chown -R nobody.nobody /var/lib/nginx && \
  chown -R nobody.nobody /var/log/nginx


USER nobody

# Add application
WORKDIR /var/www/html
COPY --chown=nobody html /var/www/html/

# Expose the port nginx is reachable on
EXPOSE 80

# Let supervisord start nginx & php-fpm
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
