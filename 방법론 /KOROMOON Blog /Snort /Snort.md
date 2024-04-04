# Snort 규칙 헤더 및 옵션 정보 _(Snort Rule Header & Option Information)_
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2020/10/snort-snort-rule-header-option.html "Go KOROMOON"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 3일 
</br>

## (1) 기본 사항
- Snort 는 유연하면서 강력한 그리고 간단한 규칙 기술 언어를 사용함.
- 대부분의 Snort 규칙은 한 줄로 작성됨.
- 1.8 버전 이상에서는 줄 끝 부분에 백슬래시(\)를 추가하여 규칙을 여러 줄로 확장할 수 있음.
- *규칙이 길지 않은 이상 가독성을 위해서 한 줄로 작성하는 걸 추천함.*
</br>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/5fcd3392-0a88-4e3a-bb37-7930e363348f) </br>
<Snort 규칙 구성 요소>

**Snort 규칙은 두 개의 논리적 섹션으로 나뉘는데 각각 규칙 헤더와 규칙 옵션임.** </br>
규칙 헤더에는 행위(Action), 프로토콜, 출발지 주소, 출발지 포트, 방향성, 목적지 주소, 목적지 포트가 포함됨. </br>
규칙 옵션에는 경고 메시지와 패킷의 어느 부분을 검사하여 규칙 행위을 수행해야 하는지 결정하는 정보가 들어 있음.

**규칙을 구성하는 모든 요소는 표시된 규칙 행위를 실행할 때 참(True)이어야 함.** </br>
**실행할 때 요소들은 논리적인 AND 문으로 형성하는 것으로 간주함.** </br>
**동시에 다양한 Snort 규칙 라이브러리 파일들은 논리적인 OR 문으로 구성하는 것으로 간주함.**

## (2) 규칙 헤더

### 2.1 규칙 행위

- 규칙 행위는 규칙 기준과 일치하는 패킷을 찾을 때 Snort 가 수행할 행위를 지시함.
- alert, log, pass 이 3가지 기본 동작이 있음.
- 인라인 모드에서 Snort 를 실행할 경우 drop, reject, sdrop 와 같은 추가 옵션이 있음.

</br>

|      분류      |                            설명                           |
|-----|----------|
|alert|선택한 alert 방법을 사용하여 경고를 생성한 다음 패킷을 기록함.|
|log| 패킷 기록 |
|pass| 패킷 무시 |
|drop| 패킷 차단 및 기록|
|reject| 패킷을 차단하고 기록한 다음 TCP 프로토콜이면 TCP Reset 플래그를 보내고 UDP 프로토콜이면 ICMP Port Unreachable 메시지를 보냄.|
|sdrop| 패킷을 차단하지만 기록하지 않음.|

### 2.2 프로토콜
- **현재 Snort 에서는 TCP, UDP, ICMP, IP 이렇게 4가지 프로토콜 분석 가능함. (규칙에 기재할 때 소문자로 기재할 것!)**
- 앞으로 다른 프로토콜이 추가할 수 있을 것으로 전망됨. (ex. ARP, IGRP, GRE, OSPF, RIP, IPX)

### 2.3 IP 주소
- IP 주소는 IP 와 CIDR 블록 형식으로 기재하며 any 키워드는 임의의 주소를 정의하는데 사용됨.
- 부정연산자 ! 를 사용할 경우 표시된 IP 주소 이외의 IP 주소만 적용됨. 
- 쉼표로 구분된 IP 주소 목록을 대괄호 기호로 이용하여 표시함.
- _참고로 Snort 는 IP 주소 필드에 대한 호스트 이름 조회를 제공하는 매커니즘이 없음._




<사용 예>

  
`alert tcp !192.168.1.0/24 any -> 192.168.1.0/24 111 (content:"|00 01 86 a5|"; msg:"external mountd access";)`


`alert tcp ![192.168.1.0/24,10.1.1.0/24] any -> [192.168.1.0/24,10.1.1.0/24] 111 (content:"|00 01 86 a5|"; msg:"external mountd access";)`


### 2.4 포트 번호
- 포트 번호는 포트, 범위연산자 :, 부정 연산자 ! 를 이용한 여러 가지 방법으로 지정함.
- any 키워드는 모든 포트를 의미하는 와일드카드 값임.

### 2.5 방향 연산자
- 일방향 연산자 -> 와 양방향 연산자 <> 를 사용함.
- **참고로 규칙 일관성을 위해서 <- 기호는 사용하지 않음.**


<사용 예>


`log udp any any -> 192.168.1.0/24 1:1024`


`log tcp any any -> 192.168.1.0/24 :6000`


`log tcp any :1024 -> 192.168.1.0/24 500:`


`log tcp any any -> 192.168.1.0/24 !6000:6010`


`log tcp !192.168.1.0/24 any <> 192.168.1.0/24 23`

## (3) 규칙 옵션
- 규칙 옵션은 Snort 침입 탐지 엔진의 핵심이며 편의성과 유연성을 결합함.
- **모든 Snort 규칙 옵션은 세미콜론 문자(;)를 사용하여 서로 구분함.**
- **규칙 옵션 키워드는 콜론 문자(:)를 사용하여 인수와 구분함.**

</br>

- 규칙 옵션에는 아래 4 가지 주요 범주가 있음.

|      분류      |                            설명                           |
|--------------|---------------------------------------------------------|
| **General**        | **규칙에 대한 정보를 제공하지만 탐지 중에 영향을 주지 않음.** |
| **Payload**        | **패킷 페이로드의 내부 데이터를 찾고 상호 관련됨.**           |
| **Non-Payload**    | **페이로드가 아닌 데이터를 찾음.**                            |
| **Post-Detection** | **규칙이 실행된 후에 발생하는 규칙 관련 트리거임.**           |

## (4) General 규칙 옵션
### 4.1 msg
- msg 키워드는 로깅 및 경고 엔진에 패킷 덤프 또는 경고와 함께 인쇄할 메시지를 알려줌.
</br>

<형식>


`msg:"<message text>";`

### 4.2 reference
- reference 키워드를 사용하면 규칙에 대해서 외부 공격 식별 시스템에 대한 참조를 포함할 수 있음.
- 플러그인은 고유 URL 뿐만 아니라 여러 특정 시스템을 지원함.
</br>

<형식>


`reference:<id system>, <id>; [reference:<id system>, <id>;]`


<사용 예>


`alert tcp any any -> any 7070 (msg:"IDS411/dos-realaudio"; flags:AP; content:"|fff4 fffd 06|"; reference:arachnids,IDS411;)`
</br>
`alert tcp any any -> any 21 (msg:"IDS287/ftp-wuftp260-venglin-linux"; flags:AP; content:"|31c031db 31c9b046 cd80 31c031db|"; reference:arachnids,IDS287; reference:bugtraq,1387; reference:cve,CAN-2000-1574;)`

</br>

<지원 시스템>
|   System  |                       URL Prefix                      |
|---------|-----------------------------------------------------|
| bugtraq   | http://www.securityfocus.com/bid/                     |
| cve       | http://cve.mitre.org/cgi-bin/cvename.cgi?name=        |
| nessus    | http://cgi.nessus.org/plugins/dump.php3?id=           |
| arachnids | (currently down) http://www.whitehats.com/info/IDS    |
| mcafee    | http://vil.nai.com/vil/content/v_                     |
| osvdb     | http://osvdb.org/show/osvdb/                          |
| msb       | http://technet.microsoft.com/en-us/security/bulletin/ |
| url       | http://                                               |

### 4.3 gid
- gid 키워드(generator id)는 특정 규칙이 발생할 때 Snort 가 어떤 이벤트를 생성하는 지 식별하는데 사용됨.
- 현재 사용 중인 gid 에 대해서는 /etc/generators 파일을 참조 바람.
- gid 키워드는 선택사항이며 규칙에 지정되지 않은 경우 기본값은 1 이며 규칙은 일반 규칙 하위시스템의 일부가 됨.
- Snort 에 정의된 gid 와 잠재적인 충돌을 피하기 위해서 1,000,000 부터 사용하는 것이 좋음.
- 일반적인 규칙 작성할 경우, gid 키워드를 사용할 것!
- 이 옵션은 sid 키워드와 함께 사용해야 함.
- etc/gen-msg.map 파일에 Preprocessor 및 Decoder gid 에 대한 자세한 정보가 들어 있음.

</br>

<형식>


`gid:<generator id>;`

</br>


<사용 예>


`alert tcp any any -> any 80 (content:"KOROMOON"; gid:1000001; sid:1; rev:1;)`

### 4.4 sid
- sid 키워드는 Snort 규칙을 고유하게 식별하는 데 사용됨.
- 이 정보는 출력 플러그인이 규칙을 쉽게 식별할 수 있게 함.
- 이 옵션은 rev 키워드와 함께 사용해야 함.

|      분류      |                            설명                           |
|--------------|---------------------------------------------------------|
|<100|향후 사용을 위해 예약됨|
|100~999,999|Snort 배포판에 포함된 규칙|
|>=1,000,000|사용자가 정의한 규칙|

</br>

- sid-msg.map 파일에는 Snort 규칙 ID 에 대한 경고 메시지 매핑이 들어 있음.
- 이 정보는 경고를 사후 처리하여 ID 를 경고 메시지에 매핑할 때 유용함.

