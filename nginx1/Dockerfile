FROM local:nginx

MAINTAINER Ian Ellis

COPY conf.d/nginx1.conf /etc/nginx/conf.d/nginx1.conf

RUN chown -R nginx:nginx /etc/nginx

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
