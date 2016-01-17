### 빌드
  * encoding이 설정되어 있지 않다는 warning 메시지.

'''  
[WARNING] File encoding has not been set, using platform encoding MS949, i.e. build is platform dependent!
'''

  * 설정
'''
	<properties>
		<project.build.sourceEncoding>utf-8</project.build.sourceEncoding>
	</properties>
'''

  * 위와 같이 설정했음에도 같은 에러가 발생했다. 그 이유는 reporting 인코딩 설정을 다음과 같이 추가해야 warning 메시지가 사라진다.
'''
	<properties>
		<project.build.sourceEncoding>utf-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>utf-8</project.reporting.outputEncoding>
	</properties>
'''