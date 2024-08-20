FROM nginx:latest

COPY main.c /
COPY nginx/nginx.conf /etc/nginx/nginx.conf

RUN apt-get update && apt-get install -y gcc libfcgi-dev && \
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    gcc -o mini_server main.c -lfcgi

#USER nginx

CMD /bin/sh -c "nginx -g 'daemon off;' & /mini_server"

HEALTHCHECK NONE