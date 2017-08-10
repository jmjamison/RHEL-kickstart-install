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
      
      - if SELinux security is set at 'enforce', change to 'permissive' at least while testing setup.
      
  - Database system / MySql server: mariadb because RHEL doesn't use Oracle MySQL, instead mariadb. According to Yutah/SDA, this hypothetically works with SDA but I ran into some issues - for now using MySQL and will try mariadb late
      - remove mariadb (yum remove mariadb, yum clean all)
      - add EPEL epel-release-6-8.noarch.rpm (dependencies for mysql workbench)
          - yum-config-manager --enable epel  
       - insall mysql57-community-release-el7-11.noarch.rpm  (repo from mysql site)
            - yum install mysql-community-{server,client,common,libs}-*
            - start: service mysqld start (system message: 'redirecting to /bin/systect. start mysql.service')
           - ***NOTE***:  the mysql server 5.7.x generates a random password for the server. Find by grep-ing for 'temporary password' in  /var/log/mysqld.log". Use that to log in and then chenge the password.
           - ***NOTE#2***:  be careful when searching for the temp password - it may be split across a line (ie. ![linebreak]something...)
          
      - install mysql workbench (if not installed)yum 
        - also from mysql sitesys
        - rpm package and rpm package debug info
      
     


## SDA install list (p.2 SDA setup "instructions")
### Java, JKD, etc
- JKD or JDK 8: OpenJDK Runtime Env, 64-bit server VM  (I didn't install manually so must have been part of RHEL install)
  - set JAVA_HOME, created the setenv.sh file in /usr/share/tomcat/bin
### Apache Tomcat 
    - currently 7 or 8
 - DON'T use the tomcat install in RDEL. This will not work correctly or at all.
 - DO USE the rpm from Apache site: <http://tomcat.apache.org/download-70.cgi> (site has downloads for v.7,8, 9) 
 The apache packages includes the startup, shutdown files though you do have to create your own setenv script. (Currently keep a spare copy of this as backup.
- tomcat-users.xmltomc file: /usr/share/tomcat/conf/tomcat-users.xml, add the admin user<tomcat-users>  
  \<user username="admin" password="password" roles="manager-gui,admin-gui"\/>  \</tomcat-users\>'
- SDA docs, p.3 for starting or stoping tomcat, use 'tomcat stop/start/version' rather than what's in "documentation"

### SDA files
-- create in /var/www/ the sda folder
-- in /var/www/sda create two folders   docs and sdaprogs
    --- the sdaprogs.zip is unstipped int sda progs
### sdamanager

### sdaweb
