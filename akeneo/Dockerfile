FROM ubuntu:14.04
MAINTAINER François-Marie de Jouvencel <fm.de.jouvencel@gmail.com>
LABEL Description="Latest version of akeneo pim with demo data."

RUN apt-get update && apt-get install -y apache2 libapache2-mod-php5 curl php5-intl php-apc php5-mysql mysql-client php5-gd php5-mcrypt php5-curl
RUN php5enmod mcrypt
RUN a2enmod rewrite
RUN curl -s http://download.akeneo.com/pim-community-standard-v1.5-latest-icecat.tar.gz | tar xzvf -
RUN mv pim-community-standard /var/www/akeneo
RUN mv composer.phar /var/www/akeneo
COPY sites-enabled /etc/apache2/sites-enabled/
COPY php.ini /etc/php5/apache2/php.ini
COPY php.ini /etc/php5/cli/php.ini
COPY parameters.yml /var/www/akeneo/app/config/parameters.yml
RUN rm /etc/apache2/sites-enabled/000-default.conf
RUN chmod g+rwxs -R /var/www/akeneo
RUN chgrp www-data -R /var/www/akeneo
VOLUME /var/log
WORKDIR /var/www/akeneo
#RUN php app/console pim:install

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
