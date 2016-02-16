## 패킷의 크기를 지정하는 MTU
  * MTU(Maximum Transmission Unit)
    * 네트워크 인터페이스에서 세근먼트 없이 보낼 수 있는 최대 데이터그램 크기
    * 데이터가 해당 값 이상이라면 여러개의 패킷으로 분할 되어 나감, 즉 한번에 패킷이 나갈 수 있는 최대 크기
      * 점보 프레임(9000)같은 것도 존재 하지만 일반적으로 MSS(Maximum segment size)
      * MTU = MSS + TCP/IP header
      * MSS = MTU - 40(IP + TCP header)   
    * TCP 상에서 일반적인 패킷 크기 = 1460
      * RPC 1323 time stamp 옵션으로 인해 1448로 됨.
    
## MTU 확인
  * netsh
    * cmd netsh interface ip show interaface
    ``` 
    색인     메트릭         MTU          상태                이름
    ---  ----------  ----------  ------------  ---------------------------
    3          10        1500  connected     이더넷
    1          50  4294967295  connected     Loopback Pseudo-Interface 1
    9          10        1500  disconnected  이더넷 2
    7          20        1500  connected     VirtualBox Host-Only Network
    ```
    
  * ping으로 확인하기
    ```
    C:\Users\guild_000>ping -f -l 1472 google.com
    Ping google.com [1.255.22.168] 1472바이트 데이터 사용:
    1.255.22.168의 응답: 바이트=1472 시간=2ms TTL=58
    1.255.22.168의 응답: 바이트=1472 시간=2ms TTL=58
    1.255.22.168의 응답: 바이트=1472 시간=2ms TTL=58
    1.255.22.168의 응답: 바이트=1472 시간=7ms TTL=58

    1.255.22.168에 대한 Ping 통계:
    패킷: 보냄 = 4, 받음 = 4, 손실 = 0 (0% 손실),
    왕복 시간(밀리초):
    최소 = 2ms, 최대 = 7ms, 평균 = 3ms

    C:\Users\guild_000>ping -f -l 1473 google.com

    Ping google.com [1.255.22.168] 1473바이트 데이터 사용:
    패킷 조각화가 필요하지만 DF가 설정되어 있습니다.
    패킷 조각화가 필요하지만 DF가 설정되어 있습니다.
    패킷 조각화가 필요하지만 DF가 설정되어 있습니다.
    패킷 조각화가 필요하지만 DF가 설정되어 있습니다.

    1.255.22.168에 대한 Ping 통계:
    패킷: 보냄 = 4, 받음 = 0, 손실 = 4 (100% 손실),
    ```    
## 결론
    * 일반적으로 게임서버에서는 한번에 보낼 크기만큼 보내는 것이 좋을 듯, 너무 채워서 보내면 지연이 되고, 너무 짧으면 과부하니 +_+
    * 1448 - packet header로 보낼 크기 제한을 잡자. 
  