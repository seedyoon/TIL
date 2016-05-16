### mysql 5.7 설치
  * 참조 (https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04, http://egloos.zum.com/kwaknu/v/5212895)

  *  install 
    ```
    # 일반 설치가 안됨, 다운로드 후 ~
    $wget http://dev.mysql.com/get/mysql-apt-config_0.6.0-1_all.deb
    $sudo dpkg -i mysql-apt-config_0.6.0-1_all.deb
    $sudo apt-get update
    $sudo apt-get install mysql-server
   
    ```
    
  * configuring mysql
    ```
    $sudo mysql_secure_installation
    
    # 버전 확인
    $mysql --version
    $sudo mysql_install_db

    ```
    
  * 원격 접속 에러 (Table 'performance_schema.session_variables' doesn't exist)
    ```
    mysql_upgrade -u root -p --force
    
    
    update user set authentication_string=password('{password}') where user='{userid}';
    FLUSH PRIVILEGES;
    ```
    
  * devart mysql 배포 에러 (http://forums.devart.com/viewtopic.php?f=23&t=32784)

     ```
     set @@global.show_compatibility_56=ON; 
     ```
    
    
     
    
     
  