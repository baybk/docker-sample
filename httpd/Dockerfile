FROM httpd


WORKDIR /home/sites/

# install PHP and its extension
RUN apt-get update
RUN apt-get install -y sudo
RUN sudo apt-get install -y php
RUN sudo apt install -y openssl php-common php-curl php-json php-mbstring php-mysql php-xml php-zip
RUN sudo apt install -y php7.3-common php7.3-bcmath openssl php7.3-json php7.3-mbstring

# install php composer
RUN sudo apt-get install -y curl
RUN sudo apt-get install -y software-properties-common
RUN sudo curl -s https://getcomposer.org/installer | php
RUN sudo mv composer.phar /usr/local/bin/composer
RUN sudo apt-get install -y php7.3-gd

# intall node and npm for front-end
RUN curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN sudo apt-get install -y nodejs

# RUN sudo apt install -y npm
# RUN cd sites/mevent-web
# RUN sudo npm install --save-dev  --unsafe-perm=true node-sass --allow-root
# RUN sudo npm watch_prod   --unsafe-perm=true --allow-root