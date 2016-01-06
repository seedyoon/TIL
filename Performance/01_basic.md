# 성능 기초 이론
## 기초 용어
### Transaction
  * 성능 테스트의 응답시간 측정의 업무 단위
  * Response Time
    * 사용자의 요청(Request)을 처리하는 시간을 응답시간이라고 하며, 서비스를 접속한 사용자가 특정 컨텐츠를 제공 받기 위해서 서버로 요청을 보내고
    * 서버로부터 응답을 모두 받을 때까지의 시간을 응답 시간이라고 함
'''
Response time = Network Time + Server Time(Web + App + DB) + Client Time
'''

### Think time
  * 사용자 요청간의 대기시간
  * 사용자가 서버로부터 컨텐츠를 제공 받고 해당 컨텐츠를 확인 하는 시간이며, 이 시간은 다음 컨텐츠를 요청하기 전까지의 시간과 같음
    * Request Interval : Response Time + Think Time

### Concurrent User
  * Concurrent User는 동시 사용자로 해당 시스템을 사용하기 위해 PC 앞에 앉아 있는 사용자를 의미함
  * 즉! 시스템 세션을 유지하고 있는 사용자라고 이야기 할 수 있음
      * Name User : 해당 시스템에 접소깅 가능한 사용자.

### Active user
  * Request 요청을 하여 응답을 기다리고 있는 사용자, 즉 클라이언트 환경에서 명령을 실행하고 나서 결과가 올 때 까지 기다리고 있는 사용자.
  *  Concurrent User = Active User + Inactive User

### Peak Time
  * 시스템 요청(Request)가 가장 많은 시간을 의미 함.

### TPS
  * Transaction per Second 로 사용자의 요청(Request)에 대한 초당 처리된 건수를 의미 함( 시스템에서 단위 시간당 처리되는 트랜잭션 건수)
    * TPM( Transaction Per Minute)
    * TPH( Transaction Per Hour)
    * 3600TPH = 60PTPM = 1 TPS