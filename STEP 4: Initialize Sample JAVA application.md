#INITIALIZE SAMPLE APPLICATION
#Install application on Apache Tomcat

The Apache Tomcat landing page can be accessed through your web browser with a URL in the format like below.

    http://[application-vm-ip-address]:8080
    
Use the IP address of your Application VM to access the landing page. You should see the Tomcat landing page.

    1 . Click Manager App.

    2 . You will be prompted to enter a username and password. Use following the case sensitive credentials to login to the Tomcat Manager App.

    Username: admin
    Password: welcome1
    
<img width="750" alt="Untitled8" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/1d0e19ea-cb0b-4859-8fc9-92c064a3bc3f">

You should now see the Tomcat Manager App page.

    1 . Enter /Supercar-Trader in the Context Path (required): field.

    2 . Enter the following path in the WAR or Directory path: field.
    
    file://opt/appdynamics/lab-artifacts/app-war-file/Supercar-Trader.war
    
    3 . Click the Deploy button.
    
<img width="1141" alt="Untitled9" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/68053ed1-6913-4ede-a87b-034f8983818d">

Once the deployment is completed, you should see the application running as shown in the following image.

<img width="1138" alt="Untitled10" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/9d6039ce-b707-4247-9a43-e059a83a2950">

The sample application home page is accessible through your web browser with a URL in the format seen below. Enter that URL in your browser’s navigation bar, substituting the IP Address of your Application VM.

    http://[application-vm-ip-address]:8080/Supercar-Trader/home.do

You should see the home page.

<img width="1478" alt="home" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/7ee0f872-13ca-4da2-aa98-52016a848677">


NOTE: 

    Before stating the load generator, make sure to install the AppDynamics java agent

Start the load generation for the sample application

        sudo chmod 754 /opt/appdynamics/lab-artifacts/phantomjs/*.sh

        sed -i -e 's/\r$//' /opt/appdynamics/lab-artifacts/phantomjs/*.sh

        cd /opt/appdynamics/lab-artifacts/phantomjs

        ./start_load.sh
        
You should see similar to the following.

<img width="727" alt="Untitled11" src="https://github.com/rahulchanda2009/AppDynamicsLAB/assets/108357784/12fc9e44-2c80-414f-9409-8ba8544e76ea">


