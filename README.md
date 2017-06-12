# Setup for SDA server

## the LAMP stack:
  - httpd (yum install httpd)
  - php (yum install php php-pdo php-mysql php-mbstring* php-gd)  *php-mbstring not in RHEL repo


## SDA install list (p.2 SDA setup "instructions"):
- Database system / MySql server: mariadb because RHEL doesn't use Oracle MySQL, instead mariadb, will see how this works)  (yum install mariadb-server mariadb
- JKD or JDK 8: OpenJDK Runtime Env, 64-bit server VM  (I didn't install manually so must have been part of RHEL install)
- Apache Tomcat 7 or 8: Tomcat 7.0.69 (I didn't install manually so must have been part of RHEL install)
- tomcat-users.xml file: /usr/share/tomcat/conf/tomcat-users.xml, add the admin user<tomcat-users>
> <user username="admin" password="password" roles="manager-gui,admin-gui"/>
> </tomcat-users>
