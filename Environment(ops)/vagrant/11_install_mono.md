### mono install
    ```
    cd /etc/apt
    sudo cp sources.list sources.list.bak
    # repository를 한국으로 바꿔줍니다.
    sudo sed -i 's/ftp.uk.debian.org/ftp.kr.debian.org/g' sources.list
    sudo apt-get update
    # vim을 설치합니다.
    sudo apt-get install -y vim
    # repository를 추가합니다.
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
    echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list
    sudo apt-get update
    # mono-complete를 설치합니다.
    sudo apt-get install -y mono-complete
    # libevent 설치를 합니다.
    sudo apt-get install libevent-core-2.0-5
    sudo apt-get install libevent-extra-2.0-5
    sudo apt-get install libevent-pthreads-2.0-5
    # 15500 포트 방화벽을 해제합니다.
    iptables -I INPUT -p tcp --dport 15500 -j ACCEPT
    iptables -I OUTPUT -p tcp --dport 15500 -j ACCEPT
    iptables-save
    iptables -L
    # reboot 후에도 방화벽이 유지되도록 iptable규칙을 백업합니다.
    iptables-save > /etc/iptables.up.rules
    touch /etc/network/if-pre-up.d/iptables
    sudo echo '#!bin/sh' >> /etc/network/if-pre-up.d/iptables
    sudo echo '/sbin/iptables-restore < /etc/iptables.up.rules' >> /etc/network/if-pre-up.d/iptables
    chmod +x /etc/network/if-pre-up.d/iptables
    # root 계정 비밀번호를 설정합니다.
    echo -e '{password}\n{password}\n' | sudo passwd
    # cabbage 계정을 생성하고 sudo그룹에 추가합니다.
    echo -e '{password}\n{password}\n\n\n\n\n\n\n' | adduser cabbage
    adduser cabbage sudo
    cd /home
    sudo mkdir ma50
    sudo mkdir upload
    sudo chmod 777 /home/ma50
    sudo chmod 777 /home/upload
    ```