## 원격 접속 허용
  * 참조(http://zetawiki.com/wiki/MySQL%EC%97%90_%EC%9B%90%EA%B2%A9_%EC%A0%91%EC%86%8D_%ED%97%88%EC%9A%A9)
    ```
    # 모든 ip 허용
    INSERT INTO mysql.user (host,user,password) VALUES ('%','root',password('패스워드'));
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
    FLUSH PRIVILEGES;
    ```