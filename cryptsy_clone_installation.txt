sudo apt-get update
sudo apt-get install -y build-essential
sudo apt-get install -y python-software-properties


sudo add-apt-repository ppa:ondrej/php5
sudo apt-get update
sudo apt-get upgrade
apt-get install apache2

sudo apt-get install php5
sudo apt-get install mysql-server libapache2-mod-php5 php5-mysql
sudo apt-get install libboost-all-dev
sudo apt-get install libdb++-dev
sudo apt-get install libminiupnpc-dev

-------------
//choisir sa version de libboost 
apt-cache show libboost-dev


//create a vhost
/etc/apache2/sites-available/crypto-maniac.com
mkdir -p /var/www/crypto-maniac.com/public_html
mkdir /var/www/crypto-maniac.com/logs

service apache2 restart

o7Ym7[]v5n
--------------------
<VirtualHost *:80>
     ServerAdmin webmaster@example.net
     ServerName www.crypto-maniac.com
     ServerAlias www.crypto-maniac.com
     DocumentRoot /var/www/crypto-maniac.com/public_html/
     ErrorLog /var/www/crypto-maniac.com/logs/error.log
     CustomLog /var/www/crypto-maniac.com/logs/access.log combined

</VirtualHost>
-------------------------
//enable site
a2ensite crypto-maniac.com.conf
sudo service apache2 reload
//check what module for apache is available to install
apt-cache search libapache2*


a2enmod rewrite
service apache2 restart

a2enmod headers
//add to vhost
Header always append X-Frame-Options SAMEORIGIN

-------------------------------------
https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04
sudo add-apt-repository ppa:tuxpoldo/phpmyadmin
//install phpmyadmin
sudo apt-get install phpmyadmin  (Anthemis2014OPassword)
sudo nano /etc/apache2/apache2.conf
//add this line
Include /etc/phpmyadmin/apache.conf
//secure phpmyadmin
sudo mysql_secure_installation

sudo service apache2 restart
http://www.crypto-maniac.com/phpmyadmin
sudo add-apt-repository --remove ppa:tuxpoldo/phpmyadmin
----------------------------------------------------
add user mysql
create user crypto identified by "passwordhere";
grant all on *.* to crypto with grant option;

virer tout les root et mettre un mdp pour www-data (cree le user si pas dispo)

----------------------------------------------------------
//fail2ban
https://help.ubuntu.com/community/Fail2ban