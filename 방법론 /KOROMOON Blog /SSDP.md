# SSDP
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/ssdp.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 11일

## (1) SSDP

- SSDP 란 Simple Service Discovery Protocol 의 약자로 네트워크 서비스나 정보를 찾기 위해서 사용하는 네트워크 프로토콜이며 SSDP 를 이용하면 DHCP 나 DNS 와 같은 네트워크 서버 혹은 정적인 호스트 설정 없이 이런 일들을 수행할 수 있음.
- 일반 거주와 소규모 사무 환경에서 UPnP(Universal Plug and Play) 를 위한 기본적인 프로토콜로 이미 널리 사용하고 있음. (SSDP 는 UPnP 표준에 포함됨)
- HTTPU(UDP 기반의 HTTP) 를 이용하며 모든 데이터는 TEXT 로 통신함.
- UDP 1900 포트를 사용하며 IP Multicast 주소를 이용함.
- SSDP 는 Advertisement, Search 두 개의 타입이 있음.



## (2) UPnP

- 홈네트워크에 있는 네트워크 장치들이 서로 연동될 수 있도록 하는 범용 표준 프로토콜으로 특정 운영체제나 프로그래밍 언어, 미디어와 독립적으로 네트워크 상의 디바이스 간에 명령과 제어를 가능하게 함.
- 사용자가 직접 네트워크 설정, 유지 관리를 하지 않고도 쉽게 디바이스와 서비스의 연결성을 제공함.
- IP, TCP, UDP, HTTP, XML 과 같은 기존의 프로토콜들을 사용함.
- Wire 프로토콜에 기반을 두고 있으며 디바이스 간에 교환하는 데이터는 XML 로 표현되고 HTTP 를 통해서 통신함.
- IP 네트워킹을 채택한 이유는 다른 물리적 미디어로 확장이 용이하며 실제 복수 벤더 간의 상호 운용성을 가능함.
- UPnP 를 통한 디바이스 간의 통신은 발견 단계, 기술 단계, 제어 단계, 이벤팅 단계, 프리젠테이션 단계로 나누어지며 SSDP 를 이용한 통신은 발견 단계에서 이용됨.

<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; UPnP 프로토콜 스택의 구조 &gt;</span></div>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/03473286-3203-4633-8c3b-22c37e19d69a)


## (3) SSDP 에서 사용하는 멀티캐스트 주소

IPv4 239.255.255.250  site-local 주소 </br>
IPv6 FF02::C   link-local 주소 </br>
IPv6 FF05::C   site-local 주소 </br>
IPv6 FF08::C   organization-local 주소 </br>
IPv6 FF0E::C   global 주소



## (4) SSDP Header

- SSDP 는 HTTP 1.1 의 Generic Message 를 준수한 Header Field Format 부분을 이용하여 정의되며 TCP 대신에 UDP 를 사용함.(HTTPU)
- Message Body 는 사용하지 않지만 만약에 Message Body 가 수신된다면 이를 무시할 수 있도록 정의함.
- 각각의 SSDP Message 는 하나의 시작줄(Start-LINE, 첫번째 줄)을 갖어야 하며 적어도 다음의 3 가지 중 하나이어야 함. (공통적으로 "HTTP/1.1" 을 포함하여야 하는 것을 알 수 있으며 HTTP 1.1 하위 버전과의 호환성을 유지해야 함)

NOTIFY * HTTP/1.1 </br>
M-SEARCH * HTTP/1.1 </br>
HTTP/1.1 200 OK

## (5) Advertisement 타입

- UPnP 를 지원하는 디바이스에서 자신의 디바이스와 서비스를 Advertising(광고)하기 위한 Discovery Message 를 멀티캐스트 방식으로 전달하는 타입임.
- 전송 시 Default TTL 값은 4이고 설정 가능할 수 있어야 함.
- NOTIFY 메소드를 사용하며 전송 형식은 다음과 같음.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">NOTIFY *
  HTTP/1.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Advertisement </span>타입의 요청 메소드<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">Host:239.255.255.250:1900&nbsp;&nbsp; // </span>멀티캐스트
  주소 및 포트<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: Courier New, Courier, monospace;">NT:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Notification Type<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: Courier New, Courier, monospace;">NTS:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Notification Sub
  Type (ssdp:alive / ssdp:byebye)<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">Location:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;// Device </span>에 관한 정보를 담고 있는<span lang="EN-US"> URL<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: Courier New, Courier, monospace;">USN:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Unique Service
  Name<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">Cache-Control:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // max-age </span>를 사용하며<span lang="EN-US"> Advertisement </span>가 유효한 시간<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">Server:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // UPnP </span>정보<span lang="EN-US">, OS </span>정보 등<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">BODY:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // </span>없음</span></div>
</td>
 </tr>
</tbody></table>
<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; NOTIFY 전송 형식 &gt;</span></div>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ae4b117e-709b-49f6-9e9c-1129c662ecce)
<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; NOTIFY 전송 패킷 &gt;</span></div>

- NT 필드와 USN 필드는 각 경우에 따라서 아래와 같이 전송하는 방식이 다름.

① root device 에 대하여 3개 전송

NT: upnp:rootdevice
USN: uuid:device-uuid::upnp:rootdevice (device-uuid 부분에 해당 device 에 유일한 uuid 값이 들어감)

NT: uuid:device-uuid (device-uuid 부분에 해당 device 에 유일한 uuid 값이 들어감)
USN: uuid:device-uuid (device-uuid 부분에 해당 device 에 유일한 uuid 값이 들어감)

NT: urn:schemas-upnp-org:device:devicetype:v (devicetype 과 v 에 UPnP Forum 에서 정의한 값이 들어감. e.g MediaServer:1)
USN: uuid:device-uuid::urn:schemas-upnp-org:device:devicetype:v (device-uuid 부분에 해당 device 에 유일한 uuid 값이 들어감. devicetype 과 v 에 UPnP Forum 에서 정의한 값이 들어감. e.g MediaServer:1)

② device 내의 각 servicetype 에 대하여 한번씩 전송

NT: urn:schemas-upnp-org:service:servicetype:v(servicetype 과 v 에는 UPnP Forum 에서 정의한 service type 값이 들어감. e.g ConnectionManager:1)
USN: uuid:device-UUID::urn:schemas-upnp-org:service:serviceTtpe:v

- 지원서비스가 2개라면 총 한 세트에  5번을 보내는 것임.
- 위의 NT 나 USN 에 포함된 device-uuid 에 해당하는 값은 device description 내의 UDN 값과 동일하여야 함.

- 참고로 Device 가 네트워크에서 제거될때 취소 Message 를 전송함.
- Device의 IP 주소가 변경되었을 때에도 이전 Advertisement 를 취소하고 새로운 IP 주소를 가지고 다시 Advertising 해야 함.
- NTS 필드 값에 ssdp:byebye 를 넣어 멀티캐스트 방식으로 전송함.

NOTIFY * HTTP/1.1 </br>
HOST: 239.255.255.250:1900 </br>
NT: Notifycation Type </br>
NTS: ssdp:byebye </br>
USN: uuid:advertisement UUID

## (6) Search 타입

- Control Point 에서 직접 관심있는 Device 나 Service 의 검색을 하게 하기 위한 Search Message 를 멀티캐스트 방식으로 전달하는 타입임.
- Search 요청은 UDP 멀티캐스트 방식으로 전달되고 Search 응답은 UDP 유니캐스트 방식으로 받음.
- Search 요청은 M-SEARCH 메소드를 사용하며 전송 형식은 다음과 같음.


<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; Search 요청 형식 &gt;</span></div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">M-SEARCH *
  HTTP/1.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Search </span>타입의 요청 메소드<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">Host:239.255.255.250:1900&nbsp;&nbsp; // </span>멀티캐스트
  주소 및 포트<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">ST:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // </span>검색 대상<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">MAN:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // HTTP Extension
  Framework </span>에 의해 필수 사항으로<span lang="EN-US">
  "ssdp:discover" </span>값 사용<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">MX:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Device </span>응답 최대 대기 시간<span lang="EN-US"> (0 ~ 120)</span></span></div>
</td>
 </tr>
</tbody></table>

<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; Search 요청 패킷 &gt;</span></div>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/9d6d6a32-d14e-432b-acb0-dd0072b50fcc)

- 다음은 Search 응답 형식임.

<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; Search 응답 형식 &gt;</span></div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">HTTP/1.1 200
  OK&nbsp;&nbsp; // Search </span>타입의 응답 값<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">CACHE-CONTROL:&nbsp;&nbsp;&nbsp; // </span>호스트와
  통신 유효 시간으로<span lang="EN-US"> max-age </span>지시어 포함<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">DATE:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // </span>응답이 전달된 시간<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">EXT:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // HTTP Extension Framework </span>에 의해 필수 사항으로 값은 없음<span lang="EN-US">.<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">LOCATION:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // </span>서비스에 대한 설명이 지정된<span lang="EN-US"> URL<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">SERVER:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // UPnP </span>정보<span lang="EN-US">, OS </span>정보 등<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">ST:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // </span>검색 대상<span lang="EN-US"> (Request ST </span>에 따라 전달할 응답도
  달라짐<span lang="EN-US">)<o:p></o:p></span></span></div>
<div class="MsoNoSpacing">
<span style="font-family: Courier New, Courier, monospace;"><span lang="EN-US">USN:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Unique Service Name (NOTIFY </span>전송시의<span lang="EN-US"> USN </span>과 동일한 값으로<span lang="EN-US"> ST</span>와 쌍으로 전송<span lang="EN-US">)</span></span></div>
</td>
 </tr>
</tbody></table>

<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;">&lt; Search 응답 패킷 &gt;</span></div>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/007b1347-8fe5-4d20-9472-3d41cdfe1f64)

- Search 응답 ST 필드에 대해서 좀 더 살펴보자.
- Request ST 이 "ssdp:all" 일때 ST 를 "upnp:rootdevice", "uuid:device-uuid", "urn:schemas-upnp-org:device:devicetype:v"와 "urn:schemas-upnp-org:service:servicetype:v" 를 서비스당 하나씩 하여 해당 갯 수만큼 응답을 전송해야 함.
- Request ST 이 "upnp:rootdevice" 일때 ST 값을 "upnp:rootdevice" 로 하여 한번 응답함.
- Request ST 이 "uuid:device-uuid" 일때 device-uuid 와 일치하는 device 이면 ST 값을 uuid:device-uuid 로 동일하게 하여 한번 응답함.
- Request ST 이 "urn:schemas-upnp-org:device:devicetype:v" 일때 일치하는 devicetype 과 같은 버전이면 ST 값을 동일하게 하여 한번 응답함.
- Request ST 이 "urn:schemas-upnp-org:service:servicetype:v" 이면 일치하는 servicetype 과 같은 버전이면 ST 값을 동일하게 하여 한번 응답함.

## (7) UUID

- UUID (Universally Unique Identifier) 는 기기를 식별하기 위한 유일한 값을 뜻함.
- UUID 는 128 비트 크기를 가지며 형식은 아래와 같음.

<div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: Courier New, Courier, monospace;">UUID =
  4*&lt;hexOctet&gt; "-" 2*&lt;hexOctet&gt; "-"
  2*&lt;hexOctet&gt; "-" 2*&lt;hexOctet&gt; "-" 6*&lt;hexOctet&gt;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>
</div>

UUID 조건
1. 중복 X
2. 128 비트 크기
3. 변경할 수 없는 고정 값
