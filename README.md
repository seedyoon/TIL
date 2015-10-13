## TPS에 대한 이해
### TPS와 사용자의 상관 관계

  * 사용자의 증가에 따라 TPS는 같이 증가함(시스템이 정상적으로 처리된다는 가정)

  * 응답 시간이 증가할수록 TPS는 감소함

### TPS와 동시 사용자의 상관 관계
  * Concurrent Usre = TPS * Request Interval
    * 예를 들면 동시 사용자가 20명이 접속되어 서버에 요청을 하는데, 정확하게 초당 2건씩 서버가 처리 되고 있다면, 사용자들의 호출 간격(Request Interval)은 평균 10초일 것임
    * 공식에 적용하면 
      * 20명 / 2 TPS = 10초
      * 20명 = 2 TPS * 10초
    * 와 같은 의미이다.

    * 동시 사용자 1명은 정확히 10 초 간격으로 호출하였으며, 서버는 동시에 2개씩 처리함. 동시사용자 20명
    * 동시 사용자 20명이 정확히 10초 간격으로 호출함. 2 TPS
    * 동시 사용자 20명이 접속하였고, 서버가 초당 2개씩 처리함. Request Interval 10초

    * Concurrent User = TPS * ( Response Time + Think Time)
    * TPS = Concurrent User / Reuqest Interval
    * Active User = TPS * ( Response Time)

  * 예를 들어 전체 업무의 목표는 50 TPS이며, 동시 사용자 분석 결과 300명으로 확인 됨. 성능 수행시 호출 간격은 얼마로 하는것이 적절한가?
    * 300 = 50 * Request Interval
    * Request Interval = 6초

  * 동시 사용자가 240명이고, 호출 건수를 분석한 결과 20 TPS가 산출되었음. 하지만 더미 클라이언트가 100명이라면 호출 간격을 얼마로 테스트 해야 하는가>
    * 240명 / 20 TPS = 12초, 100명 / 20 TPS = 5초로 환산
