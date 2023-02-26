FROM nginx:1.23-alpine as scratch

ARG APP_ENV
ENV APP_ENV=${APP_ENV}

# nginx
COPY .docker/nginx/nginx.conf /etc/nginx/nginx.conf
COPY .docker/nginx/default.conf /etc/nginx/conf.d/default.conf

# ENTRYPOINT ["dumb-init", "--rewrite", "15:3"]
CMD ["nginx", "-g", "daemon off;"]

WORKDIR /var/www/html

# DEV env (local)
FROM scratch as dev

# PROD env (kubernetes)
FROM scratch as prod