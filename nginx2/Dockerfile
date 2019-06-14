FROM local:nginx

MAINTAINER Ian Ellis

COPY conf.d/nginx2.conf /etc/nginx/conf.d/nginx2.conf
COPY html/index.html /usr/share/nginx/html/index.html

RUN chown -R nginx:nginx /etc/nginx \
 && chown -R nginx:nginx /usr/share/nginx/html

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
