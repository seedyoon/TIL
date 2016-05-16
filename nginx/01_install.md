## 설치
```
# nginx 1.8.0 버전을 사용하기 위해서 repository를 추가합니다.
    sudo sed -i 's/ftp.uk.debian.org/ftp.kr.debian.org/g' sources.list
    sudo echo 'deb http://nginx.org/packages/debian/ wheezy nginx' >> sources.list
    sudo echo 'deb-src http://nginx.org/packages/debian/ wheezy nginx' >> sources.list
    cd /tmp && wget http://nginx.org/keys/nginx_signing.key
    apt-key add nginx_signing.key

# nginx를 설치합니다.
    sudo apt-get install -y nginx
    
# nginx 버전을 확인합니다.
    nginx -v
    
# nginx 상태를 확인합니다.
    sudo service nginx status
    cd /etc/nginx
    sudo cp nginx.conf nginx.conf.bak
    
# nginx.conf 수정은 여기에서 합니다.
# 수정된 config파일을 적용하기 위해 nginx 를 재시작합니다.
    sudo service nginx restart

```