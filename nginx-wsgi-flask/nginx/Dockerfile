FROM nginx:1.19.7-alpine
RUN apk add bash
COPY nginx.conf /etc/nginx/nginx.conf
COPY start.sh /app/start.sh
# This file exists in the nginx folder, so this will work here
COPY default.conf /tmp/default.conf
WORKDIR /app
RUN chown -R nginx:nginx /app && chmod -R 755 /app && \
    chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /var/log/nginx && \
    chmod -R 755 /var/log/nginx; \
    chown -R nginx:nginx /etc/nginx/conf.d
RUN touch /var/run/nginx.pid && chown -R nginx:nginx /var/run/nginx.pid
USER nginx
ENTRYPOINT ["/app/start.sh"]
