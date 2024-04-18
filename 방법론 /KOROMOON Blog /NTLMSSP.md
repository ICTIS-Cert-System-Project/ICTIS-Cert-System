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

## (3) Type 1 메시지

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/a4d661c8-fadb-4a80-9d48-69c91b86e633)

Type 1 메시지에는 클라이언트의 호스트 이름과 NT 도메인 이름이 들어 있음.
호스트와 도메인 문자열은 대문자로 ASCII 코드일 수 있음.
호스트 이름은 FQDN 이 아닌 호스트 이름임. (ex. KOROMOON 은 되고 KOROMOON.BLOGSPOT.KR 은 안 됨)
오프셋은 메시지 내의 특정 필드의 오프셋을 나타내며 길이는 지정된 필드의 길이임.

## (4) Type 2 메시지

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/1c09f54b-30ef-4351-88e1-8631e1492349)

Type 2 메시지에는 서버의 NTLM Challenge 가 들어 있음.
nonce 는 클라이언트가 LanManager 및 NT 응답을 생성하는데 사용되며 임의의 8바이트 배열임.
전체 메시지 길이는 항상 40 바이트임.

## (5) Type 3 메시지

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ebf8d8f9-8f55-4949-ad2c-68afeb053b05)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/dec738c1-75d8-42d4-86fa-79a587ae9e4c)

Type 3 메시지에는 사용자 이름, 호스트 이름, NT 도메인 이름 및 두 개의 응답이 들어 있음.
호스트, 도메인, 사용자 이름의 문자열은 유니 코드이며 끝이 아닌 문자임.
호스트 및 도메인 이름은 대문자임.
응답 문자열의 길이는 24 바이트임.

## (6) 암호 해시

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/eba92159-a82b-4df3-8547-1d1eac82bffa)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/290521d1-2e8c-4cb4-ad8d-c5c95b5dc3d8)

두 개의 응답 문자열을 계산하시 위해 두 가지 암호 해시가 사용됨.
(LanManager 암호 해시와 NT 암호 해시)
입력은 passw 와 nonce 이며 결과는 lm_resp 와 nt_resp 에 있음.

## (7) HTTP 에서의 NTLMSSP 인증 과정 예

아래 정보를 가지고 가정할 경우임.
호스트 이름 : "LightCity
NT 도메인 이름 : Ursa-Minor
사용자 이름 : Zaphod
암호 : Beeblebrox
서버 nonce : SrvNonce

인증 과정은 다음과 같음.

 C -> S   GET ...
    
    S -> C   401 Unauthorized
             WWW-Authenticate: NTLM
    
    C -> S   GET ...
             Authorization: NTLM TlRMTVNTUAABAAAAA7IAAAoACgApAAAACQAJACAAAABMSUdIVENJVFlVUlNBLU1JTk9S
    
    S -> C   401 Unauthorized
             WWW-Authenticate: NTLM TlRMTVNTUAACAAAAAAAAACgAAAABggAAU3J2Tm9uY2UAAAAAAAAAAA==
    
    C -> S   GET ...
             Authorization: NTLM TlRMTVNTUAADAAAAGAAYAHIAAAAYABgAigAAABQAFABAAAAADAAMAFQAAAASABIAYAAAAAAAAACiAAAAAYIAAFUAUgBTAEEALQBNAEkATgBPAFIAWgBhAHAAaABvAGQATABJAEcASABUAEMASQBUAFkArYfKbe/jRoW5xDxHeoxC1gBmfWiS5+iX4OAN4xBKG/IFPwfH3agtPEia6YnhsADT
    
    S -> C   200 Ok

인코딩되지 않은 메시지는 다음과 같음.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ecd21668-6e45-4bd7-96cf-186d1e20336c)

중간 해시 암호는 다음과 같음.
lm_hpw (LanManager hashed password):
91 90 16 f6 4e c7 b0 0b a2 35 02 8c a5 0c 7a 03 00 00 00 00 00
nt_hpw (NT hashed password):
8c 1b 59 e3 2e 66 6d ad f1 75 74 5f ad 62 c1 33 00 00 00 00 00


## (8) HTTP 에서의 NTLMSSP 인증 과정 5단계 패킷 덤프 및 시그니처

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/a036bada-0a5c-4533-be0c-d54c54f4c963)

인증 과정에서 5 단계는 Type 3 메시지를 클라이언트에서 서버 측으로 전송하며 중요한 정보가 들어 있음.
해당 단계를 탐지하는 Snort 룰은 아래와 같음. (위 화면에서 빨간 박스 탐지)
alert tcp any any -> any 80:8080 (msg:"KOROMOON_NTLMSSP_Type3_Message"; content"Authorization|3A| NTLM TlRMTVNTUAADAAA";)



### 참고 사이트 : </br>
https://en.wikipedia.org/wiki/NTLMSSP
https://msdn.microsoft.com/en-us/library/aa480475.aspx
https://www.innovation.ch/personal/ronald/ntlm.html
https://msdn.microsoft.com/en-us/library/cc237488.aspx
http://davenport.sourceforge.net/ntlm.html
http://horae.tistory.com/entry/NTLM-VS-Kerberos-%EC%9D%B8%EC%A6%9D
https://www.secpulse.com/archives/71555.html
http://blog.daum.net/mania1001/134
