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

RUN yum install -y epel-release
RUN yum install -y ftp://ftp.pbone.net/mirror/archive.fedoraproject.org/epel/7.2019-05-29/x86_64/Packages/f/freetds-0.95.81-1.el7.x86_64.rpm
RUN yum install -y php-mssql.x86_64

# iconv
RUN yum install -y gcc
RUN yum install -y patch
RUN curl http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.13.tar.gz > /libiconv-1.13.tar.gz
RUN curl http://www2d.biglobe.ne.jp/~msyk/software/libiconv/libiconv-1.13-cp932.patch.gz > /libiconv-1.13-cp932.patch.gz

RUN gzip -dc /libiconv-1.13.tar.gz | tar xvf -
RUN cd /libiconv-1.13 && gzip -dc ../libiconv-1.13-cp932.patch.gz | patch -p1

RUN cd /libiconv-1.13 && ./configure
RUN cd /libiconv-1.13 && make && make check
RUN cd /libiconv-1.13 && make install

# Install Smarty
RUN yum install -y wget
RUN cd /usr/local/lib && wget https://github.com/smarty-php/smarty/archive/v3.1.21.tar.gz && tar -zxvf v3.1.21.tar.gz

# Port
EXPOSE 80

# Httpd start
ENTRYPOINT ["/usr/sbin/httpd", "-DFOREGROUND"]
#RUN systemctl enable httpd
#CMD ["/sbin/init"]
