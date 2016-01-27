##### Step1:安装必要依赖库
sudo apt-get install autoconf automake libtool re2c flex make libxml2-dev libssl-dev libbz2-dev libcurl3-dev libdb5.1-dev libjpeg-dev libpng-dev libXpm-dev libfreetype6-dev libt1-dev libgmp3-dev libc-client-dev libldap2-dev libmcrypt-dev libmhash-dev freetds-dev libz-dev libmysqlclient15-dev ncurses-dev libpcre3-dev unixODBC-dev libsqlite-dev libaspell-dev libreadline6-dev librecode-dev libsnmp-dev libtidy-dev libxslt-dev libt1-dev openssl   libxml2 libxml2-dev libpspell-dev libicu-dev bison

##### Step2:从Git上面拉取PHP7
sduo git clone https://git.php.net/repository/php-src.git
cd php-src

##### Step3:编译安装PHP7
sudo ./configure --prefix=/usr/local/php7 \
 --with-curl \
 --with-freetype-dir \
 --with-gd \
 --with-gettext \
 --with-iconv-dir \
 --with-kerberos \
 --with-libdir=lib64 \
 --with-libxml-dir \
 --with-mysqli \
 --with-openssl \
 --with-pcre-regex \
 --with-pdo-mysql \
 --with-pdo-sqlite \
 --with-pear \
 --with-png-dir \
 --with-xmlrpc \
 --with-xsl \
 --with-zlib \
 --enable-fpm \
 --enable-bcmath \
 --enable-libxml \
 --enable-inline-optimization \
 --enable-gd-native-ttf \
 --enable-mbregex \
 --enable-mbstring \
 --enable-opcache \
 --enable-pcntl \
 --enable-shmop \
 --enable-soap \
 --enable-sockets \
 --enable-sysvsem \
 --enable-xml \
 --enable-zip
 
 sudo make && make install
