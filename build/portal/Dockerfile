# ###
# # This is a simple nginx reverse proxy running on alpine linux using supervisord for process management.
# # It copies config files from config/nginx and config/supervisord to appropriate locations on the container.
# ###

###
# Bootstrap a self-signed TLS cert...
###
FROM alpine:3.15 as bobthebuilder
RUN apk add --no-cache openssl
RUN openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365 -nodes -subj "/C=US/ST=Oregon/L=Portland/O=rayr/OU=containarr/CN=*.containarr.lan"
RUN mkdir /var/ssl; mv /key.pem /var/ssl/key.pem; mv /cert.pem /var/ssl/cert.pem
COPY config/dhparam.pem /var/ssl/dhparam.pem
RUN chmod -R 750 /var/ssl/




###
#   Multi-stage build because why not?
###
FROM alpine:3.15
RUN apk --no-cache add nginx supervisor
RUN rm -rf /etc/nginx/http.d /etc/nginx/modules



# Copy config files and SSL
COPY --from=bobthebuilder /var/ssl /var/ssl
COPY config/supervisord/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY config/nginx /etc/nginx



# Make and change ownership
RUN mkdir /app && \
    chown -R nobody.nobody /app /run /var/lib/nginx /var/log/nginx /var/ssl


# Change user and default work dir, copy over app
USER nobody
COPY --chown=nobody app /app
WORKDIR /app


# Expose the port nginx is reachable on
EXPOSE 80
EXPOSE 443

# Start supervisor, which takes over and runs nginx.
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
