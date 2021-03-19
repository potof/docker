# CentOS 7.8
FROM centos:7
RUN yum update -y && yum clean all

# Install apache
RUN yum install -y httpd
RUN yum install -y php php-mbstring php-mysql php-gd php-mcrypt php-sqlsrv php-pear

# Install Smarty
RUN yum install -y wget
RUN cd /usr/local/lib && wget https://github.com/smarty-php/smarty/archive/v3.1.21.tar.gz && tar -zxvf v3.1.21.tar.gz

# Port
EXPOSE 80

# Httpd start
ENTRYPOINT ["/usr/sbin/httpd", "-DFOREGROUND"]
#RUN systemctl enable httpd
#CMD ["/sbin/init"]
