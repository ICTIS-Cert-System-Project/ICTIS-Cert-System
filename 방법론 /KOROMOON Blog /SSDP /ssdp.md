# SSDP
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/ssdp.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 11일

## (1) SSDP

SSDP 란 Simple Service Discovery Protocol 의 약자로 네트워크 서비스나 정보를 찾기 위해서 사용하는 네트워크 프로토콜이며 SSDP 를 이용하면 DHCP 나 DNS 와 같은 네트워크 서버 혹은 정적인 호스트 설정 없이 이런 일들을 수행할 수 있음.
일반 거주와 소규모 사무 환경에서 UPnP(Universal Plug and Play) 를 위한 기본적인 프로토콜로 이미 널리 사용하고 있음. (SSDP 는 UPnP 표준에 포함됨)
HTTPU(UDP 기반의 HTTP) 를 이용하며 모든 데이터는 TEXT 로 통신함.
UDP 1900 포트를 사용하며 IP Multicast 주소를 이용함.
SSDP 는 Advertisement, Search 두 개의 타입이 있음.



## (2) UPnP

홈네트워크에 있는 네트워크 장치들이 서로 연동될 수 있도록 하는 범용 표준 프로토콜으로 특정 운영체제나 프로그래밍 언어, 미디어와 독립적으로 네트워크 상의 디바이스 간에 명령과 제어를 가능하게 함.
사용자가 직접 네트워크 설정, 유지 관리를 하지 않고도 쉽게 디바이스와 서비스의 연결성을 제공함.
IP, TCP, UDP, HTTP, XML 과 같은 기존의 프로토콜들을 사용함.
Wire 프로토콜에 기반을 두고 있으며 디바이스 간에 교환하는 데이터는 XML 로 표현되고 HTTP 를 통해서 통신함. IP 네트워킹을 채택한 이유는 다른 물리적 미디어로 확장이 용이하며 실제 복수 벤더 간의 상호 운용성을 가능함.
UPnP 를 통한 디바이스 간의 통신은 발견 단계, 기술 단계, 제어 단계, 이벤팅 단계, 프리젠테이션 단계로 나누어지며 SSDP 를 이용한 통신은 발견 단계에서 이용됨.
