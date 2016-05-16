### too many open files
  * 특정 프로그램 구동 시, Too many open files 에러 발생 
  * 나같은 경우는 소켓 연결을 많이 하는 프로그램 구동 시(mysql connect), 해당 에러 발생
  * ulimit -a 로 확인해 보면 기본값(1024)로 설정 
  * 참조( http://jabjong.tistory.com/36) 에 따라 ulimit -n으로 수정 후 에러 발생 안함
  * 재 부팅, 혹은 로그인 시 변경을 위해 /etc/security/limits.conf 파일 수정하여 해결.
  * root로 로그 인 시, PAM 모듈을 참조하는 것만 반영 되므로 ,  /etc/pam.d 모듈을 열어서 수정 해 주어야 함
    * /root/.bash_profile 에 ulimit -n XXXX를 넣어줘서 해결.
    
  * limits.conf와 오픈 파일 개수 (http://lunatine.net/limits-conf-nofile-big-value-effect/)