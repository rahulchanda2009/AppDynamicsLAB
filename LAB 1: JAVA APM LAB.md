#DOWNLOAD JAVA APM AGENT

Download the java agent either from controller or directly via the downloads portal

Upload Java Agent to Application VM

#INSTALL JAVA APM AGENT

Create the directory structure where you will unzip the Java agent zip file.

    cd /opt/appdynamics

    mkdir javaagent
    
Copy the Java agent zip file to the new directory and unzip the file. The name of your Java agent file may be slightly different than the example below. (assumes you uploaded the zip file to the /tmp directory)

    cp /tmp/AppServerAgent-20.3.0.29587.zip /opt/appdynamics/javaagent/

    cd /opt/appdynamics/javaagent

    unzip AppServerAgent-<version>.zip
    
#Update the Java Agent configuration file

If you are using an newer version of the controller where you previously typed in the Application, Tier, and Node names when downloading the Java Agent, then you don’t need to update the Java Agent configuration file.

You will now need to update the Java agent’s XML configuration file. There are three primary ways to set the configuration properties of the Java agent. These take precedence in the following order.

    System environment variables.
    JVM properties passed on the command line.
    Properties within the controller-info.xml file.
    
There are over twenty properties with the controller-info.xml file. There are eight properties that typically need to be changed in the controller-info.xml file.

    controller-host
    controller-port
    controller-ssl-enabled
    application-name
    tier-name
    node-name
    account-name
    account-access-key
    
<img width="782" alt="Untitled" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/515726c5-e39d-4cfc-88d8-7ed00e9c3777">

Find the controller-info.xml file of the Java agent. The path to the file will be similar to the following example. The version directory will be specific to the version that you downloaded.

    cd /opt/appdynamics/javaagent/verXX.X.X.XXXXX/conf
    
 Update the application-name, tier-name, and node-name properties in the file with the following values. Do not change the values of any other properties in the file. If you are using WinSCP to update the file, ensure that the Transfer Settings are set to Text.
 
    <application-name>Supercar-Trader</application-name>
    <tier-name>Web-Portal</tier-name>
    <node-name>Web-Portal_Node-01</node-name>
    
#Add the Java Agent to Tomcat

Perform the following steps to add the Java agent to the Tomcat startup script.

 Use the following commands to stop the running instance of Apache Tomcat.
 
    cd /usr/local/apache/apache-tomcat-9/bin

    ./shutdown.sh\
    
 Find the catalina.sh startup file for Apache Tomcat. The file is located in the following directory.
 
    /usr/local/apache/apache-tomcat-9/bin
    
  Update the catalina.sh file and add the following export command right after line 124 in the file. If you are using WinSCP to update the file, ensure that the Transfer Settings are set to Text
  
      export CATALINA_OPTS="$CATALINA_OPTS -javaagent:/opt/appdynamics/javaagent/javaagent.jar"
      
   Your file should be similar to the following example after you have made the changes and saved the file.
   
 <img width="1037" alt="Untitled1" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/8f3f1912-eeeb-4e55-a36b-3aa604c8c755">
 
 Restart Apache Tomcat using the following commands.
 
    cd /usr/local/apache/apache-tomcat-9/bin

    ./startup.sh
    
 Wait for two minutes and use the following command to ensure Apache Tomcat is running on port 8080.
 
    sudo netstat -tulpn | grep LISTEN
    
 You should see output similar to the following image showing that port 8080 is in use by Apache Tomcat.
 
 <img width="556" alt="Untitled2" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/9d719820-a179-4958-8fdf-592251f7cc90">
 
 
