# PROJECT 1: LAMP STACK IMPLEMENTATION

## Step 1 — installing apache and updating the firewall

#update a list of packages in package manager

`sudo apt update` 

#run apache2 package installation

`sudo apt install apache2`

#To verify that apache2 is running as a Service in our OS

`sudo systemctl status apache2`

![Apache2 Status](./apache2_status.JPG)

#how we can access it locally in our Ubuntu shell

`curl http://localhost:80
or
 curl http://127.0.0.1:80
 `

![Apache2 Status](./curl.JPG)

#retrieve Public IP address from aws console

`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`

![Apache2 Status](./meta%20from%20console.JPG)

#retrieve webpage from Public internet 

![Apache2 Status](./webpage.JPG)

## Step 2 — Installing MYSQL

#run MYSQL package installation

`sudo apt install mysql-server`

#log in to the MySQL console

`sudo mysql`

#run script to set a password for the root user

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

#run security script that comes pre-installed with MySQL. This script will remove some insecure default settings

`sudo mysql_secure_installation`

## Step 3 — Installing PHP

#run PHP package installation

`sudo apt install php libapache2-mod-php php-mysql`

#confirm your PHP version
`php -v`

## STEP 4 — CREATING A VIRTUAL HOST FOR WEBSITE USING APACHE

#Create the directory for a new procaject called Projectlamp

`sudo mkdir /var/www/projectlamp`

#Assign ownership of the directory to current system user

`sudo chown -R $USER:$USER /var/www/projectlamp`

#create and open a new configuration file in Apache’s sites-available directory and paste in the configs

`sudo vi /etc/apache2/sites-available/projectlamp.conf`

#use a2ensite command to enable the new virtual host

`sudo a2ensite projectlamp`

#disable Apache’s default website use a2dissite

`sudo a2dissite 000-default`

#make sure your configuration file doesn’t contain syntax errors

`sudo apache2ctl configtest`

#reload Apache so these changes take effect

`sudo systemctl reload apache2`

#Testing new website URL using IP address

![Apache2 Status](./lamp-web.JPG)

## STEP 5 — ENABLE PHP ON THE WEBSITE

#Create a new file named index.php inside the custom web root folder

`vim /var/www/projectlamp/index.php`