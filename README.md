# Learning to setup an RHLE\Kickstart build

- make a couple of ks.cfg files using kickstart generator <https://access.redhat.com/labs/kickstartconfig/>  
- edit a version of sgurnick's kickstart file for the data archive
graphics-bui(ld) kc.cfg use: https://raw.githubusercontent.com/jmjamison/RHEL-kickstart-install/sda-server/ks.cfg
- LAMP stack:
  - httpd (yum install httpd)
  - php (yum install php php-pdo php-mysql php-mbstring* php-gd)  *php-mbstring not in RHEL repo
  - mariadb:  RHEL doesn't use Oracle MySQL, instead mariadb, will see how this works)  (yum install mariadb-server mariadb


```
