FROM local:nginx

MAINTAINER Ian Ellis

COPY conf.d/nginx3.conf /etc/nginx/conf.d/nginx3.conf
COPY html/index.html /usr/share/nginx/html/index.html

RUN chown -R nginx:nginx /etc/nginx \
 && chown -R nginx:nginx /usr/share/nginx/html

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
