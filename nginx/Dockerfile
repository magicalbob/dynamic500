FROM almalinux

MAINTAINER Ian Ellis

ENV container docker
RUN yum -y update                                                                                                \
 && yum -y install systemd                                                                                       \
 && cd /lib/systemd/system/sysinit.target.wants/                                                                 \
 && for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done                                    \
 && rm -f /lib/systemd/system/multi-user.target.wants/*                                                          \
 && rm -f /etc/systemd/system/*.wants/*                                                                          \
 && rm -f /lib/systemd/system/local-fs.target.wants/*                                                            \
 && rm -f /lib/systemd/system/sockets.target.wants/*udev*                                                        \
 && rm -f /lib/systemd/system/sockets.target.wants/*initctl*                                                     \
 && rm -f /lib/systemd/system/basic.target.wants/*                                                               \
 && rm -f /lib/systemd/system/anaconda.target.wants/*                                                            \
 && yum clean all                                                                                                \
 && yum install -y epel-release                                                                                  \
 && yum install -y nginx \
 && systemctl enable nginx

VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
