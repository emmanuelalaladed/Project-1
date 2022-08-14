# PROJECT-1 DOCUMENTATION

##  Step-1 : Installing APACHE and updating the Firewall

1. Update the Ubuntu package manager
- sudo apt update

2. Install Apache server
- sudo apt install apache2

3. Verify the installed apache2 server
- sudo systemctl status apache2

  ![APACHE2_Status](./images/APache2-status.PNG)

4. Accessing the Apache2 server on the Ubuntu shell 
-  curl http://localhost:80 or  curl http://127.0.0.1:80


  
   ![APACHE2_On Ubuntu shell](./images/Apache-view1.PNG)

5. Accessing the Apache2 server via brower on port 80

- First retrieve the Public IP address of the Ubuntu install on the EC2 instance.

  *curl -s http://169.254.169.254/latest/meta-data/public-ipv4*

 - Web browser access to the Apache2 server

   ![APACHE2_On Web Browser](./images/Apache-view2.PNG)


## Step-2 : INSTALLING MYSQL

1. Install mysql server
 - *sudo apt install mysql-server and log into the MySql*

   ![Mysql-instalation](./images/mysql-instalation.PNG)
 - Setting the root password for access the mysql database

   ![Mysql-password](./images/mysql-root-password.PNG)

- Password Access to the Mysql Database

  ![Password Access](./images/Password-access.PNG)


## Step-3 : INSTALLING PHP

1. Install the three packages php, php-mysql (for communication between PHP and Mysql database)  and libapache2-mod-php (for Apche server to handle PHP files)

- *sudo apt install php libapache2-mod-php php-mysql*
- check the PHP version

*php -v*
![Php-version](./images/php-version.PNG)


## Step-4 : CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE

1. Create a domain directory and change the ownership.

![Domain](./images/domain-folder.PNG)

2. Creatig a new configuration file inside the Apache's sites-available directory
 - *sudo vi /etc/apache2/sites-available/projectlamp.conf*

 ![Create a conf. file](./images/conf-file.PNG)

 - Confirm the the created conf. file
   *sudo ls /etc/apache2/sites-available*

   ![The created configuration file](./images/conf.%20file-confirmation.PNG)

-  Enable the new virtual host with the command 
   *sudo a2ensite projectlamp*
- Disable the default website, and confirm the configuration of the have no synthax error.

   ![Disabling the Default website and confirming the configuration is sythax error free](./images/disable-default.PNG)

- Create a new website using
*sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/html/project_lamp/index.html*

- Display the new website from the web browser using 

    http://44.202.1.98
    
    ![New-Website](./images/new-website.PNG)


 ## Step-5 :  ENABLE PHP ON THE WEBSITE

 1. In order for index.php to be the landing page for the website, the dir.conf needs to be edited.

    *sudo vim /etc/apache2/mods-enabled/dir.conf*

    - Edit the file as shown below

    ![Edit the Dir.conf file](./images/dir.conf.PNG)

    - Then reload the Apache2 server with the command

      *sudo systemctl reload apache2*

    - Create a new file name index.php

      *vim /var/www/html/projectlamp/index.php*

    - Add the following text into the new blank index.php file.
     
          <?php
      phpinfo();

     ![The new Websi](./images/php-content.PNG)

2.  Launch the new PHP website from the web browser

       ![The new PHP website](./images/php-website-new.PNG)

    

       
   


