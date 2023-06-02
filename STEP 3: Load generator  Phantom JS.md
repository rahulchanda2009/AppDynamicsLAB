#Install PhantomJS v2.1.1

Use the commands below to install PhantomJS that will be needed to provide the load generation for the lab application.

    cd /tmp

    sudo yum install glibc fontconfig freetype freetype-devel fontconfig-devel wget bzip2

    cd /tmp

    wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2
    
    cd /tmp

    sudo tar xvjf phantomjs-2.1.1-linux-x86_64.tar.bz2 -C /usr/local/share/

    sudo ln -sf /usr/local/share/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin
    
Now use the command below to validate the install of PhantomJS

    phantomjs --version
    
You should see output from the command like below.

    [ec2-user@ip-172-31-44-9 phantomjs]$ phantomjs --version
    2.1.1
    
NOTE:

If phantomjs -v gives error : 
      
      -bash: phantomjs: command not found
      
Use the below commands:

    sudo ln -s /usr/local/share/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/share/phantomjs
    sudo ln -s /usr/local/share/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/bin/phantomjs
    
Now use the command below to validate the install of PhantomJS

    phantomjs --version
    
You should see output from the command like below.

    [ec2-user@ip-172-31-44-9 phantomjs]$ phantomjs --version
    2.1.1
