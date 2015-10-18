## 부동 소수점 오류
### javascript를 사용하는 부분에서 long, ulong대신 text(string)으로 인자값을 보내자.
  * 발단
    * 클라이언트 접속, 데이터 상에서는 정상적으로 생성 및 찾기가 가능
	* GM 툴에서 우편 생성 시, PostUID(ulong) 가 실제 값과 다르게 되는 오류  
  
  * 디버깅 과정
    * 레디스 클라이언트가 값을 잘 못 가져오는 것으로 판단 
	  * 실제 redis 클라이언트는 ulong타입이 없음  
	  * 레디스 클라이언트의 value값(RedisValue)은 string, long, int 등을 제공, ulong은 없음 
	  * 정수 값(ulong)을 집어 넣을 경우 StackExchange.redis에서는 자신들이 사용하는 값인 RedisValue에 int64 가 아닌 float로 치환(has integer false), 이로 인해서 부동 소수점이 들어가는 것으로 레디스 매니저에서 보임 
	  * 전체 변수 값에서 앞에 4비트를 제거 하면, 부동 소수점 오류는 사라짐, 하지만 guid의 경우 해당 대역폭을 줄이기가 곤란
	* 새로운 버전의 레디스 매니저의 뷰가 string 입력 시, 기본 설정이 plain text가 아닌 view로 된 것을 발견
	  * 해당 설정을 변경하자, 정상적으로 값이 보임... (이게뭐냐)
	  * json 포멧의 부동 소수점 문제는 이전에 couchbase에서도 발생 했었음
	  * c# 코드 전반적인 부분에서 json 타입에서 변환(serialze)해서 사용하고 있기 때문에 ulong타입에 대한 걱정이 생김
	* 실제 코드에서 전환 되는 것을 보니 문제 없었음 "json.net" 은 ulong을 제대로 표현 해 줌 !!
    * 참조
	  * json 타입 텍스트로 보내도 데이터 타입(ulong)으로 변환을  시킴
  
    * 문제 발견 
      * postUID를 검사하기 위해 GM Tool에서 받은 gameUID를 입력 받아옴, 해당 부분의 값을 검사 한 결과 floating pont error 발생
	  * html 파일에서 입력 값이 number로 되어서 전달, html의 number필드는 javascript 로서 해당 에러가 발생
	  * 입력 값 부분을 string 으로 바꾼 뒤 확인 해보니 이상 없었음
	  * 결과값을 받는 부분(브라우저로 표현되는 부분)들도 동일한 문제 발생
	  
	* 문제 해결
	  * 값을 보내는 부분에서 int64 수를 전달하는 부분을 number => text으로 변경
	  * 값을 표현해 주는 부분도 string으로 변경
	  * 상황 종료 
	   