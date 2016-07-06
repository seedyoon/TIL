## 원격 접속 허용
  * 참조(http://zetawiki.com/wiki/MySQL%EC%97%90_%EC%9B%90%EA%B2%A9_%EC%A0%91%EC%86%8D_%ED%97%88%EC%9A%A9)
    ```
    # 모든 ip 허용
    INSERT INTO mysql.user (host,user,password) VALUES ('%','root',password('패스워드'));
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
    FLUSH PRIVILEGES;
    ```
    
    INSERT INTO mysql.user (host,user,password) VALUES ('%','cabbage',password('cabbage#12!!'));
    GRANT ALL PRIVILEGES ON *.* TO 'cabbage'@'%';
    
  * mysql user 생성시 ERROR 1364 (HY000): Field 'ssl_cipher' doesn't have a default value
    ```
    ERROR 1364 (HY000): Field 'ssl_cipher' doesn't have a default value
    Mysql 버전이 높아지면서 보안관련 인한 오류입니다.

    User 생성시 Host, User ,Password, ssl_cipher, x509_issuer, x509_subject 를 입력 해 주셔야 합니다.
    ssl_cipher, x509_issuer, x509_subject 값은 '' 빈값을 입력하세요.

    ex)
      insert into user (Host, User, Password, ssl_cipher, x509_issuer, x509_subject ) 
      values('localhost','사용자명',password('비밀번호'),'','','');
      ERROR 1364 (HY000): Field 'authentication_string' doesn't have a default value

    * mysql 5.5 에서 user 생성시 authentication_string 필드 추가. '' 값으로 넣어 주세요.
    ex)
      insert into user (Host, User, Password, ssl_cipher, x509_issuer, x509_subject, authentication_string) 
      values('localhost','사용자명', password('비밀번호'),'','','','');
      
    ```