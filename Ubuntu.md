**Ubuntu Something**
==============================================
_Some text._

**Apache 2 installation:**

    sudo apt-get install apache2
  	
**PHP installation:**

    sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt



**PhantomJS installation:**

Install [nodejs](https://nodejs.org/en/)

    sudo apt-get install nodejs

Install nodejs-legacy

    sudo apt-get install nodejs-legacy
    
Install [npm](https://www.npmjs.com/)

    sudo apt-get install npm
    
Install [phantomjs](http://phantomjs.org/)

    npm install -g phantomjs
* -g tag will make the installation global for the system

Run the PhantomJS webdriver on a specific port by typing

    phantomjs --webdriver=8888
    
Run the PhantomJS webdriver with option to  ignore SSL invalid certificates

    phantomjs --ignore-ssl-errors=yes --webdriver=81

**CodeSniffer installation:**

Install [PEAR - PHP Extensions and Application Repository](https://pear.php.net/)

    sudo apt-get install php-pear

Install [CodeSniffer](http://pear.php.net/package/PHP_CodeSniffer/redirected)

    sudo pear install --alldeps php_condesniffer
    
Modify php.ini file

    sudo vim /etc/php.ini
    
Add the following line in the php.ini file

    include_path = ".:/usr/share/pear"

Usage

    phpcs test.php
    

**VERY IMPORTANT LINKS**

1.  [How To Install Linux, Apache, MySQL, PHP (LAMP) stack on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)
