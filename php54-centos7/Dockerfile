# CentOS 7.8
FROM centos:7
RUN yum update -y && yum clean all

# Install apache
RUN yum install -y httpd
RUN yum install -y php php-mbstring php-mysql php-gd php-mcrypt php-sqlsrv php-pear


RUN curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
RUN ACCEPT_EULA=Y yum install -y msodbcsql
RUN ACCEPT_EULA=Y yum install -y mssql-tools
RUN yum install -y unixODBC-devel
RUN ln -sfn /opt/mssql-tools/bin/sqlcmd /usr/bin/sqlcmd
RUN ln -sfn /opt/mssql-tools/bin/bcp /usr/bin/bcp

# Install Smarty
RUN yum install -y wget
RUN cd /usr/local/lib && wget https://github.com/smarty-php/smarty/archive/v3.1.21.tar.gz && tar -zxvf v3.1.21.tar.gz

# Port
EXPOSE 80

# Httpd start
ENTRYPOINT ["/usr/sbin/httpd", "-DFOREGROUND"]
#RUN systemctl enable httpd
#CMD ["/sbin/init"]
