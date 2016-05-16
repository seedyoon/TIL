## vagrant up
    ```
    cd /etc/apt
    sudo cp sources.list sources.list.bak
    # repository를 한국으로 바꿔줍니다.
    sudo sed -i 's/ftp.uk.debian.org/ftp.kr.debian.org/g' sources.list
    sudo apt-get update
    # vim을 설치합니다.
    sudo apt-get install -y vim
    # mysql
    sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password password {password}'
    sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password_again password {password}'
    sudo apt-get update
    sudo apt-get install -y mysql-server-5.5
    sudo apt-get install -y mysql-client
    # mysql 계정을 생성하고 외부접속을 허용합니다.
    mysql -uroot -p{password} << EOF
    create user 'cabbage'@'%' identified by '{password}';
    grant all privileges on *.* to 'cabbage'@'%' identified by '{password}';
    flush privileges;
    select * from mysql.user;
    EOF
    # mysql character-set을 utf-8 로 설정합니다.
    sudo sed -i 's/#\sHere\sis/default-character-set\ =\ utf8\n#\ Here\ is/g' /etc/mysql/my.cnf
    sudo sed -i 's/lc-messages-dir\s=\s\/usr\/share\/mysql/lc-messages-dir\ =\ \/usr\/share\/mysql\ncharacter-set-server\ =\ utf8\ncollation-server\ =\ utf8_general_ci/g' /etc/mysql/my.cnf
    # mysql을 재시작합니다.
    sudo service mysql restart
    #redis
    cd /etc
    wget http://download.redis.io/releases/redis-2.8.21.tar.gz
    tar xzf redis-2.8.21.tar.gz
    cd redis-2.8.21
    make
    cd src
    make install
    cd ../utils
    echo -e '\n\n\n\n\n\n' | sudo ./install_server.sh
    cd /etc/redis
    sudo sed -i 's/# requirepass foobared/requirepass {password}/g' 6379.conf
    cd /etc/init.d
    sudo ./redis_6379 stop
    sudo ./redis_6379 start
    # 방화벽을 해제합니다.
    iptables -I INPUT -p tcp --dport 6379 -j ACCEPT
    iptables -I OUTPUT -p tcp --dport 6379 -j ACCEPT
    iptables -I INPUT -p tcp --dport 3306 -j ACCEPT
    iptables -I OUTPUT -p tcp --dport 3306 -j ACCEPT
    iptables-save
    iptables -L
    # root 계정 비밀번호를 설정합니다.
    echo -e '{password}\n{password}\n' | sudo passwd
    # cabbage 계정을 생성하고 sudo그룹에 추가합니다.
    echo -e '{password}\n{password}\n\n\n\n\n\n\n' | adduser cabbage
    adduser cabbage sudo
    ```