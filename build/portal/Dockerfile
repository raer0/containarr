###
# This is a simple nginx reverse proxy running on alpine linux using supervisord for process management.
# It copies config files from config/nginx and config/supervisord to appropriate locations on the container.
###
FROM alpine:3.15
RUN apk --no-cache add \
    nginx \
    supervisor

# Make and change ownership
RUN mkdir -p /app
RUN chown -R nobody.nobody /app && \
    chown -R nobody.nobody /run && \
    chown -R nobody.nobody /var/lib/nginx && \
    chown -R nobody.nobody /var/log/nginx

# Copy config files for supervisor and nginx, then copy and chown html/app files
COPY config/supervisord/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY config/nginx/ /etc/nginx/
COPY --chown=nobody app /app

# Change user and default work dir
USER nobody
WORKDIR /app

# Expose the port nginx is reachable on
EXPOSE 80

# Start supervisor, which takes over and runs nginx.
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
