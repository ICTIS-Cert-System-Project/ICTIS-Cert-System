# NTLMSSP
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/05/ntlmssp.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 12일 


## (1) NTLMSSP

NTLMSSP 란 NT LAN Manager(NTLM) Security Support Provider 의 약자로 NTLM 챌린지(Challenge) 및 응답 인증을 용이하게 하고 무결성 및 기밀 옵션을 협상하기 위해 SSPI(Microsoft Security Support Provider) 에서 사용하는 바이너리 메시징 프로토콜임. </br>
서버 메시지 블록/CIFS 확장 보안 인증, HTTP 협상 인증(ex. IWA 가 설정된 IIS), MSRPC 서비스를 비롯하여 SSPI 인증이 사용되는 모든 곳에서 사용됨.

## (2) HTTP 에서의 NTLMSSP 인증 과정

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/cab01000-c935-4b78-a992-19da8af124ae)

이진 구조로 된 3 가지 Type 메시지를 기반으로 인증 과정을 거침.
각각의 메시지 구조는 pseudo-C 구조체와 메모리 레이아웃 다이어그램 형식으로 아래와 같이 설명됨. (참고 사항 !!! byte - 8비트, short - 16 비트, 리틀 엔디안 순서로 저장, 배열 길이 * 는 가변 길이 필드를 나타냄, 구조체의 주석에 있는 16 진수 및 인용된 문자는 주어진 필드의 고정값을 나타냄)

4 단계와 5 단계 사이에 네트워크 연결이 유지되어야 하며 그렇지 않을 경우 3 단계 ~ 6 단계을 다시 연결이 될 경우까지 반복적으로 거침.
일단, 연결이 인증되면 연결이 유지되는 동안 Authorization 헤더를 더 이상 전송하지 않아도 됨.
