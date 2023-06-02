#Install and Configure Tomcat v9.0.50

Use the following commands to create the directory for Tomcat, download it, and install it. (assumes you already have wget installed)

    cd /usr/local

    sudo mkdir apache

    cd /usr/local/apache

    sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.50/bin/apache-tomcat-9.0.50.tar.gz

    sudo tar -zxpvf apache-tomcat-9.0.50.tar.gz -C /usr/local/apache
    

NOTE:

    When you change ownership of the /usr/local/apache directory in the next step, please ensure that you use the same OS user and group you used when changing ownership of the /opt/appdynamics directory previously.
    
Use the command below to change ownership of the Tomcat directory structure.

     sudo chown -R [your-os-user]:[your-os-group] /usr/local/apache
      
Now rename the Tomcat install directory and set the required CATALINA_HOME environment variable using commands below.

    mv apache-tomcat-9.0.50 apache-tomcat-9

    echo "export CATALINA_HOME='/usr/local/apache/apache-tomcat-9/'" >> ~/.bashrc
    source ~/.bashrc


By default no user or account is allowed to access to the Tomcat Manager Web Page and Admin Page. Use the command below to edit the file ”/usr/local/apache/apache-tomcat-9/conf/tomcat-users.xml”

    vi /usr/local/apache/apache-tomcat-9/conf/tomcat-users.xml

Add the following lines to the end of the file just before the last XML tag you see in the file named </tomcat-users> and then save the file.
    
    <!-- User linuxtechi who can access only manager section --> 
    <role rolename="manager-gui" /> 
    <user username="admin" password="welcome1" roles="manager-gui" /> 
File should look like below:

<img width="561" alt="Untitled5" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/b245181e-3cb8-49f5-a37e-87e494ba7088">

By default no remote access is allowed for the Tomcat Manager Web Page. Use the command below to edit the file ”/usr/local/apache/apache-tomcat-9/webapps/manager/META-INF/context.xml”

    vi /usr/local/apache/apache-tomcat-9/webapps/manager/META-INF/context.xml

Comment out the following lines for the Valve tag in the file as seen below and then save the file.

    <!--  
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />  
    -->
    
File should look like below:

<img width="1439" alt="Untitled6" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/7a73d4bd-6e6f-4561-91e2-ce47fa1a4432">

Start Tomcat using the commands below.

    cd /usr/local/apache/apache-tomcat-9/bin

    ./startup.sh
    
Verify you can access the Tomcat Manager Web page from your browser.

    http://{ip-address-or-hostname}:8080/manager/html
    
Enter the user name and password you added to the tomcat-users.xml file previously.

<img width="1102" alt="Untitled7" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/a4e73e04-c5b5-4f4b-b3e6-875920422f0c">


Now stop Tomcat using the commands below.

    cd /usr/local/apache/apache-tomcat-9/bin

    ./shutdown.sh
    
