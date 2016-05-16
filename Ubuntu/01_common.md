### 다운로드 소스 변경
    ```
    cd /etc/apt
    sudo cp sources.list sources.list.bak
    ```
  
### repository를 한국으로 바꿔주기

    ```
    sudo sed -i 's/ftp.uk.debian.org/ftp.kr.debian.org/g' sources.list
    sudo apt-get update
    ```

### 방화벽
    ```
  # 방화벽 설정
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
    ```

