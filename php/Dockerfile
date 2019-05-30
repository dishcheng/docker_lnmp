FROM php:7.1-fpm 
MAINTAINER caicheng

ENV TZ=Asia/Shanghai

COPY sources.list /etc/apt/sources.list

RUN apt-get update && apt-get install -y libmcrypt-dev wget unzip python cron supervisor --no-install-recommends \
    # 安装php7.2（包括） - 7.4（包括）需要使用以下方式安装mcrypt,ps:不要在docker-php-ext-install 中安装mcrypt
    #&& pecl install mcrypt-1.0.2 \
    #&& docker-php-ext-enable mcrypt \
    # 如果安装php7.2以下安装mcrypt，在docker-php-ext-install中添加mcrypt即可
    && docker-php-ext-install mcrypt pdo_mysql bcmath mysqli json \
    && wget https://dl.laravel-china.org/composer.phar -O /usr/local/bin/composer \
    && chmod a+x /usr/local/bin/composer \
    && echo "清理" \
    && apt-get purge -y --auto-remove