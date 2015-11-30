FROM nginx:1.9.7

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf
COPY default.conf /etc/nginx/conf.d/