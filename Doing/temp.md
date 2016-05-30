### mono framework task 

  1. task는 모노에서 매우 느리다.(순차적으로 스레드를 생성 후 사용한다. - 발생 중에 처리가 되지 않는다.)
  2. task 를 임의로 만들어서 사용 할 수도 있다. - 
  3. 최선은 libevent의 스레드 풀을 사용 하는 것이다. - 
    - 이를 위해 async 메소드와 함께 컨텍스트에서 await을 실행, 리턴 값으로 결과값을 처리 할 수 있게 바꾸어야 한다.
  
  4. tps는 비슷한 성능이 나왔으나 mms가 async쪽이 좀더 빠름
  5. mysql 5.7은 모노 드라이버 문제인지, 성능 변수 문제인지 모르겠지만 연결 문제로 인해 취소
  6. db connection string에서 풀 갯수를 일정 수치로 연결 시킨 뒤 작업하는 것이 낫다.

  7. 캐시 관련 부분은 일반적으로 빨라질 것으로 생각됨, 테스트 필요.
  8. 작은 부분만 수정 한 후 리얼 테스트 필요 - 더미
  
  
  
  
  ### OWIN
  * http://benfoster.io/blog/how-to-write-owin-middleware-in-5-different-steps

