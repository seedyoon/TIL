### mysql 5.5 설치
    ```
    sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password password cabbage#12!!'
    sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password_again password cabbage#12!!'
    sudo apt-get update
    sudo apt-get install -y mysql-server-5.5
    sudo apt-get install -y mysql-client
    ```

