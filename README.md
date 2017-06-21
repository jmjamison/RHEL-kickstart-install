# Setup for SDA server

## add desktop Xfce - not essential but I like a simpler desktop  
    - you will need the EPEL library, also for mysql   - add now if useing Xkfce 
    - add EPEL epel-release-6-8.noarch.rpm (dependencies for mysql workbench)
          - yum-config-manager --enable epel
     
    - yum install @xfce

## the LAMP stack:
  - httpd 
      - yum install httpd
      - systemctl enable httpd.service
      - systemctl start httpd.service
      - check 'localhost'
  - php 
      - yum install php php-pdo php-mysql php-mbstring* php-gd)  *php-mbstring not in RHEL repo
      - test.php page '<?php phpinfo(); ?>'
  - Database system / MySql server: mariadb because RHEL doesn't use Oracle MySQL, instead mariadb. According to Yutah/SDA, this hypothetically works with SDA but I ran into some issues - for now using MySQL and will try mariadb late
      - remove mariadb (yum remove mariadb, yum clean all)
      - add EPEL epel-release-6-8.noarch.rpm (dependencies for mysql workbench)
          - yum-config-manager --enable epel
      - download/add the mysql repo:  yum install mysql-community-{server,client,common,libs}-*
      - install mysql workbench
      
     - WIERD-SHIT-to-be-aware-of:  the mysql server 5.7.x generates a random password for the server. Find by "grep 'temporary password' /var/log/mysqld.log". Use that to log in and then chenge the password.
          


## SDA install list (p.2 SDA setup "instructions"):
- JKD or JDK 8: OpenJDK Runtime Env, 64-bit server VM  (I didn't install manually so must have been part of RHEL install)
  - set JAVA_HOME, created the setenv.sh file in /usr/share/tomcat/bin
- Apache Tomcat 7 or 8: Tomcat 7.0.69 (I didn't install manually so must have been part of RHEL install)
- tomcat-users.xml file: /usr/share/tomcat/conf/tomcat-users.xml, add the admin user<tomcat-users>  
  \<user username="admin" password="password" roles="manager-gui,admin-gui"\/>  \</tomcat-users\>'
- SDA docs, p.3 for starting or stoping tomcat, use 'tomcat stop/start/version' rather than what's in "documentation"
