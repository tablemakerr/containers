FROM centos:7

RUN yum clean all                     \
 && yum update -y                     \
 && yum install -y httpd mod_ssl

EXPOSE 80/tcp
CMD /usr/sbin/httpd -DFOREGROUND