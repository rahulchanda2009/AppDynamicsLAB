#Installation Steps

Before you download the lab artifacts zip file, use the commands below to create the directory where you’ll copy the file to.
 
<img width="949" alt="Untitled" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/49956ceb-8eb3-48df-80cc-ab50edbf6dae">
 
If wget is not already installed on your Linux host you can try using the command below to install it. (command may vary based on your Linux distro)

    sudo yum install wget
  
 Either use the attached lab-artifacts.zip or can use the below link:
  
    cd /opt/appdynamics/lab-artifacts

    wget https://povplaybook.appdpartnerlabs.net/zip/lab-artifacts.zip

Install Java v1.8

     sudo yum install java-1.8.0
  
     java -version
  
   The output should look similar to this


<img width="739" alt="Untitled1" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/ac78ec87-4fe9-492a-bc3e-f4381021fad1">
 
 Begin Installing MySQL v5.7
 
 Use the commands below to install MySQL 5.7 Community Version (assumes you already have wget installed)
 
    wget https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm

    sudo rpm -ivh mysql57-community-release-el7-9.noarch.rpm

    sudo yum install mysql-server
    
 Resolving GPG Key Error
 
 If you get a GPG public key error like the one seen below, then follow the next steps to resolve it.
 <img width="816" alt="Untitled2" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/754d7d6b-c907-456a-b28c-c1620a829a59">
 
 Create a new public key file using the commands below.
 
    cd /tmp

    touch mysql_pubkey.asc
    
 Copy the contents of key mysql to your saved ‘mysql_pubkey.asc’ file should look like the example below.

<img width="576" alt="Untitled3" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/c694de52-071d-4e83-b123-87e6caf52dd7">
    
 Import the new public key file using the commands below.
 
     gpg --import mysql_pubkey.asc

    sudo rpm --import mysql_pubkey.asc
    
Now run the installation again using the commands below. The installation should now succeed.

    sudo yum install mysql-server

Finish Installing MySQL v5.7

Start the MySQL service using the command below.

    sudo systemctl start mysqld

 Verify the MySQL service.
 
    service mysqld status
 
 The output should look similar to this.
 
<img width="1029" alt="Untitled4" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/f1764154-71ad-4961-8e82-6d7111cbf4e3">

Secure MySQL - During the installation process, a temporary password is generated for the MySQL root user. Locate it in the mysqld.log with this command.

    sudo grep 'temporary password' /var/log/mysqld.log
    
Make note of the password, which you will need in the next step to secure the installation and where you will be forced to change it. Execute the secure mysql installation tool with the command below.

    mysql_secure_installation

#NOTE:
    
    Make sure the new password you enter next is Welcome1! otherwise the application will not be able to connect to the database.

Now enter the following.

     New password: Welcome1!
     Remove anonymous users? n
     Disallow root login remotely? n
     Remove test database and access to it? n
     Reload privilege tables now? y
  
Initialize Application Database

Now we will run the database scripts that create the database schema, the tables, and the data for our application. Change directory to where the database scripts are located.

    cd /opt/appdynamics/lab-artifacts/db-scripts
    
Use the following commands to run the database scripts.
    
    mysql -u root -pWelcome1! < mysql-01.sql

    mysql -u root -pWelcome1! < mysql-02.sql

    mysql -u root -pWelcome1! < mysql-03.sql
    
   
