#shell 기본 속성
## 한글 입력
  * 리눅스 및 유닉스 계열 OS에서 폴더 찾기 및 한글 입력이 들어간 폴더를 사용 할 때 실제 이름을 넣으면 찾을 수 없음
  * 쌍따옴표로 유니코드를 넣어주면 찾을 수 있음
    * /home/ma50/05_테이블  ==> X 
    * /home/ma50/05_”테이블” ==> O

## 주요 커맨드
### chmod 
  * 폴더 및 파일의 읽기 쓰기 권한을 변경할 때 
  * chmod 777 {path:file}

### chown
  * 폴더 및 파일의 사용 권한을 줄 때 사용
  * chown jenkins:jenkins {path:file}

### 사용중인 포트 보기
  * netstat -an | grep "LISTEN"
  * netstat -anp | grep LISTEN | grep : 포트 번호
  * ps -ef | grep "프로그램명"
  
  