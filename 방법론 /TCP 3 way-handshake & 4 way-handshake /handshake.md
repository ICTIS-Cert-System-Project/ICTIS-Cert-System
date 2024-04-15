# TCP 3 Way-Handshake & 4 Way-Handshake
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 11일 

## TCP *(Transmission Control Protocol)*
인터넷 상에서 데이터를 메시지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜임. </br>
TCP는 애플리케이션에게 신뢰적이고 연결지향형 서비스를 제공함. </br>
따라서, 서버와 클라이언트 간에 데이터를 신뢰성있게 전달하기 위해 만들어진 프로토콜임. </br>
TCP는 장치들 사이에 논리적인 접속을 성립(establish)하기 위해서 3 Way-Handshake를 사용함. 

## TCP 3 Way-Handshake
TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정임.</br>
TCP/IP 프로토콜을 이용해서 통신하는 응용프로그램은 데이터를 주고받기 전에 먼저 연결을 진행함. </br>
3-Way Handshake는 이 연결 과정을 의미함.


- 편의를 위해 양쪽 Host를 각각 클라이언트, 서버라고 부르고 설명함.
  - 연결을 먼저 요청하는 Host -> **클라이언트**
  - 연결을 요청하는 Host -> **서버**
- 실제로 TCP는 양방향 통신이기에 **‘클라이언트-클라이언트’** 의 형태가 존재함.

## 3 Way-Handshake에서 사용되는 TCP 헤더 필드
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbln89g%2Fbtr7hQRnxHG%2F5K5g4MUKFvcfwIjjYeckh0%2Fimg.png">

__Sequence Number__

- Segment에 있는 **첫 번째 바이트의 바이트 스트림 번호**임.
  - TCP는 데이터를 단지 순서대로 정렬되어 있는 바이트 스트림으로 봄.
  - ex) 0\~999, 1000\~1999의 Segment를 보낼 때 seq# = 각각 0, 1000
- TCP 연결, 종료 시에는 **Sequence Number를 임의의 랜덤 값으로 설정**함.
  - Sequence Number가 노출되면 공격자가 위조 패킷을 보낼 수 있어 보안을 위해 랜덤 값으로 설정함.

</br>

__Acknowledgement Number__

- 받고 싶은 다음 바이트 번호를 의미함.
  - ex) 0\~999, 1000\~1999의 Segment를 받았을 때 ack# = 각각 1000, 2000

</br>

__Control bits__

- **ACK** (Acknowledgement)
  - 패킷을 받았다는 응답을 할 때 사용함.
  - Acknowledgement Number가 유효한지를 나타냄.
  - 최초 연결의 첫 번째 세그먼트를 제외한 모든 Segment의 ACK 비트는 1로 설정함.
    + 최초 연결의 첫 번째 Handshake 과정에서는 응답할 요청이 없기 때문임.

</br>

- **SYN** (Synchronize Sequence Number)
  - **연결을 요청** 할 때 SYN bit를 사용함.
  - 연결을 요청하는 경우에 SYN bit를 1로 설정함.
    - 따라서, SYN bit = 1 이면 TCP 연결을 요청하는 과정인 것을 알 수 있음.
  - 다른 모든 경우에는 SYN bit를 0으로 설정함.
    - 연결 요청에 응답하는 마지막 Handshake의 Segment에서도 SYN bit를 0으로 설정함.
   
  ## 3 Way-Handshake의 역할
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcolneJ%2FbtrEE0Ggbwx%2FVzhD9eByIMPCRSn6QSGGy1%2Fimg.png">
위의 이미지에서 화살표 방향을 보면 알 수 있겠지만, 이 3way handshake는 양쪽 모두 데이터를 전송할 준비가 되어있다는 것을 보장하고, 실제로 데이터 전달이 시작하기 전에 다른 한쪽이 준비되었다는 것을 알 수 있도록 해줌.

 
다음 이미지에 작성되어있는 상태와 SYN과 ACK의 플래그 내용은 다음과 같다.

 
[State 정보]

- CLOSED: 포트가 닫힌 상태
- LISTEN: 포트가 열린 상태로 연결 요청 대기 중
- SYN_RECV: SYNC 요청을 받고 상대방의 응답을 기다리는 중
- ESTABLISHED: 포트 연결 상태
- TIME-WAIT: Server로부터 FIN을 수신하더라도 일정시간(default: 240초)동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 말함.


[Flag 정보]

- TCP Header에는 CONTROL BIT(플래그 비트, 6bit)가 존재하며, 각각의 bit는 "URG-ACK-PSH-RST-SYN-FIN"의 의미를 가짐.
  - 즉, 해당 위치의 bit가 1이면 해당 패킷이 어떠한 내용을 담고 있는 패킷인지를 나타냄.




- **SYN**(Synchronize Sequence Number)

  - 연결 설정.
  - Sequence Number를 랜덤으로 설정하여 세션을 연결하는 데 사용하며, 초기에 Sequence Number를 전송함.
  - 따라서, Connection을 생성할때 사용하는 flag임.


- **ACK**(Acknowledgement)

  - 응답 확인.
  - 패킷을 받았다는 것을 의미하는 flag.
  - Acknowledgement Number 필드가 유효한지를 나타냄.
  - 양단 프로세스가 쉬지 않고 데이터를 전송한다고 가정하면 최초 연결 설정 과정에서 전송되는 첫 번째 세그먼트를 제외한 모든 세그먼트의 ACK 비트는 1로 지정된다고 생각할 수 있음.


- **FIN**(Finish)

  - 연결 해제.
  - 세션 연결을 종료시킬 때 사용되며, 더 이상 전송할 데이터가 없음을 의미함.
  - 4way handshake에서 사용함.


### 3 Way-Handshake의 동작방식

3 Way-Handshake의 동작방식을 말로 풀어내면 다음과 같이 풀어낼 수 있음.

 
Step1 __[Client -> SYN -> Server]__ </br>
Client가 Server에게 접속을 요청하는 SYN플래그를 보냄.


Step2. __[Server -> SYN + ACK -> Client ]__ </br>
Server는 Listen상태에서 SYN이 들어온 것을 확인하고 SYN_RECV상태로 바뀌어 SYN + ACK플래그를 Client에게 전송함.  </br>
그 후 Server는 다시 ACK 플래그를 받기 위해 대기상태로 변경됨.


Step3. __[Client -> ACK -> Server]__ </br>
SYN + ACK 상태를 확인한 Client는 서버에게 ACK를 보내고 연결 성립(Established)이 됨. 


위와 같이 신뢰성을 위해 3번의 핸드쉐이킹을 거쳐 연결을 맺는것을 3 Way-Handshake라고 함.


