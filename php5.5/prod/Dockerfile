FROM centos

MAINTAINER somni <sleepdragon@moofa.com>


RUN yum install -y gcc gcc-c++ pcre-devel zlib-devel libxml2-devel libcurl-devel libjpeg-devel libpng-devel  freetype-devel openssl-devel


RUN mkdir /install
RUN cd /install
RUN wget http://jaist.dl.sourceforge.net/project/mcrypt/Libmcrypt/2.5.8/libmcrypt-2.5.8.tar.gz
RUN tar zxvf libmcrypt-2.5.8.tar.gz
RUN cd libmcrypt-2.5.8
RUN ./configure
RUN make
RUN make install

RUN cd /install
RUN wget http://jp1.php.net/distributions/php-5.5.12.tar.bz2
RUN tar jxvf php-5.5.12.tar.bz2
RUN cd php-5.5.12
RUN ./configure --prefix=/usr/local/php --with-config-file-path=/etc/ --with-config-file-scan-dir=/etc/php.d --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-zlib --enable-mbstring --with-gd --with-jpeg-dir --with-png-dir --enable-gd-native-ttf --enable-fpm --with-curl --with-mcrypt --with-freetype-dir --enable-pcntl --with-openssl
RUN make 
RUN make install
RUN cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
RUN chmod +x /etc/init.d/php-fpm


# remove files
RUN rm -rf /install



CMD ["/etc/init.d/php-fpm", "start"]
