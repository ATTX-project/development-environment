FROM nginx:alpine

EXPOSE 5039

COPY nginx.conf /etc/nginx/nginx.conf
ADD pypi /var/www/pivy/pypi
ADD index.html /var/www

ENTRYPOINT ["nginx"]
