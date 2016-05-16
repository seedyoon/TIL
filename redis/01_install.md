### source 설치
    ```
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

    ```