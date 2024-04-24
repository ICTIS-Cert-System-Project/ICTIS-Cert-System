# Snort 규칙 헤더 및 옵션 정보 _(Snort Rule Header & Option Information)_
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2020/10/snort-snort-rule-header-option.html "Go KOROMOON"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 3일 
</br>

## (1) 기본 사항
Snort 는 유연하면서 강력한 그리고 간단한 규칙 기술 언어를 사용함.
대부분의 Snort 규칙은 한 줄로 작성됨.
1.8 버전 이상에서는 줄 끝 부분에 백슬래시(\\)를 추가하여 규칙을 여러 줄로 확장할 수 있음.
*규칙이 길지 않은 이상 가독성을 위해서 한 줄로 작성하는 걸 추천함.*
</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
Snort </span>규칙 구성 요소<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/efbcc7de-7cb7-49f8-a3ca-90aa0c2a3909)

</br>


**Snort 규칙은 두 개의 논리적 섹션으로 나뉘는데 각각 규칙 헤더와 규칙 옵션임.** </br>
규칙 헤더에는 행위(Action), 프로토콜, 출발지 주소, 출발지 포트, 방향성, 목적지 주소, 목적지 포트가 포함됨. </br>
규칙 옵션에는 경고 메시지와 패킷의 어느 부분을 검사하여 규칙 행위을 수행해야 하는지 결정하는 정보가 들어 있음.

**규칙을 구성하는 모든 요소는 표시된 규칙 행위를 실행할 때 참(True)이어야 함.** </br>
**실행할 때 요소들은 논리적인 AND 문으로 형성하는 것으로 간주함.** </br>
**동시에 다양한 Snort 규칙 라이브러리 파일들은 논리적인 OR 문으로 구성하는 것으로 간주함.**

## (2) 규칙 헤더

### 2.1 규칙 행위

규칙 행위는 규칙 기준과 일치하는 패킷을 찾을 때 Snort 가 수행할 행위를 지시함.
alert, log, pass 이 3가지 기본 동작이 있음.
인라인 모드에서 Snort 를 실행할 경우 drop, reject, sdrop 와 같은 추가 옵션이 있음.

</br>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">분류<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">alert<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">선택한<span lang="EN-US"> alert </span>방법을 사용하여
  경고를 생성한 다음 패킷을 기록함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">log<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷 기록<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">pass<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷 무시<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">drop<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷 차단 및 기록<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">reject<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷을 차단하고 기록한 다음<span lang="EN-US"> TCP </span>프로토콜이면<span lang="EN-US"> TCP Reset </span>플래그를 보내고<span lang="EN-US"> UDP </span>프로토콜이면<span lang="EN-US"> ICMP Port Unreachable </span>메시지를 보냄<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sdrop<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷을 차단하지만 기록하지 않음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 2.2 프로토콜
**현재 Snort 에서는 TCP, UDP, ICMP, IP 이렇게 4가지 프로토콜 분석 가능함. (규칙에 기재할 때 소문자로 기재할 것!)**
앞으로 다른 프로토콜이 추가할 수 있을 것으로 전망됨. (ex. ARP, IGRP, GRE, OSPF, RIP, IPX)

### 2.3 IP 주소
IP 주소는 IP 와 CIDR 블록 형식으로 기재하며 any 키워드는 임의의 주소를 정의하는데 사용됨.
부정연산자 ! 를 사용할 경우 표시된 IP 주소 이외의 IP 주소만 적용됨. 
쉼표로 구분된 IP 주소 목록을 대괄호 기호로 이용하여 표시함.
_참고로 Snort 는 IP 주소 필드에 대한 호스트 이름 조회를 제공하는 매커니즘이 없음._




<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert tcp !192.168.1.0/24 any -&gt; 192.168.1.0/24 111
  (content:"|00 01 86 a5|"; msg:"external mountd access";)<o:p></o:p></span></span></i></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert tcp ![192.168.1.0/24,10.1.1.0/24] any -&gt;
  [192.168.1.0/24,10.1.1.0/24] 111 (content:"|00 01 86 a5|";
  msg:"external mountd access";)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 2.4 포트 번호
포트 번호는 포트, 범위연산자 :, 부정 연산자 ! 를 이용한 여러 가지 방법으로 지정함.
any 키워드는 모든 포트를 의미하는 와일드카드 값임.

### 2.5 방향 연산자
일방향 연산자 -> 와 양방향 연산자 <> 를 사용함.
**참고로 규칙 일관성을 위해서 <- 기호는 사용하지 않음.**


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log udp any any -&gt; 192.168.1.0/24 1:1024<o:p></o:p></span></span></i></p>
  <p align="left" class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log tcp any any -&gt; 192.168.1.0/24 :6000<o:p></o:p></span></span></i></p>
  <p align="left" class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log tcp any :1024 -&gt; 192.168.1.0/24 500:<o:p></o:p></span></span></i></p>
  <p align="left" class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log tcp any any -&gt; 192.168.1.0/24 !6000:6010<o:p></o:p></span></span></i></p>
  <p align="left" class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log tcp !192.168.1.0/24 any &lt;&gt; 192.168.1.0/24 23<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


## (3) 규칙 옵션
규칙 옵션은 Snort 침입 탐지 엔진의 핵심이며 편의성과 유연성을 결합함.
**모든 Snort 규칙 옵션은 세미콜론 문자(;)를 사용하여 서로 구분함.**
**규칙 옵션 키워드는 콜론 문자(:)를 사용하여 인수와 구분함.**

</br>

규칙 옵션에는 아래 4 가지 주요 범주가 있음.

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">분류<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US" style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">General<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">규칙에 대한 정보를 제공하지만 탐지 중에 영향을 주지 않음<span lang="EN-US">.<o:p></o:p></span></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US" style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">Payload<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">패킷 페이로드의 내부 데이터를 찾고 상호 관련됨<span lang="EN-US">.<o:p></o:p></span></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US" style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">Non-Payload<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">페이로드가 아닌 데이터를 찾음<span lang="EN-US">.<o:p></o:p></span></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US" style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">Post-Detection<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="color: red; mso-fareast-font-family: &quot;맑은 고딕&quot;; mso-fareast-theme-font: minor-latin;"><span style="font-family: courier;">규칙이 실행된 후에 발생하는 규칙 관련 트리거임<span lang="EN-US">.<o:p></o:p></span></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


## (4) General 규칙 옵션
### 4.1 msg
msg 키워드는 로깅 및 경고 엔진에 패킷 덤프 또는 경고와 함께 인쇄할 메시지를 알려줌.
</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">msg:"&lt;message text&gt;";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.2 reference
reference 키워드를 사용하면 규칙에 대해서 외부 공격 식별 시스템에 대한 참조를 포함할 수 있음.
플러그인은 고유 URL 뿐만 아니라 여러 특정 시스템을 지원함.
</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">reference:&lt;id system&gt;, &lt;id&gt;;
  [reference:&lt;id system&gt;, &lt;id&gt;;]<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 7070 (msg:"IDS411/dos-realaudio"; flags:AP;
  content:"|fff4 fffd 06|"; reference:arachnids,IDS411;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 21 (msg:"IDS287/ftp-wuftp260-venglin-linux";
  flags:AP; content:"|31c031db 31c9b046 cd80 31c031db|";
  reference:arachnids,IDS287; reference:bugtraq,1387;
  reference:cve,CAN-2000-1574;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>지원 시스템<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">System<o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">URL Prefix<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bugtraq<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://www.securityfocus.com/bid/<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">cve<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://cve.mitre.org/cgi-bin/cvename.cgi?name=<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">nessus<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://cgi.nessus.org/plugins/dump.php3?id=<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">arachnids<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">(currently down) http://www.whitehats.com/info/IDS<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">mcafee<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://vil.nai.com/vil/content/v_<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">osvdb<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://osvdb.org/show/osvdb/<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">msb<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://technet.microsoft.com/en-us/security/bulletin/<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">url<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http://<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.3 gid
gid 키워드(generator id)는 특정 규칙이 발생할 때 Snort 가 어떤 이벤트를 생성하는 지 식별하는데 사용됨.
현재 사용 중인 gid 에 대해서는 /etc/generators 파일을 참조 바람.
gid 키워드는 선택사항이며 규칙에 지정되지 않은 경우 기본값은 1 이며 규칙은 일반 규칙 하위시스템의 일부가 됨.
Snort 에 정의된 gid 와 잠재적인 충돌을 피하기 위해서 1,000,000 부터 사용하는 것이 좋음.
일반적인 규칙 작성할 경우, gid 키워드를 사용할 것!
이 옵션은 sid 키워드와 함께 사용해야 함.
etc/gen-msg.map 파일에 Preprocessor 및 Decoder gid 에 대한 자세한 정보가 들어 있음.

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">gid:&lt;generator id&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (content:"KOROMOON"; gid:1000001; sid:1;
  rev:1;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.4 sid
sid 키워드는 Snort 규칙을 고유하게 식별하는 데 사용됨.
이 정보는 출력 플러그인이 규칙을 쉽게 식별할 수 있게 함.
이 옵션은 rev 키워드와 함께 사용해야 함.

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">분류<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">&lt;100<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">향후 사용을 위해 예약됨<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">100~999,999<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">Snort </span>배포판에 포함된 규칙<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">&gt;=1,000,000<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">사용자가 정의한 규칙<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

sid-msg.map 파일에는 Snort 규칙 ID 에 대한 경고 메시지 매핑이 들어 있음.
이 정보는 경고를 사후 처리하여 ID 를 경고 메시지에 매핑할 때 유용함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sid:&lt;snort rules id&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; an 80 (content:"KOROMOON"; sid:1000983; rev:1;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.5 rev
rev 키워드는 Snort 규칙의 수정 버전을 고유하게 식별하는 데 사용됨.
Snort 규칙 ID 와 함께 개정이 허용되며 서명 및 설명을 수정하여 업데이트 된 정보를 대체할 수 있음.
이 옵션은 sid 키워드와 함께 사용해야 함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rev:&lt;revision integer&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (content:"KOROMOON"; sid:1000983; rev:1;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.6 classtype

classtype 키워드는 규칙에 대한 공격 범주화하는데 사용함.
Snort 는 기본적으로 제공하는 규칙에 대해서 공격 범주를 제공함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">classtype:&lt;class name&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 25 (msg:"SMTP expn root"; flags:A+;
  content:"expn root"; nocase; classtype:attempted-recon;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

Snort 가 정의한 공격 범주 분류는 classification.config 파일에 있음.
이 파일은 다음과 같은 구문을 사용함.
config classification: \<class name>,\<class description>,\<default priority>

이러한 공격 범주 분류는 아래 표에 나열되어 있음.
현재 4 가지 기본 우선 순위로 기재하였으며 1(높음) 은 가장 심각하고 4(매우 낮음) 는 가장 덜 심각함.

</br>

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">Classtype<o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">우선순위<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm; mso-pagination: widow-orphan; text-autospace: ideograph-numeric ideograph-other; word-break: keep-all;"><span lang="EN-US"><span style="font-family: courier;">attempted-admin <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">관리자 권한 획득 시도<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">attempted-user <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">사용자 권한 획득 시도<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">inappropriate-content<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">부적절한 컨텐츠 감지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">policy-violation <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">잠재적인 개인 정보 침해<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">shellcode-detect <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">실행 코드 감지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">successful-admin <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">관리자 권한 획득 성공<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">successful-user <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">사용자 권한 획득 성공<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">trojan-activity <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">네트워크 트로이목마 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">unsuccessful-user <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">사용자 권한 획득 실패<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">web-application-attack <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">웹 응용 프로그램 공격<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">high<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">attempted-dos <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">DoS </span>시도<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">attempted-recon <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">정보 유출 시도<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">bad-unknown <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">잠재적인 나쁜 트래픽<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">default-login-attempt <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">기본 사용자 이름과 암호로 로그인 시도<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">denial-of-service <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">DoS </span>탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">misc-attack <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">기타 공격<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">non-standard-protocol <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">비표준 프로토콜 또는 이벤트 감지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">rpc-portmap-decode <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">RPC </span>쿼리 디코드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">successful-dos <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">DoS<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">successful-recon-largescale <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">대규모 정보 유출<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">successful-recon-limited <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">정보 유출<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">suspicious-filename-detect <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">의심스러운 파일 이름 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">suspicious-login <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">의심스러운 사용자 이름을 사용하여 로그인 시도 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">system-call-detect <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">시스템 호출 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">unusual-client-port-connection<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">클라이언트가 비정상적인 포트 사용<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">web-application-activity <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">잠재적으로 취약한 웹 응용 프로그램에 대한 액세스<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">medium<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">icmp-event <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">일반적인<span lang="EN-US"> ICMP </span>이벤트<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">misc-activity <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">기타 활동<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">network-scan<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">네트워크 스캔 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">not-suspicious <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">의심스러운 트래픽 아님<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">protocol-command-decode <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">일반 프로토콜 명령어 디코드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">string-detect <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">의심스러운 문자열 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">unknown <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">알 수 없는 트래픽<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">low<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 118.8pt;" width="158">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">tcp-connection <o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">TCP </span>연결 탐지<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 58.9pt;" width="79">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">very low<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>
</br>

- classtype 옵션은 구성 분류 옵션(config classification option)을 이용한 snort.conf 에 정의된 분류만 사용할 수 있음.
- Snort 는 classification.config 파일에서 제공하는 규칙에 따라 사용되는 기본 분류 집합을 제공함.


### 4.7 priority
- priority 키워드는 규칙에 심각도 레벨을 지정함.
- classtype 키워드는 구성 분류 옵션(config classification option)에 의해 정의된 기본적인 우선순위를 할당함.
- 각 경우의 예는 아래와 같음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">priority:&lt;priority integer&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"WEB-MISC phf attempt"; flags:A+;
  content:"/cgi-bin/phf"; priority:10;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"EXPLOIT ntpdx overflow";
  dsize:&gt;128; classtype:attempted-admin; priority:10 );<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 4.8 metadata
- metadata 키워드를 사용하면 규칙 작성자가 규칙에 대한 추가 정보를 일반적으로 키-값 형식으로 포함시킬 수 잇음.
- 특정 메타데이터 키와 값은 Snort 에 의미가 있으며 아래 표에 나열되어 있음.

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">&lt;
Snort Metadata Keys &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">키<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 87.25pt;" width="116">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">값 형식<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">engine<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNoSpacing"><span style="font-family: courier;">공유 라이브러리 규칙 표시<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 87.25pt;" width="116">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">"shared"<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">soid<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNoSpacing"><span style="font-family: courier;">공유 라이브러리 규칙 생성기 및<span lang="EN-US"> SID<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 87.25pt;" width="116">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">gid|sid<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">service<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 10cm;" width="378">
  <p class="MsoNoSpacing"><span style="font-family: courier;">목표 기반 서비스 식별자<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">(service </span>메타데이터 키는 호스트 속성 테이블이 제공될 때만 의미가 있음<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 87.25pt;" width="116">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">"http"<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

- 표에 나열된 것 이외의 키는 Snort 에서 효과적으로 무시되며 키와 값을 사용하여 자유 형식이 될 수 있음.
- 여러 키는 쉼표로 구분되며 키와 값은 공백으로 구분됨.
</br>
<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">metadata:key1 value1;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">metadata:key1 value1, key2 value2;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

아래 예제는 공유 라이브러리 규칙에서 스텁(stub) 규칙을 보여줌.
첫 번째 예제는 여러 metadata 키워드를 사용하고 두 번째 예제는 단일 metadata 키워드를 사용하며 키는 쉼표로 구분됨.

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"Shared Library Rule Example";
  metadata:engine shared; metadata:soid 3|12345;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"Shared Library Rule Example";
  metadata:engine shared, soid 3|12345;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"HTTP Service Rule Example";
  metadata:service http;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>





### 4.9 General Rule Quick Reference
<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
General </span>규칙 옵션 키워드 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">키워드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">msg<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">msg </span>키워드는 로깅 및 경고 엔진에 패킷 덤프 또는 경고와 함께 인쇄할
  메시지를 알려줌<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">reference<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">reference </span>키워드를 사용하면 규칙에 대해서 외부 공격 식별 시스템에 대한
  참조를 포함할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">gid<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">gid </span>키워드<span lang="EN-US">(generator
  id)</span>는 특정 규칙이 발생할 때<span lang="EN-US"> Snort </span>가 어떤 이벤트를 생성하는 지 식별하는데
  사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">sid<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">sid </span>키워드는<span lang="EN-US"> Snort </span>규칙을
  고유하게 식별하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">rev<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">rev </span>키워드는<span lang="EN-US"> Snort </span>규칙의
  수정 버전을 고유하게 식별하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">classtype<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">classtype </span>키워드는 규칙에 대한 공격 범주화하는데 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">priority<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">priority </span>키워드는 규칙에 심각도 레벨을 지정함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">metadata<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">metadata </span>키워드를 사용하면 규칙 작성자가 규칙에 대한 추가 정보를 일반적으로
  키<span lang="EN-US">-</span>값 형식으로 포함시킬 수 잇음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

## (5) Payload 감지 규칙 옵션
### 5.1 content
content 키워드는 Snort 의 중요한 기능 중 하나임. </br>
이를 통해 사용자는 패킷 페이로드의 특정 컨텐츠를 검색하고 해당 데이터를 기반으로 응답을 트리거하는 규칙을 설정할 수 있음. </br>
content 옵션 패턴 매치가 수행될 때마다 Boyer-Moore 패턴 매치 함수가 호출되고 패킷 내용에 대해 테스트가 수행됨.  </br>
인수 데이터 문자열과 정확히 일치하는 데이터가 패킷 페이로드의 모든 위치에 포함되어 있으면 테스트가 성공하고 나머지 규칙 옵션 테스트가 수행됨. </br>
이 테스트는 대소문자를 구분함.

</br>

content 키워드에 대한 옵션 데이터는 다소 복잡함. 혼합 텍스트 및 바이너리 데이터를 포함할 수 있음. </br>
바이너리 데이터는 일반적으로 파이프(|) 문자로 묶여 있으며 바이트 코드로 표시됨. </br>
바이트 코드는 16진수로 바이너리 데이터를 나타내고 복잡한 바이너리 데이터를 설명하기 위한 좋은 축약 방법임.  </br>
아래 예제는 Snort 규칙에서 혼합 텍스트와 바이너리 데이터의 사용을 보여줌.

</br>

하나의 규칙에 여러 content 규칙을 지정할 수 있음. </br>
따라서 규칙을 잘못 판정하지 않도록 조정할 수 있음.

</br>

규칙 앞에 ! 문자열이 있을 경우 content 가 포함되지 않은 패킷에 대해 경고를 트리거됨. </br>
이는 특정 패턴과 일치하지 않는 패킷에 대해 경고를 보내려는 규칙을 작성할 때 유용함.

</br>

참고로 다음 문자는 contnet 규칙 내에서 이스케이프 처리해야 함. </br>
;\”

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">content:[!]"&lt;content
  string&gt;";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 139 (content:"|5c 00|P|00|I|00|P|00|E|00
  5c|";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (content:!"GET";)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


</br>


! 수정자(modifier)는 해당 수정자가 포함된 전체 내용 검색 결과를 무효화함. </br>
예를 들어 content:!"A"; within:50; 규칙일 경우 페이로드가 5바이트 뿐이며 해당 5 바이트에 “A” 가 없으면 결과는 일치로 리턴함. </br>
유효한 일치를 위해 50 바이트가 있어야 하는 경우 isdataat 을 내용의 선행자(pre-cursor)로 사용해야 함.



content 키워드에는 여러 수정자(modifier) 키워드가 있음. </br>
수정자(modifier) 키워드는 이전에 지정된 내용이 어떻게 작동하는지를 변경함. </br>
수정자(modifier) 키워드는 다음과 같음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
content </span>수정자<span lang="EN-US">(modifiers) &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">수정자<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">섹션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">nocase<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.5<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">rawbytes<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.6<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">depth<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.7<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.8<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">distance<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.9<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">within<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.10<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_client_body<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.11<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_cookie<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.12<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_raw_cookie<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.13<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_header<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.14<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_raw_header<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.15<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_method<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.16<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_uri<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.17<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_raw_uri<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.18<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_stat_code<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.19<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">http_stat_msg<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.20<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">fast_pattern<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.22<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.2 protected_content 
protected_content 키워드는 content 키워드의 많은 기능을 제공하지만 매우 다른 방식으로 수행되고 활용됨. </br>
protected_content 키워드가 content 키워드에 비해 갖는 주요 이점은 보안 해시 다이제스트만 공개함으로써 지정된 컨텐츠를 숨길 수 있다는 것임. </br>
content 키워드와 마찬가지로 주요 목적은 특정 바이트의 문자열을 일치시키는 것임. </br>
들어오는 패킷의 일부를 해싱한 결과값과 지정된 해시값을 비교하여 검색을 수행하므로 계산 비용이 많이 듬. 


현재는 protected_content 키워드로 MD5, SHA256, SHA512 해시 알고리즘을 사용할 수 있음. </br>
Snort 설정에서 기본값을 설정하지 않은 경우 해시를 사용하여 규칙에 해시 알고리즘을 지정해야 함. </br>
또한, 원시 데이터의 길이를 나태내기 위해 length 수정자(modifier)를 이용해서 사용해야 함.



content 키워드와 마찬가지로 여러 protected_content 규칙을 하나의 규칙으로 사용할 수 있음. </br>
또한, 여러 protected_content  규칙을 여러 protected_content 규칙과 혼합할 수 있음.



규칙 앞에 ! 가 있으면 대상 콘텐츠가 포함되지 않은 패킷에 대해 경고(alert)를 트리거함. </br>
이는 특정 패턴과 일치하지 않는 패킷에 대해 경고(alert)하려는 규칙을 작성할 때 유용함.



Protected_content 키워드는 일부 content 수정자(modifiers)와 함께 사용할 수 있으나 지원되지 않는 것들은 아래와 같음: </br>
nocase </br>
fast_pattern </br>
depth </br>
within
</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">protected_content:[!]"&lt;content
  hash&gt;", length:orig_len[, hash:md5|sha256|sha512];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">"HTTP"
  </span></i><i>문자열에 대한 다음 경고<span lang="EN-US">(alert)
  : <o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any &lt;&gt; any 80 (msg:"MD5 Alert";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">protected_content:"293C9EA246FF9985DC6F62A650F78986";
  hash:md5; offset:0; length:4;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any &lt;&gt; any 80 (msg:"SHA256 Alert";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">protected_content:"56D6F32151AD8474F40D7B939C2161EE2BBF10023F4AF1DBB3E13260EBDC6342";
  hash:sha256; offset:0; length:4;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

! 수정자(modifier)는 해당 수정자가 포함된 전체 내용 검색 결과를 무효화함. </br>
예를 들어 content:!"A"; within:50; 규칙일 경우 페이로드가 5 바이트 뿐이며 해당 5 바이트에 “A” 가 없으면 결과는 일치로 리턴함. </br>
유효한 일치를 위해 50 바이트가 있어야 하는 경우 isdataat 을 내용의 선행자(pre-cursor)로 사용해야 함. </br>


### 5.3 hash
hash 키워드는 protected_content 규칙과 일치할 때 사용할 해싱 알고리즘을 지정하는 데 사용됨.
Snort 설정에 기본 알고리즘이 지정되지 않은 경우 protected_content 규칙에 반드시 사용할 알고리즘을 지정해야 함.
현재 MD5, SHA256, SHA512가 지원됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">hash:[md5|sha256|sha512];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.4 length
length 키워드는 protected_content 규칙 요약(digest)에 지정된 컨텐츠의 원래 길이를 지정하는데 사용됨. 
제공된 값은 0보다 크도 65536보다 작아야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">length:[&lt;original_length&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.5 nocase
nocase 키워드를 사용하면 규칙 작성기(rule writer)가 Snort에서 대소문자를 무시하고 특정 패턴을 찾도록 지정할 수 있음. 
nocase 는 규칙에서 이전 content 키워드를 수정함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">nocase;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 21 (msg:"FTP ROOT"; content:"USER
  root"; nocase;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>



### 5.6 rawbytes
rawbytes 키워드를 사용하면 규칙이 원시 패킷 데이터를 보고 전처리기(preprocessors)에 의해 수행된 디코딩을 무시함.
이는 content 키워드 옵션의 수정자(modifier) 역할을 함.

</br>

HTTP Inspect 는 원시 HTTP 요청 및 응답의 특정 부분과 일치하는 http_raw_cookie, http_raw_header, http_raw_uri 등과 같은 원시 데이터를 사용하기 위한 키워드 세트가 있음.

</br>

rawbytes 가 명시적으로 지정되지 않은 경우 대부분의 다른 전처리기는 기본적으로 컨텐츠 일치를 위해 디코딩/정규화된 데이터를 사용함. 
따라서 패킷에서 임의의 원시 데이터를 검사하려면 rawbytes 를 지정해야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rawbytes;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>



<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는 컨텐츠 패턴 일치자<span lang="EN-US">(content patten matcher)</span>에게<span lang="EN-US">&nbsp;Telnet&nbsp;</span>디코더가 제공한 디코딩된 트래픽 대신 원시 트래픽을 보도록 지시함<span lang="EN-US">.</span></span></i></p><p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;"><br></span></span></i></p><p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 21 (msg:"Telnet NOP"; content:"|FF
  F1|"; rawbytes;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.7 depth

depth 키워드를 사용하면 규칙 작성자(rule writer)가 지정된 패턴을 검색해야 하는 거리를 지정할 수 있음. </br>
예를 들어 "depth:5;" 는 페이로드의 처음 5 바이트 내에서만 지정된 패턴을 찾도록 지시함. </br>
depth 키워드는 이전 content 키워드에 대한 수정자이므로 depth 키워드를 지정하기 전에 content 키워드가 있어야 함. </br>
이 키워드는 검색되는 패턴 길이보다 크거나 같은 값을 허용하며 허용 범위는 1 ~ 65535 임. </br>
동일한 규칙에서 byte extract 키워드로 추출된 변수를 참조하는 문자열 값으로 설정할 수도 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">depth:[&lt;number&gt;|&lt;var_name&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.8 offset
offset 키워드를 사용하면 규칙 작성기(Rule Writer)가 패킷 내에서 패턴 검색을 시작할 위치를 지정할 수 있음.
예를 들어 "offset:5;" 는 페이로드의 처음 5 바이트 이후에 지정된 패턴을 찾도록 Snort 에 지시함.
offset 키워드는 이전 content 키워드에 대한 수정자이므로 offset 키워드를 지정하기 전에 content 키워드가 있어야 함.
해당 키워드의 값 허용 범위는 -65535 ~ 65535 임.
동일한 규칙에서 byte extract 키워드로 추출된 변수를 참조하는 문자열 값으로 설정할 수도 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset:[&lt;number&gt;|&lt;var_name&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다음
  예제는 결합된<span lang="EN-US"> content, offset </span>및<span lang="EN-US"> depth </span>키워드를
  사용하는 예제임<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"cgi-bin/phf"; offset:4;
  depth:20;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.9 distance
distance 키워드를 사용하면 규칙 작성자가 이전 패턴 일치의 끝을 기준으로 지정된 패턴 검색을 시작하기 전에 Snort 가 무시해야 하는 패킷의 거리를 지정할 수 있음.
이는 패킷의 시작이 아닌 마지막 패턴 일치의 끝과 관련이 있다는 점으로 offset 키워드와 정반대임.
해당 키워드의 값 허용 범위는 -65535 ~ 65535 임.
동일한 규칙에서 byte extract 키워드로 추출된 변수를 참조하는 문자열 값으로 설정할 수도 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">distance:[&lt;byte_count&gt;|&lt;var_name&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> /ABC.{1,}DEF/ </span>의 정규표현식과 매핑됨<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any any (content:"ABC"; content:"DEF";
  distance:1;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.10 within
within 키워드는 content 키워드를 사용하여 패턴 일치 사이에 최대 N 바이트가 되도록 하는 content 수정자임. (5.1 참조)
distance 키워드와 함께 규칙 옵션으로 사용하도록 설계됨.
해당 키워드는 검색되는 패턴 길이보다 크거나 같은 값을 허용하며 최대값은 63335 임.
동일한 규칙에서 byte extract 키워드로 추출된 변수를 참조하는 문자열 값으로 설정할 수도 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">within:[&lt;byte_count&gt;|&lt;var_name&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> ABC </span>일치한 후<span lang="EN-US"> 10 </span>바이트를 넘지 않도록<span lang="EN-US"> EFG </span>검색을 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any any (content:"ABC"; content:"EFG";
  within:10;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.11 http_client_body
http_client_body 키워드는 HTTP 클라이언트 요청의 본문으로 검색을 제한하는 content 수정자임.
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_client_body 키워드를 지정하기 전에 content 키워드가 있어야 함.
이 옵션으로 검사하는 데이터의 양은 HttpInspect 의 포스트 깊이 구성 옵션(post depth config option)에 따라 다름.
이 키워드를 사용한 패턴 일치는 포스트 깊이(post depth)가 -1 로 설정한 경우 작동하지 않음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_client_body;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청의
  본문으로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_client_body;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>


노트 : </br>
http_client_body 수정자는 동일한 content 에 대해 rawbytes 수정자와 함께 사용할 수 없음.


### 5.12 http_cookie
http_cookie 키워드는 HTTP 클라이언트 요청 또는 HTTP 서버 응답의 추출된 쿠키 헤더 필드(헤더 필드 이름 자체와 헤더 필드 행을 종료하는 CRLF 제외)로 검색을 제한하는 content 수정자임. (HttpInspect 구성에 따라) </br>
쿠키 버퍼에는 헤더 필드 이름이나 선행 공백 및 헤더 필드 행을 종료하는 CRLF 가 포함되지 않음. </br>
이는 HTTP 헤더 버퍼에 포함됨. </br>
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_cookie 키워드를 지정하기 전에 content 키워드가 있어야 함. </br>
이 키워드는 쿠키 사용 구성 옵션(enable cookie config option)에 따라 다름. </br>
이 옵션이 구성된 경우에만 쿠키 헤더 필드가 추출됨. </br>
쿠키 사용이 지정되지 않은 경우에도 쿠키는 HTTP 헤더로 끝남. </br>
쿠키 사용이 지정되지 않은 경우 HTTP 쿠키 사용은 HTTP 헤더 사용과 동일함. </br>
추출된 쿠키 헤더 필드는 HttpInspect 구성에 따라 NORMALIZED 일 수 있음.
</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_cookie;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청의
  추출된 쿠키 헤더 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_cookie;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>


노트 : </br>
http_cookie 수정자는 동일한 content 에 대해 rawbytes 또는 fast_pattern 수정자와 함께 사용할 수 없음.

### 5.13 http_raw_cookie
http_raw_cookie 키워드는 HTTP 클라이언트 또는 HTTP 서버 응답의 추출된 비정규화(UNNORMALIZED) 쿠키 헤더 필드로 검색을 제한하는 content 수정자임. (HttpInspect 구성에 따라)
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_raw_cookie 키워드를 지정하기 전에 content 키워드가 있어야 함.
이 키워드는 쿠키 사용 구성 옵션(enable cookie config option)에 따라 다름.
이 옵션이 구성된 경우에만 쿠키 헤더 필드가 추출됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_raw_cookie;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청의
  추출된 비정규화<span lang="EN-US">(Unnormalized) </span>쿠키 헤더 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_raw_cookie;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

노트 : </br>
http_raw_cookie 수정자는 동일한 content 에 대해 rawbytes, http_cookie 또는 fast_pattern 수정자와 함께 사용할 수 없음.

### 5.14 http_header
http_header 키워드는 HTTP 클라이언트 요청 또는 HTTP 서버 응답의 추출된 헤더 필드로 검색을 제한하는 content 수정자임. (HttpInspect 구성에 따라)
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_header 키워드를 지정하기 전에 content 키워드가 있어야 함.
추출된 헤더 필드는 HttpInspect 구성에 따라 NORMALIZED 일 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_header;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청
  또는<span lang="EN-US"> HTTP </span>서버 응답의 추출된 헤더 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_header;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

노트 : </br>
http_header 수정자는 동일한 content 에 대해 rawbytes 수정자와 함께 사용할 수 없음.

### 5.15 http_raw_header
http_raw_header 키워드는 HTTP 클라이언트 또는 HTTP 서버 응답의 추출된 비정규화(UNNORMALIZED) 헤더 필드로 검색을 제한하는 content 수정자임. (HttpInspect 구성에 따라)
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_raw_header 키워드를 지정하기 전에 content 키워드가 있어야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_raw_header;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청
  또는 <span lang="EN-US">HTTP </span>서버 응답의 추출된 비정규화<span lang="EN-US">(Unnormalized)
  </span>헤더 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_raw_header;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_raw_header 수정자는 동일한 content 에 대해 rawbytes, http_header 또는 fast_pattern 수정자와 함께 사용할 수 없음.

### 5.16 http_method

http_method 키워드는 HTTP 클라이언트 요청에서 추출된 Method 로 검색을 제한하는 content 수정자임.
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_method 키워드를 지정하기 전에 content 키워드가 있어야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_method;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "GET" </span>패턴 검색을<span lang="EN-US"> HTTP </span>클라이언트 요청에서
  추출된 메소드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"GET";
  http_method;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_method 수정자는 동일한 content 에 대해 rawbytes 또는 fast_pattern 수정자와 함께 사용할 수 없음.


### 5.17 http_uri
http_uri 키워드는 정규화(NORMALIZED) 요청 URI 필드로 검색을 제한하는 content 수정자임.
content 규칙 옵션 다음에 http_uri 수정자를 사용하는 것은 uricontent 키워드를 사용하는 것과 같음. (5.23 참조)
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_uri 키워드를 지정하기 전에 content 키워드가 있어야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_uri;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴 검색을 정규화<span lang="EN-US">(NORMALIZED)
  URI </span>로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"EFG";
  http_uri;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_uri 수정자는 동일한 content 에 대해 rawbytes 수정자와 함께 사용할 수 없음.

### 5.18 http_raw_uri
http_raw_uri 키워드는 비정규화(UNNORMALIZED) 요청 URI 필드로 검색을 제한하는 content 수정자임.
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_raw_uri 키워드를 지정하기 전에 content 키워드가 있어야 함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_raw_uri;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "EFG" </span>패턴
  검색을 비정규화<span lang="EN-US">(UNNORMALIZED) URI </span>로 제한함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">alert tcp any any -&gt; any 80
  (content:"ABC"; content:"EFG"; http_raw_uri;)<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_raw_uri 수정자는 동일한 content 에 대해 rawbytes, http_uri 또는 fast_pattern 수정자와 함께 사용할 수 없음.


### 5.19 http_stat_code
http_stat_code 키워드는 HTTP 서버 응답에서 추출된 상태 코드 필드로 검색을 제한하는 content 수정자임.
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_stat_code 키워드를 지정하기 전에 content 키워드가 있어야 함.
상태 코드 필드는 확장 응답 검사가 HttpInspect 에 대해 구성된 경우에만 추출됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_stat_code;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "200" </span>패턴에 대한 검색을<span lang="EN-US"> HTTP </span>서버
  응답의 추출된 상태 코드 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any 80 -&gt; any any (content:"ABC"; content:"200";
  http_stat_code;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_stat_code 수정자는 동일한 content 에 대해 rawbytes 또는 fast_pattern 수정자와 함께 사용할 수 없음.

### 5.20 http_stat_msg
http_stat_msg 키워드는 HTTP 서버 응답에서 추출된 상태 메시지 필드로 검색을 제한하는 content 수정자임.
이 키워드는 이전 content 키워드에 대한 수정자이므로 http_stat_msg 키워드를 지정하기 전에 content 키워드가 있어야 함.
상태 메시지 필드는 확장 응답 검사가 HttpInspect 에 대해 구성된 경우에만 추출됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_stat_msg;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "Not Found" </span>패턴 검색을<span lang="EN-US"> HTTP </span>서버
  응답의 추출된 상태 메시지 필드로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABC"; content:"Not
  Found"; http_stat_msg;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
http_stat_msg 수정자는 동일한 content 에 대해 rawbytes 또는 fast_pattern 수정자와 함께 사용할 수 없음.

### 5.21 http_encode
http_encode 키워드는 HTTP 클라이언트 요청 또는 HTTP 서버 응답에 있는 인코딩 유형을 기반으로 경고를 활성화함. </br>
HTTP 인코딩과 관련된 여러 키워드가 있음. </br>
키워드 'uri', 'header' 및 'cookie' 는 특정 인코딩 유형을 검색하는 데 사용되는 HTTP 필드를 결정함. </br>
키워드 'utf8', 'double encode', 'non ascii', 'uencode', 'iis encode', 'ascii' 및 'bare byte' 는 경고를 트리거하는 인코딩 유형을 결정함. </br>
이러한 키워드는 OR 연산을 사용하여 결합할 수 있으며 제외도 허용됨. </br>
규칙이 키워드 'header' 와 함께 작동하려면 구성 옵션 '헤더 정규화(normalize header)'를 설정해야 함. </br>
키워드 'cookie' 는 '쿠키 사용(enable cookie)' 및 '쿠키 정규화(normalize cookies)' 옵션에 따라 다름. </br>
이 규칙 옵션은 지정된 HTTP 필드가 정규화(NORMALIZED)가 아닌 경우 인코딩을 감지할 수 없음.

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">uri<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">HTTP </span>클라이언트 요청 <span lang="EN-US">URI </span>필드에서
  지정된 인코딩 유형을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">header<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답
  헤더 필드에서 지정된 인코딩 유형을 확인함<span lang="EN-US">. (</span>패킷의 흐름에 따라 다름<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">cookie<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답
  쿠키 헤더 필드에서 지정된 인코딩 유형을 확인함<span lang="EN-US">. (</span>패킷의 흐름에 따라 다름<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">utf8<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 <span lang="EN-US">utf8 </span>인코딩을
  확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">double_encode<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 이중 인코딩<span lang="EN-US">(double
  encoding)</span>을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">non_ascii<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 비<span lang="EN-US"> ASCII </span>인코딩<span lang="EN-US">(non-ASCII encoding)</span>을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">uencode<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 <span lang="EN-US">u </span>인코딩<span lang="EN-US">(u-encoding)</span>을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bare_byte<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 <span lang="EN-US">bare </span>바이트
  인코딩<span lang="EN-US">(bare byte encoding)</span>을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ascii<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 <span lang="EN-US">ASCII </span>인코딩을
  확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">iis_encode<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 버퍼에서 <span lang="EN-US">IIS </span>유니코드
  인코딩을 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_encode:&lt;http buffer type&gt;,
  [!]&lt;encoding type&gt;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">http_encode:[uri|header|cookie],
  [!][&lt;utf8|double_encode|non_ascii|uencode|bare_byte|ascii|iis_encode&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (msg:"UTF8/UEncode Encoding present";
  http_encode:uri,utf8|uencode;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any any (msg:"No UTF8"; http_encode:uri,!utf8;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.22 fast_pattern

fast_pattern 키워드는 빠른 패턴 일치자(matcher)와 함께 사용할 규칙 내의 컨텐츠를 설정하는 content 수정자임. </br>
빠른 패턴 결정의 기본 동작은 가장 긴 HTTP 버퍼 컨텐츠를 사용하는 것임. </br>
HTTP 버퍼가 없으면 빠른 패턴이 가장 긴 컨텐츠임. </br>
이 동작이 주어지면 짧은 컨텐츠가 긴 컨텐츠보다 "고유한" 경우 유효함. </br>
즉, 더 짧은 컨텐츠가 긴 컨텐츠보다 패킷에서 발견될 가능성이 적음. </br>

</br>

빠른 패턴 일치자(matcher)는 선택을 위해 규칙의 컨텐츠를 사용하고 컨텐츠가 페이로드에서 발경되는 경우에만 해당 규칙을 평가하여 일치 가능성이 있는 규칙만 선택하는데 사용됨. </br>
이는 오버헤드로 보일 수 있지만 평가해야 하는 규칙 수를 크게 줄여 성능을 향상시킬 수 있음. </br>
빠른 패턴 일치자(matcher)에 사용되는 컨텐츠가 좋을수록 규칙이 불필요하게 평가될 가능성이 줄어듬. </br>

</br>

이 키워드는 이전 content 키워드에 대한 수정자이므로 fast_pattern 을 지정하기 전에 규칙에 content 규칙 옵션이 있어야 함. </br>
fast_pattern 옵션은 규칙당 한 번만 지정할 수 있음. </br>

</br>

노트 : </br>
fast_pattern 수정자는 다음 http 컨텐츠 수정자와 함께 사용할 수 없음. (http_cookie, http_raw_uri, http_raw_header, http_raw_cookie, http_method, http_stat_code, http_stat_msg) </br>
fast_pattern 수정자는 해당 내용이 offset, depth, distance 및 within 내에서 수정되지 않은 경우에만 부정된(negated) 컨텐츠과 함께 사용할 수 있음. </br>
빠른 패턴 일치자(matcher)는 항상 대소문자를 구분하지 않음. </br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">fast_pattern </span>옵션은
  단독으로 사용하거나 선택적으로 인수를 사용할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">단독으로 사용하는 경우 단순히 지정된 컨텐츠를 규칙의 빠른 패턴 컨텐츠로 사용한다는
  의미임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fast_pattern;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">선택적 인수는 컨텐츠가 빠른 패턴 일치자<span lang="EN-US">(matcher)</span>에만
  사용되어야 하며 규칙 옵션으로 평가되지 않도록 지정하는 데만 사용할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">예를 들어<span lang="EN-US">, </span>알려진 컨텐츠가 페이로드의
  위치와 관계없이 페이로드에 있어야 하는 경우에 유용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">규칙 옵션을 평가하는 데 필요한 시간을 절약하기 때문임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">1. </span>패턴이 대소문자를 구분하지 않는 방식으로 패턴 일치자<span lang="EN-US">(matcher)</span>에 삽입되므로 수정된 컨텐츠는 대소문자를 구분하지 않아야 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">2. </span>부정된<span lang="EN-US">(negated) </span>컨텐츠는
  사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">3. </span>컨텐츠에는<span lang="EN-US"> offset,
  depth, distance </span>또는<span lang="EN-US"> within </span>와 같은 위치 수정자가 있을 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fast_pattern:only;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">선택적 인수<span lang="EN-US"> &lt;offset&gt;,
  &lt;length&gt; </span>를 사용하여 컨텐츠의 일부만 빠른 패턴 일치자<span lang="EN-US">(matcher)</span>에
  사용되도록 지정할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이는 패턴이 매우 길고<span lang="EN-US"> "</span>고유성<span lang="EN-US">"</span>을 충족시키기 위해 패턴의 일부만 필요한 경우에 유용하므로 빠른 패턴 일치자<span lang="EN-US">(matcher)</span>에 전체 패턴을 저장하는 데 필요한 메모리가 줄어듬<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fast_pattern:&lt;offset&gt;,&lt;length&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

 
</br>


노트 : </br>
선택적 인수 \<offset>, \<length> 는 상호 배타적임. 

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "IJKLMNO" </span>패턴이 이전 패턴<span lang="EN-US">
  "ABCDEFGH" </span>보다 짧더라도<span lang="EN-US"> fast_pattern </span>일치자와
  함께 사용되도록 함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (content:"ABCDEFGH"; content:"IJKLMNO";
  fast_pattern;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> fast_pattern </span>일치자에<span lang="EN-US">
  content:"IJKLMNO"; </span>를 사용하고<span lang="EN-US"> content</span>가<span lang="EN-US"> fast_pattern </span>일치자만 사용되어야 하며<span lang="EN-US"> content </span>규칙
  옵션으로 평가되지 않아야 함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (content:"ABCDEFGH";
  content:"IJKLMNO"; nocase; fast_pattern:only;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> "JKLMN" </span>을 <span lang="EN-US">fast_pattern content </span>로
  사용하지만 <span lang="EN-US">content </span>규칙 옵션을 <span lang="EN-US">“IJKLMNO” </span>로
  평가함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"ABCDEFGH";
  content:"IJKLMNO"; fast_pattern:1,5;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.23 uricontent
Snort 규칙 언어의 uricontent 키워드는 정규화(NORMALIZED) 요청 URI 필드를 검색함. </br>
이는 content 키워드에 http_uri 수정자를 사용하는 것과 같음. </br>
따라서 %2f 또는 Directory Traversal 기법과 같이 정규화된 항목을 포함하는 규칙을 작성하는 경우 이러한 규칙은 경고하지 않음. </br>
그 이유는 찾고 있는 항목이 정규화된 URI 버퍼에서 찾기 때문임. </br>

</br>


예를 들어, URI : </br>
/scripts/..%c0%af../winnt/system32/cmd.exe?/c+ver

</br>

다음으로 정규화됨 : </br>
/winnt/system32/cmd.exe?/c+ver

</br>

또 다른 예, URI : </br>
bin/aaaaaaaaaaaaaaaaaaaaaaaaaa/..%252fp%68f?

</br>

다음으로 정규화됨 : </br>
/cgi-bin/phf?

</br>

uricontent 규칙을 작성할 때 URI 가 정규화될 문자열(context)에서 찾을려는 content 를 작성해야 함. </br>
예를 들어 Snort 가 Directory Traversal 기법을 정규화하는 경우 Directory Traversal 기법을 포함하지 말 것! </br>
content 옵션을 사용하여 정규화되지 않은 컨텐츠를 찾는 규칙을 작성할 수 있음. (5.1 섹션 참조) </br>
uricontent 는 content 키워드에 사용할 수 있는 여러 수정자와 함께 사용할 수 있음. </br>
여기에는 다음이 포함되며 이 옵션은 HTTP 검사 전처리기(HTTP Inspect preprocessor)와 함께 작동함. </br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
uricontent </span>수정자 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">수정자<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">섹션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">nocase<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.5<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">depth<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.7<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.8<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">distance<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.9<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">within<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.10<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">fast_pattern<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">5.22<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">uricontent:[!]"&lt;content
  string&gt;";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
uricontent 는 rawbytes 수정자 또는 다른 HTTP 수정자로 수정할 수 없음. </br>
비정규화(UNNORMALIZED) 요청 URI 필드를 검색하려면 content 옵션과 함께 http_raw_uri 수정자를 사용해야 함. </br>


### 5.24 urilen
Snort 규칙 언어의 urilen 키워드는 일치시킬 URI 길이의 정확한 길이, 최소 길이, 최대 길이 또는 범위를 지정함. 
기본적으로 원시 URI 버퍼가 사용됨. 
선택적 <uribuf> 인수를 사용하면 원시 또는 정규화된 버퍼를 사용할 지 여부를 지정할 수 있음. 

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">urilen:min&lt;&gt;max[,&lt;uribuf&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">urilen:[&lt;|&gt;]&lt;number&gt;[,&lt;uribuf&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">&lt;uribuf&gt; : "norm" |
  "raw"<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

</br>

다음 예는 길이가 5 바이트인 URI 와 일치함. </br>
urilen:5;

</br>

다음 예는 5 바이트보다 짧은 URI 와 일치함. </br>
urilen:<5;

</br>

다음 예는 5 바이트보다 크고 10 바이트(포함)보다 작은 URI 와 일치함. </br>
urilen:5<>10;

</br>

다음 예는 정규화된 URI 버퍼를 사용하여 500 바이트보다 큰 URI 를 일치시킴. </br>
urilen:>500,norm;

</br>

다음 예는 원시 URI 버퍼를 사용하도록 명시적으로 나타내는 500 바이트보다 큰 URI 와 일치함. </br>
urilen:>500,row;

</br>

이 옵션은 HTTP 감사 전처리기(HTTP Inspect preprocessor)와 함께 작동함.


### 5.25 isdataat
페이로드의 지정된 위치에 데이터가 있는지 확인하고 선택적으로 이전의 컨텐츠 끝과 관련된 데이터를 찾음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">isdataat:[!]&lt;int&gt;[,
  relative|rawbytes];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은
  패킷에 <span lang="EN-US">PASS </span>문자열이 있는지 확인한 다음 문자열 <span lang="EN-US">PASS </span>가
  끝난 후 <span lang="EN-US">50 </span>바이트 이상이 있는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">그런
  다음<span lang="EN-US"> PASS </span>문자열 끝의 <span lang="EN-US">50 </span>바이트 내에 개행 문자가
  없는지 확인함<span lang="EN-US">.</span></span></i></p><p class="MsoNoSpacing"><i><span style="font-family: courier;"><span lang="EN-US"><br></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 111 (content:"PASS"; isdataat:50,relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">content:!"|0a|";
  within:50;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

rawbytes 수정자가 isdataat 와 함께 지정되면 원시 패킷 데이터를 살펴보고 전처리기가 수행한 모든 디코딩을 무시함.
이 수정자는 이전 컨텐츠 일치가 원시 패킷 데이터에 있는 한 relative 수정자와 함께 작동함.
! 수정자는 isdataat 테스트의 결과를 무효화함.
페이로드 내에 특정 양의 데이터가 없으면 경고함.
예를 들어 수정자 컨텐츠가 있는 규칙은 다음과 같음.
"foo"; isdataat:!10,relative; 는 페이로드가 끝나기 전에 “foo” 뒤에 10 바이트가 없으면 경고함.



### 5.26 pcre
pcre 키워드를 사용하면 perl 호환 정규식을 사용하여 규칙을 작성할 수 있음.
무엇을 할 수 있는지에 대한 자세한 내용은 PCRE 웹사이트(http://www.pcre.org) 를 확인하십시오.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식<span lang="EN-US"> &gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">pcre:[!]"(/&lt;regex&gt;/|m&lt;delim&gt;&lt;regex&gt;&lt;delim&gt;)[ismxAEGRUBPHMCOIDKYS]";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

post-re 수정자는 정규식에 대한 컴파일 시간 플래그를 설정함.

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">Perl </span>호환 수정자<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">i<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">대소문자를 구분하지 않음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">s<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">점 메타 문자<span lang="EN-US">(.)</span>에 줄바꿈 포함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">m<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">기본적으로 문자열은 하나의 큰 문자 줄로 처리됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">^ </span>및 <span lang="EN-US">$ </span>는 문자열의
  시작과 끝으로 일치함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">m </span>이 설정되면<span lang="EN-US"> ^ </span>및
  <span lang="EN-US">$ </span>는 버퍼의 모든 개행 바로 뒤 또는 바로 앞과 버퍼의 맨 처음과 맨 끝을 일치함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">x<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패턴의 공백 데이터 문자는 이스케이프되거나 문자 클래스 내부의 경우를 제외하고
  무시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">A<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패턴은 버퍼의 시작 부분에서만 일치해야 함<span lang="EN-US">.
  (^ </span>와 동일<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">E<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">제목 문자열의 끝에서만 일치하도록 <span lang="EN-US">$ </span>를
  설정하십시오<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">E </span>가 없으면 <span lang="EN-US">$ </span>는
  개행 문자인 경우 최종 문자 바로 앞과도 일치함<span lang="EN-US">. (</span>다른 개행 앞이 아님<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">G<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">한정자<span lang="EN-US">(quantifier)</span>의 <span lang="EN-US">“</span>탐욕<span lang="EN-US">”(greediness)</span>을 반전하여 기본적으로 탐욕스럽지<span lang="EN-US">(greedy) </span>않지만 <span lang="EN-US">“?” </span>가 뒤따르면 탐욕스러워짐<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">R<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">마지막 패턴 일치의 끝을 기준으로 일치함<span lang="EN-US">.
  (distance:0; </span>과 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">U<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">디코딩된 <span lang="EN-US">URI </span>버퍼를 일치시킴<span lang="EN-US">. (uricontent </span>및<span lang="EN-US"> http_uri </span>와 비슷<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 정규화되지 않은 <span lang="EN-US">HTTP </span>요청<span lang="EN-US"> uri </span>버퍼 수정자<span lang="EN-US">(I)</span>와
  함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">I<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화되지 않은 <span lang="EN-US">HTTP </span>요청 <span lang="EN-US">uri </span>버퍼와 일치함<span lang="EN-US">. (http_raw_uri </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 <span lang="EN-US">HTTP </span>요청
  <span lang="EN-US">uri </span>버퍼 수정자<span lang="EN-US">(U)</span>와 함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">P<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화되지 않은 <span lang="EN-US">HTTP </span>요청 본문과
  일치함<span lang="EN-US">. (http_client_body </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">SIP </span>메시지의 경우 요청 또는 응답에 대해 <span lang="EN-US">SIP </span>본문을 일치시킴<span lang="EN-US">. (sip_body </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">H<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화된 <span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답 헤더와 일치함<span lang="EN-US">. (http_header </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 정규화되지 않은 <span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답 헤더 수정자<span lang="EN-US">(D)</span>와 함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">SIP </span>메시지의 경우 요청 또는 응답에 대해 <span lang="EN-US">SIP </span>헤더를 일치시킴<span lang="EN-US">. (sip_header </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">D<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화되지 않은 <span lang="EN-US">HTTP </span>요청 또는
  <span lang="EN-US">HTTP </span>응답 헤더와 일치함<span lang="EN-US">. (http_raw_header </span>와
  유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 정규화된 <span lang="EN-US">HTTP
  </span>요청 또는 <span lang="EN-US">HTTP </span>응답 헤더 수정자<span lang="EN-US">(H)</span>와
  함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">M<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화된 <span lang="EN-US">HTTP </span>요청 방법과 일치함<span lang="EN-US">. (http_method </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">C<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화된 <span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답 쿠키와 일치함<span lang="EN-US">. (http_cookie </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 정규화되지 않은 <span lang="EN-US">HTTP </span>요청 또는 <span lang="EN-US">HTTP </span>응답 쿠키 수정자<span lang="EN-US">(K)</span>와 함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">K<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">정규화되지 않은 <span lang="EN-US">HTTP </span>요청 또는
  <span lang="EN-US">HTTP </span>응답 쿠키와 일치함<span lang="EN-US">. (http_raw_cookie </span>와
  유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 수정자는 동일한 컨텐츠에 대해 정규화된 <span lang="EN-US">HTTP
  </span>요청 또는 <span lang="EN-US">HTTP </span>응답 쿠키 수정자<span lang="EN-US">(C)</span>와
  함께 사용할 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">S<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">HTTP </span>응답 상태 코드와 일치함<span lang="EN-US">.
  (http_stat_code </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">Y<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">HTTP </span>응답 상태 메시지와 일치함<span lang="EN-US">.
  (http_stat_msg </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">B<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">디코딩된 버퍼를 사용하지 마십시오<span lang="EN-US">.
  (rawbytes </span>와 유사<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">O<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 표현식에 대해 구성된 <span lang="EN-US">pcre </span>일치
  제한 및 <span lang="EN-US">pcre </span>일치 제한 재귀를 재정의함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된<span lang="EN-US"> pcre </span>패턴을 평가하는
  동안 제한을 완전히 무시함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
수정자 R(상대) 과 B(원시 바이트)는 U, I, P, H, D, M, C, K, S 및 Y 와 같은 HTTP 수정자와 함께 허용되지 않음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는
  <span lang="EN-US">HTTP URI foo.php?id=&lt;some numbers&gt; </span>에 대해 대소문자를 구분하지
  않는 검색을 수행함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any 80 (content:"/foo.php?id=";
  pcre:"/\/foo.php?id=[0-9]{1,10}/iU";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

노트 : </br>
pcre 를 사용하는 규칙에 하나 이상의 content 키워드가 있는 것이 좋음. </br>
이를 통해 fast_pattern 일치자가 일치하지 않는 패킷을 필터링하여 회선을 통해 들어오는 각 패킷에 대해 pcre 평가가 수행되지 않도록 할 수 있음.

</br>

노트 : </br>
Snort 가 PCRE 를 사용하여 여러 URI 를 처리하는 것이 예상대로 작동하지 않음. </br>
uricontent 없이 사용되는 PCRE 는 첫 번째 URI 만 평가함. </br>
pcre 를 사용하여 모든 URI 를 검사하려면 content 또는 uricontent 를 사용해야 함. </br>



### 5.27 pkt_data

이 옵션은 감지에 사용되는 커서(cursor)를 원시 전송 페이로드로 설정함.
규칙에서 pkt_data 뒤에 오는 상대 또는 절대 컨텐츠 일치(HTTP 수정자 또는 원시 바이트 없음) 및 기타 페이로드 감지 규칙 옵션은 커서(탐지에 사용)가 다시 설정될 때까지 원시 TCP/UDP 페이로드 또는 정규화된 버퍼(telnet, 정규화된 smtp 경우)에 적용됨.
이 규칙 옵션은 규칙에서 여러 번 사용할 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">pkt_data;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"Absolute Match"; pkt_data;
  content:"BLAH"; offset:0; depth:10;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"PKT DATA"; pkt_data;
  content:"foo"; within:10;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"PKT DATA"; pkt_data;
  content:"foo";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><br></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any any(msg:"PKT DATA"; pkt_data;
  pcre:"/foo/i";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>



### 5.28 file_data



이 옵션은 감지에 사용되는 커서를 다음 버퍼 중 하나로 설정함.



1. 탐지되는 트래픽이 HTTP 일 때 버퍼를 설정함 : </br>
  a. HTTP 응답 본문 (chunking/압축/정규화 제외) </br>
  b. HTTP dechunked 응답 본문 </br>
  c. HTTP 압축해제 응답 본문 (inspect_gzip 이 켜져 있는 경우) </br>
  d. HTTP 정규화된 응답 본문 (normalized_javascript 가 설정된 경우) </br>
  e. HTTP UTF 정규화된 응답 본문 (normalized_utf 가 설정된 경우) </br>
  f. 모두 포함(All of the obove)

</br>

2. 감지되는 트래픽이 SMTP/POP/IMAP 인 경우 버퍼를 다음으로 설정함 : </br>
  a. SMTP/POP/IMAP 데이터 본문 (디코딩이 해제된 이메일 헤더 및 MIME 포함) </br>
  b. Base64 디코딩된 MIME 첨부 파일 (b64_decode_depth 가 -1 보다 큰 경우) </br>
  c. 인코딩되지 않은 MIME 첨부 파일 (bitenc_decode_depth 가 -1 보다 큰 경우) </br>
  d. 인용 인쇄 가능한(Quoted-Printable) 디코딩된 MIME 첨부 파일 (qp_decde_depth 가 -1 보다 큰 경우) </br>
  e. Unix-to-Unix 디코딩된 첨부 파일 (uu_decode_depth 가 -1 보다 큰 경우)

</br>


3. 1 과 2 번 항목으로 설정하지 않으면 페이로드로 설정됨.

</br>

상대 또는 절대 컨텐츠 일치(HTTP 수정자 또는 rawbytes 없음) 및 규칙에서 file_data 를 따르는 페이로드 감지 규칙 옵션은 다른 규칙 옵션에 의해 명시적으로 재설정될 때까지 이 버퍼에 적용됨. 
이 규칙 옵션은 규칙에서 여러 번 사용할 수 있음. 
file_data 에 대한 mime 인수는 더 이상 사용되지 않음. 
규칙 옵션 file_data 는 자체적으로 디코딩된 MIME 첨부를 가리킴. </br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">file_data;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>



<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"Absolute Match"; file_data;
  content:"BLAH"; offset:0; depth:10;)</span></span></i></p><p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;"><br></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"FILE DATA"; file_data; content:"foo";
  within:10;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"FILE DATA"; file_data;
  content:"foo";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any(msg:"FILE DATA"; file_data;
  pcre:"/foo/i";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다음
  규칙은 <span lang="EN-US">file_data </span>버퍼 내에서 컨텐츠 <span lang="EN-US">"foo"
  </span>를 검색하고 전체 패킷 페이로드 내에서 컨텐츠 <span lang="EN-US">"bar" </span>를 검색함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">규칙
  옵션 <span lang="EN-US">pkt_data </span>는 탐지에 사용되는 커서를 <span lang="EN-US">TCP </span>페이로드로
  재설정함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">alert
  tcp any any -&gt; any any(msg:"FILE DATA"; file_data;
  content:"foo"; pkt_data; content:"bar";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.29 base64_decode



이 옵션은 base64 로 인코딩된 데이터를 디코딩하는 데 사용됨.
이 옵션은 HTTP 인증 헤더와 같은 HTTP 헤더의 경우 특히 유용함.
이 옵션은 디코딩하기 전에 데이터를 펼침.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">base64_decode[:[bytes
  &lt;bytes_to_decode&gt;][, ][offset &lt;offset&gt;[, relative]]];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">디코딩할 <span lang="EN-US">base64 </span>인코딩 바이트
  수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 인수는 양수 및 <span lang="EN-US">0 </span>이 아닌
  값만 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 옵션을 지정하지 않으면 헤더 라인의 끝에 도달하거나 패킷 페이로드의 끝에
  도달할 때까지 <span lang="EN-US">base64 </span>로 인코딩된 데이터를 찾음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">relative </span>옵션이 지정될 때 <span lang="EN-US">doe_ptr
  </span>에 상대적인 오프셋을 결정하거나 <span lang="EN-US">base64 </span>인코딩 데이터의 검사를 시작하기 위해 패킷
  페이로드의 시작에 상대적인 오프셋을 결정함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 인수는 양수 및 <span lang="EN-US">0 </span>이 아닌
  값만 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">relative<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">base64 </span>로 인코딩된 데이터에 대한 검사가 <span lang="EN-US">doe_ptr </span>에 상대적임을 지정함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

base64_decode 에 대한 위의 인수는 선택사항임.



노트 : </br>
이 옵션은 HTTP 와 유사한 폴딩(folding)이 있는 프로토콜로 확장할 수 있음. </br>
폴딩(folding)이 없으면 다음 공백이나 탭없이 캐리지 리턴이나 줄바꿈 또는 둘 다가 표시되면 base64 로 인코딩된 데이터 검색이 종료됨. </br>
이 옵션은 다른 페이로드 감지 규칙 옵션이 base64 디코딩된 버퍼에서 작동하도록 base64_data 와 함께 사용해야 함. </br>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"Base64
  Encoded Data"; base64_decode; base64_data; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"foo
  bar"; within:20;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"Authorization
  NTLM"; content:"Authorization: NTLM"; base64_decode:relative;
  base64_data; content:"NTLMSSP"; )<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (msg:"Authorization NTLM"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"Authorization:";
  http_header; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">base64_decode:bytes
  12, offset 6, relative; base64_data; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">content:"NTLMSSP";
  within:8;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.30 base64_data



이 옵션은 file_date 규칙 옵션과 유사하며 감지에 사용되는 커서가 있는 경우 base64 디코딩된 버퍼의 시작 부분으로 설정하는 데 사용됨.
이 옵션은 인수를 사용하지 않음.
base64_data 옵션보다 먼저 base64_decode 규칙 옵션을 지정해야 함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">base64_data;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

이 옵션은 base64 디코딩된 버퍼가 있는 경우 일치함.



노트 : </br>
이 버퍼에서는 빠른 패턴 컨텐츠(fast pattern content) 일치가 허용되지 않음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (msg:"Authorization NTLM"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"Authorization:";
  http_header; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">base64_decode:bytes
  12, offset 6, relative; base64_data; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">content:"NTLMSSP";
  within:8;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.31 byte_test



특정 값(연산자 사용)에 대해 바이트 필드를 테스트함.
바이너리 값을 테스트하거나 대표 바이트 문자열을 해당 바이너리로 변환하고 테스트할 수 있음.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_test:&lt;bytes to convert&gt;,
  [!]&lt;operator&gt;, &lt;value&gt;, &lt;offset&gt; \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, relative][, &lt;endian&gt;][, string,
  &lt;number type&gt;][, dce] \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, bitmask &lt;bitmask_value&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes = 1 - 10<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">operator = ’&lt;’ | ’=’ | ’&gt;’ |
  ’&lt;=’ | ’&gt;=’ | ’&amp;’ | ’ˆ’<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">value = 0 - 4294967295<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset = -65535 to 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask_value = 1 to 4 byte hexadecimal
  value<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">Perl </span>호환 수정자<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_convert<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷에서 가져올 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>없이 사용할 경우 허용되는 값은 <span lang="EN-US">1-10 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>와 함께 사용하는 경우 허용되는 값은 <span lang="EN-US">1,2 </span>및 <span lang="EN-US">4 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">operator<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">값을 테스트하기 위해 수행할 작업 <span lang="EN-US">: <o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•</span><span lang="EN-US" style="font-family: courier;"> &lt; - </span><span style="font-family: courier;">미만</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &gt; - </span>보다 큼<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &lt;= - </span>작거나 같음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &gt;= - </span>크거나 같음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> = - </span>같음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &amp; - </span>비트 <span lang="EN-US">AND<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> ˆ - </span>비트<span lang="EN-US"> OR<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">value<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 값을 테스트할 값임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">처리를 시작할 페이로드의 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">relative<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">마지막 패턴 일치에 상대적인 오프셋을 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">endian<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">읽고 있는 번호의 엔디안 유형 <span lang="EN-US">: <o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•</span><span lang="EN-US" style="font-family: courier;"> big - </span><span style="font-family: courier;">데이터를 빅 엔디안으로
  처리</span><span lang="EN-US" style="font-family: courier;"> (</span><span style="font-family: courier;">기본값</span><span lang="EN-US" style="font-family: courier;">).</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> little - </span>데이터를 리틀
  엔디안으로 처리<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">string<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터는 패킷에 문자열 형식으로 저장됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">number
  type<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">읽을 번호 유형 <span lang="EN-US">: <o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•</span><span lang="EN-US" style="font-family: courier;"> hex - </span><span style="font-family: courier;">변환된 문자열 데이터가</span><span lang="EN-US" style="font-family: courier;"> 16 </span><span style="font-family: courier;">진수로 표시됨</span><span lang="EN-US" style="font-family: courier;">.</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> dec - </span>변환된 문자열 데이터가<span lang="EN-US"> 10 </span>진수로 표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> oct - </span>변환된 문자열 데이터가<span lang="EN-US"> 8 </span>진수로 표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>는<span lang="EN-US"> DCE/RPC 2 </span>전처리기가
  변환할 값의 바이트 순서를 결정하도록 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 바이트에 <span lang="EN-US">AND </span>연산자를
  적용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">결과는 마스크의 후행 <span lang="EN-US">0 </span>수와 동일한
  비트 수만큼 오른쪽 시프트됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

모든 연산자에 ! 연산자가 사실이 아닌지 확인함. 
만약 ! 연산자없이 지정된 경우 연산자는 = 로 설정됨.



노트 : </br> 
Snort 는 이러한 각 연산자에 대해 C 연산자를 사용함. </br>
& 연산자를 사용하면 if (data & value) { do something();} 을 사용하는 것과 같음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"AMD
  procedure 7 plog overflow"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  04 93 F3|"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  00 00 07|"; distance:4; within:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:4,
  &gt;, 1000, 20, relative;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"AMD
  procedure 7 plog overflow"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  04 93 F3|"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  00 00 07|"; distance:4; within:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:4,
  &gt;, 1000, 20, relative;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1234 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:4,
  =, 1234, 0, string, dec; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"got
  1234!";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1235 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:3,
  =, 123, 0, string, dec; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"got
  123!";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1236 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:2,
  =, 12, 0, string, dec; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"got
  12!";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1237 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:10,
  =, 1234567890, 0, string, dec; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"got
  1234567890!";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1238 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:8,
  =, 0xdeadbeef, 0, string, hex; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"got
  DEADBEEF!";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_test:2,
  =, 568, 0, bitmask 0x3FF0; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">msg:"got
  568 after applying bitmask 0x3FF0 on 2 bytes extracted";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.23 byte_jump



byte_jump 키워드를 사용하면 길이 인코딩된 프로토콜에 대한 규칙을 간단하게 작성할 수 있음.
데이터 일부의 길이를 읽은 다음 패킷에서 훨씬 앞으로 건너 뛰는 옵션을 사용하면 길이 인코딩된 프로토콜의 특정 부분을 건너 뛰고 특정 위치에서 탐지를 수행하는 규칙을 작성할 수 있음.
byte_jump 옵션은 일부 바이트 수를 읽고 숫자 표현으로 변환하고 해당 바이트를 앞으로 이동하고 나중에 감지할 수 있도록 포인터를 설정하여 이를 수행함.
이 포인터는 오프셋 감지 끝 포인터 또는 doe_ptr 로 알려져 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_jump:&lt;bytes_to_convert&gt;,
  &lt;offset&gt; [, relative][, multiplier &lt;mult_value&gt;] \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, &lt;endian&gt;][, string,
  &lt;number_type&gt;][, align][, from_beginning][, from_end] \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, post_offset &lt;adjustment
  value&gt;][, dce][, bitmask &lt;bitmask_value&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes = 1 - 10<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset = -65535 to 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">mult_value = 0 - 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">post_offset = -65535 to 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask_value = 1 to 4 bytes hexadecimal
  value<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_convert<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷에서 가져올 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>없이 사용할 경우 허용되는 값은 <span lang="EN-US">1-10 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>와 함께 사용하는 경우 허용되는 값은 <span lang="EN-US">1, 2 </span>및 <span lang="EN-US">4 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">from_end </span>인수와 함께 사용하면 <span lang="EN-US">bytes_to_convert
  </span>는 <span lang="EN-US">0 </span>이 될 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">bytes_to_convert </span>가 <span lang="EN-US">0 </span>이면 추출된 값은 <span lang="EN-US">0 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">처리를 시작할 페이로드의 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">relative<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">마지막 패턴 일치에 상대적인 오프셋을 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">multiplier
  &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">계산된 바이트 수에 <span lang="EN-US">&lt;value&gt;
  </span>을 곱하고 해당 바이트 수를 앞으로 건너뜀<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">big<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터를 빅 엔디안으로 처리함<span lang="EN-US">. (</span>기본값<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">little<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터를 리틀 엔디안으로 처리함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">string<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터는 패킷에 문자열 형식으로 저장됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">hex<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">16 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dec<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">10 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">oct<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">8 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">align<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 바이트 수를 다음 <span lang="EN-US">32 </span>비트
  경계까지 반올림함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">from_beginning<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷의 현재 위치에서가 아니라 패킷 페이로드의 시작 부분부터 앞으로 건너뜀<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">from_end<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">점프는 페이로드의 끝에서 시작됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">post_offset
  &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">다른 점프 옵션이 적용된 후 <span lang="EN-US">&lt;value&gt;
  </span>바이트 수만큼 앞으로 또는 뒤<span lang="EN-US">(</span>음수 값의 양수<span lang="EN-US">)</span>로
  건너뜀<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">dce<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">DCE/RPC 2 </span>전처리기<span lang="EN-US">(preprocessor)</span>가
  변환할 값의 바이트 순서를 결정하게 하십시오<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span lang="EN-US"><span style="font-family: courier;">bitmask<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">bytes_to_convert </span>인수에
  <span lang="EN-US">AND </span>연산자를 적용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">결과는 마스크의 후행 <span lang="EN-US">0 </span>수와 동일한
  비트 수만큼 오른쪽 시프트됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 32770:34000 (content:"|00 01 86 B8|"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  00 00 01|"; distance:4; within:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_jump:4,
  12, relative, align; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:4,
  &gt;, 900, 20, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"statd
  format string buffer overflow";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (content:"Begin"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_jump:0,
  0, from_end, post_offset -6; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"end..";
  distance:0; within:5; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"Content
  match from end of the payload";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (content:"catalog"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_jump:2,
  1, relative, post_offset 2, bitmask 0x03f0; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:2,
  =, 968, 0, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"Bitmask
  applied on the 2 bytes extracted for byte_jump";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (content:"catalog"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_jump:1,
  2, from_end, post_offset -5, bitmask 0x3c; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:1,
  =, 106, 0, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">msg:"Byte
  jump calculated from end of payload after bitmask applied";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.33 byte_extract



byte_extract 키워드는 길이 인코딩 프로토콜에 대한 규칙을 작성하는 데 유용한 또 다른 옵션임.
패킷 페이로드에서 몇 바이트를 읽어 변수에 저장됨.
이러한 변수는 하드 코딩된 값을 사용하는 대신 나중에 규칙에서 참조할 수 있음.



노트 : </br>
규칙당 2개의 byte_extract 변수만 생성할 수 있음. </br>
동일한 규칙에서 여러 번 재사용할 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center"><table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_extract:&lt;bytes_to_extract&gt;,
  &lt;offset&gt;, &lt;name&gt; [, relative] \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, multiplier &lt;multiplier value&gt;][,
  &lt;endian&gt;][, string][, hex][, dec][, oct] \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, align &lt;align value&gt;][, dce][,
  bitmask &lt;bitmask&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_extract = 1 - 10<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">operator = ’&lt;’ | ’=’ | ’&gt;’ |
  ’&lt;=’ | ’&gt;=’ | ’&amp;’ | ’ˆ’<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">value = 0 - 4294967295<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset = -65535 to 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask_value = 1 to 4 byte hexadecimal
  value<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_convert<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷에서 가져올 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">처리를 시작할 페이로드의 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">name<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변수의 이름임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">다른 규칙 옵션에서 변수를 참조하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">relative<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">마지막 패턴 일치에 상대적인 오프셋을 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">multiplier
  &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷에서 읽은 바이트에 <span lang="EN-US">&lt;value&gt;
  </span>을 곱하고 그 숫자를 변수에 저장함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">big<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터를 빅 엔디안으로 처리함<span lang="EN-US">. (</span>기본값<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">little<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터를 리틀 엔디안으로 처리함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">DCE/RPC 2 </span>전처리기<span lang="EN-US">(preprocessor)</span>가
  변환할 값의 바이트 순서를 결정하십시오<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 옵션이 작동하려면<span lang="EN-US"> DCE/RPC 2 </span>전처리기가
  활성화되어야 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">string<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터는 패킷에 문자열 형식으로 저장됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">hex<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">16 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dec<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">10 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">oct<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 문자열 데이터는 <span lang="EN-US">8 </span>진수로
  표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">align
  &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">변환된 바이트 수를 다음 <span lang="EN-US">&lt;value&gt;
  </span>바이트 경계까지 반올림함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">&lt;value&gt; </span>은 <span lang="EN-US">2 </span>또는 <span lang="EN-US">4 </span>일 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">인수를 추출하기 위해 바이트 값에 <span lang="EN-US">AND </span>연산자를
  적용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">결과는 마스크의 후행 <span lang="EN-US">0 </span>수와 동일한
  비트 수만큼 오른쪽 시프트함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

byte_extract 규칙 옵션은 자체적으로 아무것도 감지하지 않음.
다른 규칙 옵션에서 사용할 패킷 데이터를 추출하는 데 사용됨.
다음은 byte_extract 변수를 사용할 수 있는 위치 목록 :

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>바이트 추출 변수를 사용하는 기타 옵션 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">규칙
  옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">변수를
  취하는 인수<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">content/uricontent<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset, depth, distance, within<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">byte_test<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset, value<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">byte_jump<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">isdataat<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는
  두 개의 변수를 사용하여 다음을 수행함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">• 오프셋<span lang="EN-US"> 0</span>의 바이트에서 문자열의 오프셋을 읽음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">• 오프셋<span lang="EN-US"> 1</span>의 바이트에서 문자열의 깊이를 읽음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">• 이
  값을 사용하여 패턴 일치를 더 작은 영역으로 제한함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (byte_extract:1, 0, str_offset; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_extract:1,
  1, str_depth; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"bad
  stuff"; offset:str_offset; depth:str_depth; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"Bad
  Stuff detected within field";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (content:"|04 63 34 35|"; offset:4;
  depth:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_extract:
  2, 0, var_match, relative, bitmask 0x03ff; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:
  2, =, var_match, 2, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">msg:"Byte
  test value matches bitmask applied on bytes extracted";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.34 byte_math



추출된 값과 지정된 값 또는 기존 변수에 대해 수학적 연산을 수행하고 결과를 새 결과 변수에 저장함.
이러한 결과 변수는 하드 코딩된 값을 사용하는 대신 나중에 규칙에서 참조할 수 있음.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_math:bytes &lt;bytes_to_extract&gt;,
  offset &lt;offset_value&gt;, oper &lt;operator&gt;,<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rvalue &lt;r_value&gt;, result
  &lt;result_variable&gt; [, relative]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, endian &lt;endian&gt;] [, string
  &lt;number type&gt;][, dce]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[, bitmask &lt;bitmask_value&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_extract = 1 - 10<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">operator = ’+’ | ’-’ | ’*’ | ’/’ |
  ’&lt;&lt;’ | ’&gt;&gt;’<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">r_value = 0 - 4294967295 | byte extract
  variable<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset_value = -65535 to 65535<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask_value = 1 to 4 byte hexadecimal
  value<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">result_variable = Result Variable name<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bytes_to_extract<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">패킷에서 가져올 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>없이 사용할 경우 허용되는 값은 <span lang="EN-US">1-10 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dce </span>와 함께 사용하는 경우 허용되는 값은 <span lang="EN-US">1, 2 </span>및 <span lang="EN-US">4 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">&lt;&lt; </span>또는 <span lang="EN-US">&gt;&gt; </span>연산자와
  함께 사용하는 경우 허용되는 값은 <span lang="EN-US">1-4 </span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">oper<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">추출된 값에 대해 수행할 수학적 연산이 허용된 연산자 <span lang="EN-US">: <o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">+, -, *, /, &lt;&lt;, &gt;&gt;<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rvalue<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">수학적 연산을 사용할 값임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">처리를 시작할 페이로드의 바이트 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">relative<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">마지막 패턴 일치에 상대적인 오프셋을 사용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">endian<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">읽고 있는 번호의 엔디안 유형<span lang="EN-US"> : <o:p></o:p></span></span></p><p class="MsoNoSpacing"><span style="font-family: courier;">•</span><span lang="EN-US" style="font-family: courier;"> big - </span><span style="font-family: courier;">데이터를 빅 엔디안으로
  처리함</span><span lang="EN-US" style="font-family: courier;">. (</span><span style="font-family: courier;">기본값</span><span lang="EN-US" style="font-family: courier;">).</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> little - </span>데이터를 <span lang="EN-US">little endian</span>으로 처리함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">string<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터는 패킷에 문자열 형식으로 저장됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">number
  type<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">읽을 번호 유형<span lang="EN-US"> : <o:p></o:p></span></span></p><p class="MsoNoSpacing"><span style="font-family: courier;">•</span><span lang="EN-US" style="font-family: courier;"> hex - </span><span style="font-family: courier;">변환된 문자열 데이터가</span><span lang="EN-US" style="font-family: courier;"> 16 </span><span style="font-family: courier;">진수로 표시됨</span><span lang="EN-US" style="font-family: courier;">.</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> dec - </span>변환된 문자열 데이터가<span lang="EN-US"> 10 </span>진수로 표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> oct - </span>변환된 문자열 데이터가<span lang="EN-US"> 8 </span>진수로 표시됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">DCE/RPC 2 </span>전처리기<span lang="EN-US">(preprocessor)</span>가
  변환할 값의 바이트 순서를 결정하게 하십시오<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="left" class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bitmask<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">추출된 바이트에 <span lang="EN-US">AND </span>연산자를
  적용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">결과는 마스크의 후행 <span lang="EN-US">0 </span>수와 동일한
  비트 수만큼 오른쪽 시프트됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>바이트 수학 결과 변수를 사용하는 기타 규칙 옵션 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">규칙
  옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">결과
  변수를 받는 인수<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">content<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset, depth, distance, within<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">byte_test<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset, value<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">byte_jump<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">isdataat<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"Perform
  Arithmetic Operation on the extracted bytes"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  04 93 F3|"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  00 00 07|"; distance:4; within:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_math:bytes
  4, offset 0, oper +, rvalue 248, result var, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:4,
  &gt;, var, 2, relative;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $EXTERNAL_NET any -&gt; $HOME_NET any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"Bitwise
  shift operator"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"|00
  00 00 07|"; distance:4; within:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_extract:
  1, 0, extracted_val, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_math:
  bytes 1, offset 2, oper &gt;&gt;, rvalue extracted_val, result var, relative;
  \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:2,
  =, var, 0, relative;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1234 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(content:
  "Packets start"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_math:
  bytes 2, offset 0, oper -, rvalue 100, result var, relative, bitmask 0x7FF0;
  \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:
  "Packets end"; distance: 2; within var; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"Content
  match with bitmask applied to the bytes extracted";)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 1235 \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(byte_extract:
  4, 3, extracted_val, relative; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_math:
  bytes 5, offset 0, oper +, rvalue extracted_val, result var, string hex; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">byte_test:5,
  =, var, 4, string, hex; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">msg:"String
  operator used with math rule option";)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.35 ftpbounce

- ftpbounce 키워드는 FTP bounce 공격을 감지함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ftpbounce;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $EXTERNAL_NET any -&gt; $HOME_NET 21 (msg:"FTP PORT bounce
  attempt"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flow:to_server,established;
  content:"PORT"; nocase; ftpbounce; pcre:"/ˆPORT/smi";\<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">classtype:misc-attack;
  sid:3441; rev:1;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.36 asn1



ASN.1 탐지 플러그인은 패킷 또는 패킷의 일부를 디코딩하고 다양한 악성 인코딩을 찾음.
'asn1' 옵션에 여러 옵션을 사용할 수 있으며 암시적 논리의 부울 OR 임.
따라서 인수 중 하나라도 참으로 평가되면 전체 옵션이 참으로 평가됨.
ASN.1 옵션은 좀 더 동적인 유형 감지뿐만 아니라 프로그래밍 방식 감지 기능을 제공함.
옵션에 인수가 있는 경우 옵션과 인수는 공백이나 쉼표로 구분됨.
선호하는 사용법은 옵션과 인수 사이에 공백을 사용하는 것임.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">asn1:[bitstring_overflow][,
  double_overflow][, oversize_length &lt;value&gt;][, absolute_offset
  &lt;value&gt;|relative_of<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">bitstring_overflow<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">원격으로 악용될 수 있는 것으로 알려진 유효하지 않은 비트 문자열 인코딩을 감지함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">double_overflow<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">표준 버퍼보다 큰 이중 <span lang="EN-US">ASCII </span>인코딩을 감지함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">이것은 <span lang="EN-US">Microsoft </span>에서 악용 가능한 기능으로 알려져 있지만 현재 어떤 서비스가
  악용될 수 있는지는 알 수 없음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">oversize_length &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">ASN.1 </span>유형 길이를 제공된 인수와 비교함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">구문은 <span lang="EN-US">"oversize_length 500" </span>과 같음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">즉<span lang="EN-US">, ASN.1 </span>유형이 <span lang="EN-US">500 </span>보다 크면
  이 키워드가 <span lang="EN-US">true </span>로 평가됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">이 키워드에는 비교할 길이를 지정하는 하나의 인수가 있어야 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">absolute_offset &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">이것은 패킷 시작으로부터의 절대 오프셋임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">예를 들어 <span lang="EN-US">snmp </span>패킷을 디코딩하려면 <span lang="EN-US">"absolute_offset
  0" </span>이라고 말하면 됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">absolute_offset </span>에는 오프셋 값이라는 하나의 인수가 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">오프셋은 양수 또는 음수일 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">relative_offset &lt;value&gt;<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 336.2pt;" width="448">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">이것은 마지막 컨텐츠 일치<span lang="EN-US">, pcre </span>또는 <span lang="EN-US">byte_jump
  </span>의 상대적 오프셋임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">relative_offset </span>에는 오프셋 번호라는 하나의 인수가 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">따라서 콘텐츠<span lang="EN-US"> "foo"</span>바로 다음에<span lang="EN-US"> ASN.1 </span>시퀀스 디코딩을 시작하려면 <span lang="EN-US">'content:"foo";
  asn1:bitstring_overflow, relative_offset 0' </span>를 지정함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">오프셋 값은 양수 또는 음수일 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  udp any any -&gt; any 161 (msg:"Oversize SNMP Length"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">asn1:oversize_length
  10000, absolute_offset 0;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 80 (msg:"ASN1 Relative Foo";
  content:"foo"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">asn1:bitstring_overflow,
  relative_offset 0;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 5.37 cvs



CVS 감지 플러그인은 Bugtraq-10384, CVE-2004-0396, "Malformed Entry Modified and Unchanged flag insertion" 를 감지하는 데 도움이 됨. 
기본 CVS 서버 포트는 2401 및 514 이며 스트림 재조립을 위한 기본 포트에 포함됨.

</br>

노트 : </br>
이 플러그인은 암호화된 세션은 감지할 수 없음. </br>
예를 들어 SSH 서비스와 일반적으로 포트 22번에 대해서 감지할 수 없음.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">cvs:&lt;option&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span lang="EN-US"><span style="font-family: courier;">invalid-entry<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">CVS 1.11.15 </span>및 이전 버전에서 힙 오버플로우 및 잘못된 포인터 역참조를 유발하는
  잘못된 항목 문자열을 찾음<span lang="EN-US">. (CVE-2004-0396 </span>참조<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 2401 (msg:"CVS Invalid-entry"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flow:to_server,established;
  cvs:invalid-entry;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 5.38 dce_iface
생략





### 5.39 dce_opnum
생략





### 5.40 dce_stub_data
생략





### 5.41 sip_method
생략





### 5.42 sip_stat_code
생략





### 5.43 sip_header
생략





### 5.44 sip_body
생략





### 5.45 gtp_type
생략





### 5.46 gtp_info
생략





### 5.47 gtp_version
생략





### 5.48 ssl_version
생략





### 5.49 ssl_state
생략


### 5.50 Payload Detection Quick Reference

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>페이로드 감지 규칙 옵션 키워드 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">키워드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">content<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">content </span>키워드를 통해 사용자는 패킷 페이로드에서 특정 컨텐츠를 검색하고
  해당 데이터를 기반으로 응답을 트리거하는 규칙을 설정할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rawbytes<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">rawbytes </span>키워드를 사용하면 규칙에서 전처리기가 수행한 디코딩을 무시하고
  원시 패킷 데이터를 볼 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">depth<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">depth </span>키워드를 사용하면 규칙 작성기가 패킷 <span lang="EN-US">Snort </span>가 지정된 패턴을 검색해야 하는 거리를 지정할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">offset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">offset </span>키워드를 사용하면 규칙 작성기가 패킷 내에서 패턴 검색을 시작할
  위치를 지정할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">distance<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">distance </span>키워드를 사용하면 규칙 작성자가 이전 패턴 일치의 끝을 기준으로
  지정된 패턴을 검색하기 전에 <span lang="EN-US">Snort </span>가 무시해야 하는 패킷의 거리를 지정할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">within<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">within </span>키워드는<span lang="EN-US"> content </span>키워드를
  사용하여 패턴 일치 사이에 최대 <span lang="EN-US">N </span>바이트가 있는지 확인하는 내용 수정자임<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">uricontent<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">Snort </span>규칙 언어의 <span lang="EN-US">uricontent
  </span>키워드는 정규화된 요청 <span lang="EN-US">URI </span>필드를 검색함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">isdataat<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">isdataat </span>키워드는 페이로드의 지정된 위치에 데이터가 있는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">pcre<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">pcre </span>키워드를 사용하면 <span lang="EN-US">perl </span>호환
  정규식을 사용하여 규칙을 작성할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_test<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">byte_test </span>키워드는 특정 값<span lang="EN-US">(</span>연산자
  포함<span lang="EN-US">)</span>에 대해 바이트 필드를 테스트함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">byte_jump<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">byte_jump </span>키워드를 사용하면 규칙이 데이터 일부의 길이를 읽은 다음 패킷에서
  해당 길이를 건너 뛸 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ftpbounce<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">ftpbounce </span>키워드는<span lang="EN-US"> FTP bounce </span>공격을
  감지함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">asn1<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">asn1 </span>탐지 플러그인은 패킷 또는 패킷의 일부를 디코딩하고 다양한 악성
  인코딩을 찾음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">cvs<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">cvs </span>키워드는 유효하지 않은 항목 문자열을 감지함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce_iface<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce_opnum<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dce_stub_data<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sip_method<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sip_stat_code<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sip_header<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sip_boy<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">gtp_type<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">gtp_info<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">gtp_version<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;">생략<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>



## (6) Non-Payload 감지 규칙 옵션
### 6.1 fragoffset


fragoffset 키워드를 사용하면 IP 조각 오프셋 필드를 10 진수 값과 비교할 수 있음.
IP 세션의 모든 첫 번째 조각을 포착하려면 fragbits 키워드를 사용하고 fragoffset 0 과 함께 More fragments 옵션을 찾을 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fragoffset:[!|&lt;|&gt;]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  ip any any -&gt; any any \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">(msg:"First
  Fragment"; fragbits:M; fragoffset:0;)</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 6.2 ttl



ttl 키워드는 IP 수명 값을 확인하는 데 사용됨.
이 옵션 키워드는 traceroute 시도 감지에 사용하기 위한 것임.
이 키워드는 0 에서 255 까지의 숫자를 사용함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ttl:[&lt;, &gt;, =, &lt;=, &gt;=]&lt;number&gt;;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ttl:[&lt;number&gt;]-[&lt;number&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 3</span>보다 작은<span lang="EN-US"> TTL </span>값을 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:&lt;3;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 3</span>과<span lang="EN-US"> 5 </span>사이의 수명 값을 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:3-5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 0</span>에서<span lang="EN-US"> 5 </span>사이의<span lang="EN-US"> TTL </span>값을
  확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:-5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 5</span>에서<span lang="EN-US"> 255 </span>사이의 수명 값을 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:5-;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다른
  몇 가지 예는 다음과 같음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:&lt;=5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:&gt;=5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:=5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다음
  예제는<span lang="EN-US"> ttl </span>키워드에서 허용되지 않음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:=&gt;5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ttl:=&lt;5;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">ttl:5-3;</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.3 tos

tos 키워드는 특정 값에 대한 IP TOS 필드를 확인하는 데 사용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">tos:[!]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는<span lang="EN-US"> 4</span>가 아닌<span lang="EN-US"> tos </span>값을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">tos:!4;</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.4 id



- id 키워드는 특정 값에 대한 IP ID 필드를 확인하는 데 사용됨.
- 일부 도구(Exploits, Scanner, 기타 프로그램)는 특히 다양한 목적으로 이 필드를 설정함.
 - 예를 들어, 31337 값은 일부 해커에게 매우 인기가 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">id:&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는
  <span lang="EN-US">IP ID 31337 </span>을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">d:31337;</span></i><span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.5 ipopts



ipopts 키워드는 특정 IP 옵션이 있는지 확인하는 데 사용됨.

다음 옵션을 확인할 수 있음.

   rr - 경로 기록 </br>
   eol - 목록 끝 </br>
   nop - 작업 없음 </br>
   ts - 타임 스탬프 </br>
   sec - IP 보안 </br>
   esec - IP 확장 보안 </br>
   lsrr - 느슨한 소스 라우팅 </br>
   lsrre - 느슨한 소스 라우팅 (MS99-038 및 CVE-1999-0909 의 경우) </br>
   ssrr - 엄격한 소스 라우팅 </br>
   satid - 스트림 식별자 </br>
   any - 모든 IP 옵션 설정 </br>

</br>

IP 옵션에 대해 가장 자주 관찰되는 것은 광범위하고 널리 퍼진 인터넷 어플리케이션에서 사용되지 않는 엄격하고 느슨한 소스 라우팅임.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ipopts:&lt;rr|eol|nop|ts|sec|esec|lsrr|lsrre|ssrr|satid|any&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는
  느슨한 소스 라우팅의<span lang="EN-US"> IP </span>옵션을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ipopts:lsrr;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


경고 : </br>
규칙 당 하나의 ipopts 키워드만 지정할 수 있음.


### 6.6 fragbits

fragbits 키워드는 단편화 및 예약된 비트가 IP 헤더에 설정되어 있는지 확인하는 데 사용됨.
다음 비트를 확인할 수 있음.
   M - 더 많은 조각
   D - 조각화하지 마십시오.
   R - 예약된 비트



다음 수정자를 설정하여 일치 기준을 변경할 수 있음.
   \+ - 지정된 비트 및 다른 비트에서 일치
   \* - 지정된 비트가 설정된 경우 일치
   ! - 지정된 비트가 설정되지 않은 경우 일치

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fragbits:[+*!]&lt;[MDR]&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는<span lang="EN-US"> More Fragments </span>비트와<span lang="EN-US"> Do not Fragment </span>비트가
  설정되어 있는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">fragbits:MD+;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.7 dsize



dsize 키워드는 패킷 페이로드 크기를 테스트하는 데 사용됨.
버퍼 오버플로우(buffer overflow)를 유발할 수 있는 비정상적인 크기의 패킷을 확인하는 데 사용할 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dsize:min&lt;&gt;max;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dsize:[&lt;|&gt;]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는<span lang="EN-US"> 300 </span>에서<span lang="EN-US"> 400 </span>바이트<span lang="EN-US">(</span>포함<span lang="EN-US">) </span>사이의<span lang="EN-US"> dsize</span>를 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">dsize:300&lt;&gt;400;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


경고 : </br>
세분화는 HTTP 와 같은 TCP 기반 프로토콜에서 dsize 의 안정성을 떨어뜨림. </br>
또한, 프로토콜 인식 플러시(PAF - Protocol Aware Flushing)가 이 패킷을 메시지의 시작으로 표시하지 않는 한 페이로드의 크기에 관계없이 스트림 재구축 된 패킷에서 dsize 가 실패함.





### 6.8 flags



flags 키워드는 특정 TCP 플래그 비트가 있는지 확인하는 데 사용됨.
다음 비트를 확인할 수 있음.
   F - FIN \(완료, TCP 플래그 바이트의 LSB)
   S - SYN \(시퀀스 번호 동기화)
   R - RST \(재설정)
   P - PSH \(푸시)
   A - ACK \(승인)
   U - URG \(긴급)
   C - CWR \(혼잡 창 감소, TCP 플래그 바이트의 MSB)
   E - ECE \(ECN-Echo, SYN이면 ECN 가능하며 그렇지 않으면 IP 헤더의 CE 플래그가 설정됨)
   0 - TCP 플래그가 설정되지 않음



다음 수정자를 설정하여 일치 기준을 변경할 수 있음.

\+ - 지정된 비트 및 다른 비트에서 일치

\* - 지정된 비트가 설정된 경우 일치

! - 지정된 비트가 설정되지 않은 경우 일치



SYN 패킷이 CWR 및 ECE 세트와 함께 전송되는 ECN 같은 세션 시작 패킷에 대한 쓰기 규칙을 처리하기 위해 마스크 앞에 쉼표를 붙여 옵션 마스크를 지정할 수 있음.

예약된 비트의 값에 관계없이 syn 비트만 있는 패킷을 찾으려면 규칙은 S, CE 플래그 값을 확인할 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flags:[!|*|+]&lt;FSRPAUCE0&gt;[,&lt;FSRPAUCE&gt;];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예제는<span lang="EN-US"> CWR(</span>예약 비트<span lang="EN-US"> 1) </span>및<span lang="EN-US">
  ECN(</span>예약 비트<span lang="EN-US"> 2) </span>을 무시하고<span lang="EN-US"> SYN </span>및<span lang="EN-US"> FIN </span>비트만 설정되었는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (flags:SF,CE;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


노트 : </br>
RFC 3168, "The Addition of Explicit Congestion Notification \(ECN) to IP" 와 일치하도록 예약된 비트 '1' 및 '2' 가 각각 'C' 및 'E' 로 대체됨. </br>
'1' 및 '2' 의 이전 값은 여전히 플래그 키워드에 유효하지만 현재는 더 이상 사용되지 않음. </br>





### 6.9 flow

flow 키워드는 세션 추적과 함께 사용됨.
규칙을 트래픽 흐름의 특정 방향에만 적용 할 수 있음.
이렇게 하면 규칙이 클라이언트 또는 서버에만 적용됨.
이를 통해 웹 페이지를 보는 $HOME_NET 클라이언트와 관련된 패킷을 $HOME_NET 에서 실행되는 서버와 구별 할 수 있음.
설정된 키워드는 설정된 TCP 연결을 표시하기 위해 여러 위치에서 사용되는 flags:+A 를 대체함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>옵션 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">to_client<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">A </span>에서<span lang="EN-US"> B </span>로 서버
  응답을 트리거함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">to_server<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">A </span>에서<span lang="EN-US"> B </span>로 클라이언트
  요청에 대해 트러거함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">from_client<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">A </span>에서<span lang="EN-US"> B </span>로 클라이언트
  요청에 대해 트러거함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">from_server<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">A </span>에서<span lang="EN-US"> B </span>로 서버
  응답을 트리거함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">established<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">설정된<span lang="EN-US"> TCP </span>연결에서만 트리거됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">not_established<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">TCP </span>연결이 설정되지 않은 경우에만 트리거됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">stateless<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">스트림 프로세서의 상태에 관계없이 트리거됨<span lang="EN-US">.
  (</span>시스템 충돌을 유발하도록 설계된 패킷에 유용함<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">no_stream<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">재구축된 스트림 패킷에서 트리거하지 마십시오<span lang="EN-US">.
  (dsize </span>및<span lang="EN-US"> stream5 </span>에 유용<span lang="EN-US">)<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">only_stream<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">재구축된 스트림 패킷에서만 트리거됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">no_frag<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">재구축된 조각 패킷에서 트리거하지 마십시오<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">only_frag<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">재구축된 조각 패킷에서만 트리거됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flow:[(established|not_established|stateless)]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[,(to_client|to_server|from_client|from_server)]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[,(no_stream|only_stream)]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">[,(no_frag|only_frag)];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp !$HOME_NET any -&gt; $HOME_NET 21 (msg:"cd incoming detected";
  \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flow:from_client;
  content:"CWD incoming"; nocase;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp !$HOME_NET 0 -&gt; $HOME_NET 0 (msg:"Port 0 TCP traffic"; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flow:stateless;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### 6.10  flowbits



flowbits 키워드는 세션 전처리기의 대화 추적과 함께 사용됨.
규칙이 전송 프로토콜 세션 동안 상태를 추적할 수 있도록 함.
flowbits 옵션은 규칙이 일반적으로 어플리케이션 프로토콜의 상태를 추적할 수 있도록 허용하므로 TCP 세션에 가장 유용함.
flowbits 와 관련된 몇 가지 키워드가 있음.
대부분의 옵션에는 검사중인 특정 상태에 대한 사용자 정의 이름이 필요함.
일부 키워드는 그룹 이름을 사용함.
그룹 이름이 지정되지 않은 경우 flowbits 는 기본 그룹에 속함.
특정 flowbits 는 둘 이상의 그룹에 속할 수 있음.
flowbits 이름과 그룹 이름은 마침표, 대시 및 밑줄을 포함한 영숫자 문자열로 제한되어야 함.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>일반적인 형식 <span lang="EN-US">&gt;</span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:[set|setx|unset|toggle|isset|isnotset|noalert|reset][,
  &lt;bits/bats&gt;][, &lt;GROUP_NAME&gt;];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bits ::= bit[|bits]<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">bats ::= bit[&amp;bats]<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>일반적인 사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any 143 -&gt; any any (msg:"IMAP login";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"OK
  LOGIN"; flowbits:set,logged_in;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:noalert;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 143 (msg:"IMAP LIST";
  content:"LIST";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:isset,logged_in;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">set<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">현재 흐름에 대해 지정된 상태를 설정하고<span lang="EN-US">
  GROUP_NAME </span>이 지정되면 그룹에 할당함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">setx<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">현재 흐름에 대해 지정된 상태를 설정하고 그룹의 다른 상태를 지움<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">unset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">현재 흐름에 대해 지정된 상태를 설정 해제함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">toggle<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 모든 상태에 대해 상태가 설정되지 않은 경우 지정된 상태를 설정하고
  상태가 설정된 경우 설정을 해제함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">isset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 상태가 설정되었는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">isnotset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 상태가 설정되지 않았는지 확인함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">noalert<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">나머지 검색 옵션에 관계없이 규칙이 경고를 생성하지 않도록 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">reset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">지정된 흐름의 모든 상태를 재설정함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### **set**

이 키워드는 특정 흐름에 대해 그룹화할 비트를 설정함.
그룹이 지정되지 않은 경우 기본 그룹을 설정함.
이 키워드는 항상 true 를 반환함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:set,bats[,group]<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">첫 번째
  규칙은 <span lang="EN-US">doc </span>그룹에서<span lang="EN-US"> bit1 </span>을 설정하고 두 번째
  규칫은 <span lang="EN-US">doc </span>그룹에서<span lang="EN-US"> bit2 </span>및<span lang="EN-US"> bit3 </span>을 설정함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">따라서
  <span lang="EN-US">doc </span>그룹에는<span lang="EN-US"> bit1, bit2, bit3 </span>이 설정되어
  있음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:set,bit1,doc;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:set,bit2&amp;bit3,doc;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### **setx**

- 이 키워드는 그룹화할 비트를 독점적으로 설정함.
- 이것은 그룹의 다른 비트를 지움.
- 그룹이 있어야 함.
- 이 키워드는 항상 true 를 반환함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:setx,bats,group<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">첫 번째
  규칙은 <span lang="EN-US">doc </span>그룹에서 <span lang="EN-US">bit1 </span>을 설정하고 두 번째
  규칙은 <span lang="EN-US">doc </span>그룹에서<span lang="EN-US"> bit2 </span>및<span lang="EN-US"> bit3 </span>을 설정함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">따라서<span lang="EN-US"> bit1 </span>은 규칙<span lang="EN-US">2 </span>에 의해 지워지므로 <span lang="EN-US">doc </span>그룹에는<span lang="EN-US"> bit2 </span>및<span lang="EN-US">
  bit3 </span>이 설정되어 있음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  setx, bit1, doc<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  setx, bit2&amp;bit3, doc<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### **unset**

이 키워드는 특정 흐름에 대해 지정된 비트를 지우거나 그룹의 모든 비트를 지움. \(그룹이 있어야 함)
이 키워드는 항상 true 를 반환함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:unset,bats<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:unset,all,group<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">bit1
  </span></i><i>을 지움<span lang="EN-US">.<o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  unset, bit1<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">bit1
  </span></i><i>및<span lang="EN-US"> bit2 </span>를 지움<span lang="EN-US">.<o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  unset, bit1&amp;bit2<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">doc
  </span></i><i>그룹의 모든 비트가 지워짐<span lang="EN-US">.<o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  unset, all, doc<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### **toggle**

flowbit 가 설정되어 있으면 설정을 해제함.
설정되지 않은 경우 설정하십시오.
지정된 모든 비트를 토글(toggle)하거나 1그룹의 모든 비트를 토글함. \(그룹이 있어야 함)
이 키워드는 항상 true 를 반환함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:toggle,bats<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:toggle,all,group<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙
  이전에<span lang="EN-US"> bit1 </span>이<span lang="EN-US"> 0 </span>이고<span lang="EN-US"> bit2 </span>가<span lang="EN-US"> 1 </span>이면 이 규칙 이후에<span lang="EN-US"> bit1 </span>은<span lang="EN-US"> 1 </span>이고<span lang="EN-US"> bit2 </span>은<span lang="EN-US"> 0 </span>임<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:
  toggle, bit1&amp;bit2<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">위에서
  설명한대로 <span lang="EN-US">doc </span>그룹의 모든 비트를 토글함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flowbits:toggle,all,doc<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


### **isset**

이 키워드는 설정되었는지 확인하기 위해 비트 또는 여러 비트를 확인함.
다음 구문에 따라 true 또는 false 를 반환함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flowbits:isset, bits =&gt; </span>비트가
  설정되었는지 확인<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flowbits:isset, bats =&gt; </span>모든
  비트가 설정되었는지 확인<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flowbits:isset, any, group =&gt; </span>그룹의
  비트가 설정되었는지 확인<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flowbits:isset, all, group =&gt; </span>그룹의
  모든 비트가 설정되었는지 확인<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:isnotset,
  bit1|bit2 =&gt; bit1 </span></i><i>또는<span lang="EN-US"> bit2 </span>가 설정되면<span lang="EN-US"> true </span>를 반환<span lang="EN-US"><o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:isnotset,
  bit1&amp;bit2 =&gt; bit1 </span></i><i>과<span lang="EN-US"> bit2 </span>가 모두 설정된 경우<span lang="EN-US"> true </span>를 반환하고 그렇지 않으면<span lang="EN-US"> false </span>를 반환<span lang="EN-US"><o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:isnotset,
  any, doc =&gt; doc </span></i><i>그룹의
  비트가 설정되면<span lang="EN-US"> true </span>를 반환<span lang="EN-US"><o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:isnotset,
  all, doc =&gt; doc </span></i><i>그룹의
  모든 비트가 설정되면<span lang="EN-US"> true </span>를 반환<span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### **noalert**

이 키워드는 항상 false 를 반환함.
이를 통해 사용자는 경고를 생성하지 않고 비트를 설정, 설정 해제 및 토글하는 규칙을 작성할 수 있음.
이는 정상적인 트래픽에 비트를 설정하고 원치 않은 경고를 크게 줄이는 flowbit 규칙을 작성하는 데 가장 유용함.
이 키워드에 지정된 비트가 없음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:noalert;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### **reset**

이 키워드는 지정된 그룹이 없는 경우 지정된 흐름의 모든 상태를 재설정하고 그렇지 않으면 그룹의 모든 비트를 재설정함.
이것은 항상 true 를 반환함.
이 키워드에 지정된 비트가 없음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits:reset[,group]<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:reset
  =&gt; </span></i><i>흐름의
  모든 비트 재설정<span lang="EN-US"><o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">flowbits:
  reset, doc =&gt; doc </span></i><i>그룹의
  모든 비트 재설정<span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.11 seq



seq 키워드는 특정 TCP 시퀀스 번호를 확인하는 데 사용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">seq:&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> TCP </span>시퀀스 번호<span lang="EN-US"> 0 </span>을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">seq:0;</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.12 ack



ack 키워드는 특정 TCP 승인 번호를 확인하는 데 사용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ack:&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> TCP </span>승인 번호<span lang="EN-US"> 0 </span>을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">ack:0;</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 6.13 window



window 키워드는 특정 TCP 창 크기를 확인하는 데 사용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">window:[!]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> TCP </span>창 크기<span lang="EN-US"> 55808 </span>를 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">window:55808;</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 6.14 itype



itype 키워드는 특정 ICMP 유형 값을 확인하는 데 사용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icode:min&lt;&gt;max;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icode:[&lt;|&gt;]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 30 </span>보다 큰<span lang="EN-US"> ICMP </span>유형을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">itype:&gt;30;</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>



### 6.15 icode



icode 키워드는 특정 ICMP 코드 값을 확인하는 데 사용됨.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">itype:min&lt;&gt;max;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">itype:[&lt;|&gt;]&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>




첫 번째 형식의 <> 연산자는 지정된 범위(배타적) 내에서 ICMP 코드를 확인함.
즉, 최소값보다 크거나 최대값보다 작음.
최소값은 -1 이 될 수 있으므로 ICMP 코드 0 이 범위에 포함될 수 있음.
숫자 값은 0 에서 255 사이의 허용되는 ICMP 코드 값 및 기타 기준과 관련하여 검증됨.



icode:min<>max </br>
-1 <= min <= 254 </br>
1 <= max <= 256 </br>
(max - min) > 1 </br>

</br>

icode:number </br>
0 <= number <= 255 </br>

</br>

icode:<number </br>
1 <= number <= 256 </br>

</br>

icode:>number </br>
0 <= number <= 254 </br>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 30 </span>보다 큰<span lang="EN-US"> ICMP </span>코드를 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">icode:&gt;30;<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> 0 </span>보다 크고<span lang="EN-US"> 30 </span>보다 작은<span lang="EN-US">
  ICMP </span>코드를 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">icode:-1&lt;&gt;30;</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.16 icmp_id

icmp_id 키워드는 특정 ICMP ID 값을 확인하는 데 사용됨.
이것은 일부 비밀 채널 프로그램이 통신 할 때 정적 ICMP 필드를 사용하기 때문에 유용함.
이 특정 플러그인은 stacheldraht DDoS 에이전트를 감지하기 위해 개발됨.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icmp_id:&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는 <span lang="EN-US">ICMP ID 0 </span>을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">icmp_id:0;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.17 icmp_seq



icmp seq 키워드는 특정 ICMP 시퀀스 값을 확인하는 데 사용됨.
이것은 일부 비밀 채널 프로그램이 통신 할 때 정적 ICMP 필드를 사용하기 때문에 유용함.
이 특정 플러그인은 stacheldraht DDoS 에이전트를 감지하기 위해 개발됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icmp_seq:&lt;number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는 <span lang="EN-US">ICMP </span>시퀀스<span lang="EN-US"> 0 </span>을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">icmp_seq:0;<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.18 rpc



rpc 키워드는 SUNRPC CALL 요청에서 RPC 애플리케이션, 버전 및 프로시저 번호를 확인하는 데 사용됨.
와일드 카드는 ’\*’ 를 사용하여 버전 및 프로시저 번호 모두에 유효함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rpc:&lt;application number&gt;,
  [&lt;version number&gt;|*], [&lt;procedure number&gt;|*]&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다음 예제는<span lang="EN-US"> RPC </span>포트 맵<span lang="EN-US"> GETPORT </span>요청을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 111 (rpc:100000, *, 3;);<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


경고 : </br>
빠른 패턴 일치 엔진으로 인해 RPC 키워드는 일반 컨텐츠 일치를 사용하여 RPC 값을 찾는 것보다 느림.



### 6.19 ip_proto

ip_proto 키워드는 IP 프로토콜 헤더에 대한 검사를 허용함.
이름으로 지정할 수 있는 프로토콜 목록은 /etc/protocols 를 참조하십시오.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ip_proto:[!|&gt;|&lt;] &lt;name or
  number&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는<span lang="EN-US"> IGMP </span>트래픽을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  ip any any -&gt; any any (ip_proto:igmp;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.20 sameip



sameip 키워드를 사용하면 규칙에서 소스 IP 가 대상 IP 와 동일한 지 확인할 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sameip;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예에서는 소스<span lang="EN-US"> IP</span>와 대상<span lang="EN-US"> IP</span>가 동일한 트래픽을 찾음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  ip any any -&gt; any any (sameip;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 6.21 stream_reassemble



stream_reassemble 키워드를 사용하면 규칙이 일치하는 트래픽에서 TCP 스트림 재조립을 활성화 또는 비활성화할 수 있음.



노트 : </br>
stream_reassemble 옵션은 스트림 전처리기(Stream preprocessor)가 활성화된 경우에만 사용할 수 있음.

</br>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">stream_reassemble:&lt;enable|disable&gt;,
  &lt;server|client|both&gt;[, noalert][, fastpath];<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">• 선택적<span lang="EN-US"> noalert </span>매개 변수를
  사용하면 규칙이 일치할 때 경고를 생성하지 않음<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">• 선택적<span lang="EN-US"> fastpath </span>매개
  변수를 사용하면<span lang="EN-US"> Snort </span>가 나머지 연결을 무시함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">예를 들어<span lang="EN-US">, HTTP 200 Ok </span>응답 메시지가 표시 될 때 클라이언트 트래픽에 대한<span lang="EN-US">
  TCP </span>재조립을 비활성화하려면 다음을 사용함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">&nbsp;</span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any 80 -&gt; any any (flow:to_client, established; content:"200
  OK";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">stream_reassemble:disable,client,noalert;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>




### 6.22 stream_size



stream_size 키워드를 사용하면 규칙이 TCP 시퀀스 번호에 의해 결정된 대로 관찰된 바이트 수에 따라 트래픽을 일치시킬 수 있음.



노트 : </br>
stream_size 옵션은 스트림 전처리기(Stream preprocessor)가 활성화된 경우에만 사용할 수 있음.


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">stream_size:&lt;server|client|both|either&gt;,
  &lt;operator&gt;, &lt;number&gt;;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">operator </span>가 다음 중 하나인 경우<span lang="EN-US"> : <o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &lt; - </span>미만<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &gt; - </span>보다 큼<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> = - </span>같음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> != - </span>같지 않음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &lt;= - </span>작거나 같음<span lang="EN-US"><o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">•<span lang="EN-US"> &gt;= - </span>크거나 같음<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">예를 들어<span lang="EN-US">, </span>클라이언트 측에서<span lang="EN-US"> 6 </span>바이트 미만인 세션을 찾으려면 다음을 사용함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any any (stream_size:client,&lt;,6;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>



### 6.23 Non-Payload Detection Quick Reference

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>비 페이로드 감지 규칙 옵션 키워드 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">키워드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fragoffset<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">fragoffset </span>키워드를 사용하면<span lang="EN-US"> IP </span>조각
  오프셋 필드를<span lang="EN-US"> 10 </span>진수값과 비교할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ttl<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">ttl </span>키워드는<span lang="EN-US"> IP </span>수명값을
  확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">tos<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">tos </span>키워드는 특정 값에 대한<span lang="EN-US"> IP
  TOS </span>필드를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">id<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">id </span>키워드는 특정 값에 대한<span lang="EN-US"> IP
  ID </span>필드를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ipopts<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">ipopts </span>키워드는 특정<span lang="EN-US"> IP </span>옵션이
  있는지 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">fragbits<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">fragbits </span>키워드는 단편화 및 예약 된 비트가<span lang="EN-US"> IP </span>헤더에 설정되어 있는지 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">dsize<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">dsize </span>키워드는 패킷 페이로드 크기를 테스트하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flags<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flags </span>키워드는 특정<span lang="EN-US"> TCP </span>플래그
  비트가 있는지 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flow<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flow </span>키워드는 규칙이 트래픽 흐름의 특정 방향에만 적용되도록 허용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">flowbits<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">flowbits </span>키워드를 사용하면 규칙이 전송 프로토콜 세션 동안 상태를 추적할
  수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">seq<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">seq </span>키워드는 특정<span lang="EN-US"> TCP </span>시퀀스
  번호를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ack<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">ack </span>키워드는 특정<span lang="EN-US"> TCP </span>승인
  번호를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">window<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">window </span>키워드는 특정<span lang="EN-US"> TCP </span>창
  크기를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">itype<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">itype </span>키워드는 특정<span lang="EN-US"> ICMP </span>유형
  값을 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icode<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">icode </span>키워드는 특정<span lang="EN-US"> ICMP </span>코드
  값을 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icmp_id<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">icmp_id </span>키워드는 특정<span lang="EN-US"> ICMP ID </span>값을
  확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">icmp_seq<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">icmp_seq </span>키워드는 특정<span lang="EN-US"> ICMP </span>시퀀스
  값을 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">rpc<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">rpc </span>키워드는<span lang="EN-US"> SUNRPC CALL </span>요청에서<span lang="EN-US"> RPC </span>애플리케이션<span lang="EN-US">, </span>버전 및 프로시저 번호를 확인하는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">ip_proto<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">ip_proto </span>키워드는<span lang="EN-US"> IP </span>프로토콜
  헤더에 대한 검사를 허용함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">sameip<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" valign="top" width="494">
  <p class="MsoNormal" style="line-height: normal; margin-bottom: 0cm;"><span style="font-family: courier;"><span lang="EN-US">sameip </span>키워드를 사용하면 규칙에서 소스<span lang="EN-US"> IP </span>가
  대상<span lang="EN-US"> IP </span>와 동일한 지 확인할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

## (7) Post-Detection 규칙 옵션
### 7.1 logto


logto 키워드는이 규칙을 트리거하는 모든 패킷을 특수 출력 로그 파일에 기록하도록 Snort에 지시함.
이는 NMAP 활동, HTTP CGI 스캔 등과 같은 데이터를 결합하는 데 특히 유용함.
이 옵션은 Snort 가 바이너리 로깅 모드에 있을 때는 작동하지 않음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">logto:"filename";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


### 7.2 session



session 키워드는 TCP 세션에서 사용자 데이터를 추출하기 위해 작성됨.
사용자가 telnet, rlogin, ftp 또는 웹 세션에서 입력하는 내용을 보는 것이 매우 유용한 경우가 많음.
session 규칙 옵션에 대해 세 가지 사용 가능한 인수 키워드(printable, binary, all)가 있음.
printable 키워드는 사용자가 일반적으로 보거나 입력할 수 있는 데이터만 인쇄함.binary 키워드는 바이너리 형식으로 데이터를 인쇄함.all 키워드는 인쇄할 수 없는 문자를 16진수 문자으로 대체함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">session:[printable|binary|all];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">다음 예제는 텔넷 패킷에 인쇄 가능한
  모든 문자열을 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log
  tcp any any &lt;&gt; any 23 (session:printable;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">포트
  <span lang="EN-US">12345 </span>의<span lang="EN-US"> FTP </span>데이터 세션이 주어지면 페이로드
  바이트를 바이너리 형식으로 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">log
  tcp any any &lt;&gt; any 12345 (metadata:service ftp-data; session:binary;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


경고 : </br>
session 키워드를 사용하면 Snort 속도가 상당히 느려질 수 있으므로 부하가 많은 상황에서 사용해서는 안됨. </br>
session 키워드는 사후 처리 바이너리\(pcap) 로그 파일에 가장 적합함. </br>
binary 키워드는 어플리케이션 계층 아래의 프로토콜 헤더를 기록하지 않으며 스트림 재조립은 재조립 된 패킷이 기록 될 때 중복 데이터를 발생시킴. </br>





### 7.3 resp

resp 키워드는 문제가되는 세션을 종료하는 활성 응답을 활성화함.
resp 는 수동 또는 인라인 모드 모두에서 사용할 수 있음.





### 7.4 react



react 키워드를 사용하면 웹 페이지 또는 기타 컨텐츠를 클라이언트에 보낸 다음 연결을 닫는 것을 포함하는 활성 응답을 사용할 수 있음.
React는 수동 모드와 인라인 모드 모두에서 사용할 수 있음.





### 7.5 tag



tag 키워드를 사용하면 규칙에다가 규칙을 트리거 한 단일 패킷 이상을 기록 할 수 있음.
규칙이 트리거되면 소스 및 또는(and/or) 대상 호스트와 관련된 추가 트래픽에 태그가 지정됨.
태그가 지정된 트래픽이 기록되어 응답 코드 및 공격 후 트래픽을 분석 할 수 있음.
태그가 지정된 경고는 원래 경고와 동일한 출력 플러그인으로 전송되지만 이러한 특수 경고를 적절하게 처리하는 것은 출력 플러그인의 책임임.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">tag:host, &lt;count&gt;, &lt;metric&gt;,
  &lt;direction&gt;;<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">tag:session[, &lt;count&gt;,
  &lt;metric&gt;][, exclusive];<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


type </br>

</br>

• session - 규칙을 설정한 세션의 패킷 기록 </br>
• host - 태그를 활성화 한 호스트의 로그 패킷 \(\[방향] 수정자 사용)

</br>

count </br>
• \<integer> - 개수는 단위 수로 지정됨. 
단위는 \<metric> 필드에 지정됨.

</br>

metric </br>

</br>

• packets - \<count> 패킷 동안 host/session 에 태그를 지정 </br>
• seconds - \<count> 초 동안 host/session 에 태그를 지정 </br>
• bytes - \<count> 바이트 동안 host/session 에 태그를 지정 </br>

</br>

other </br>

• src - 초기 이벤트를 생성한 패킷에서 소스 IP 주소를 포함하는 패킷에 태그를 지정함. 호스트 유형이 사용되는 경우에만 관련됨. </br>
• dst - 초기 이벤트를 생성한 패킷에서 대상 IP 주소를 포함하는 패킷에 태그를 지정함. 호스트 유형이 사용되는 경우에만 관련됨. </br>
• exclusive - 첫 번째 일치 세션에서만 패킷에 태그를 지정함. 세션 유형이 사용되는 경우에만 관련됨. </br>

</br>

- 후속 경고나 이벤트 필터는 태그가 지정된 패킷이 기록되는 것을 방지하지 않음.
- 이후에 태그가 지정된 경고로 인해 제한이 재설정됨.



alert tcp any any <> 10.1.1.1 any \\              </br>
\(flowbits:isnotset,tagged; content:"foobar"; nocase; \            </br>
flowbits:set,tagged; tag:host,600,seconds,src;)



또한, 규칙에 packets 이외의 메트릭을 사용하는 태그 옵션이 있는 경우 seconds 또는 bytes 개수에 관계없이 태그가 지정된 패킷 수를 제한하는 데 tagged_packet_limit 가 사용됨.
기본 tagged_packet_limit 값은 256 이며 snort.conf 파일에서 구성 옵션을 사용하여 수정할 수 있음.태그 옵션에 packets 메트릭을 추가하고 개수를 0 으로 설정하여 특정 규칙에 대해 이 패킷 제한을 비활성화 할 수 있음. \(이는 snort.conf 의 tagged_packet_limit 옵션을 0 으로 설정하여 글로벌 규모로 수행할 수 있음)
이렇게하면 패킷이 seconds 또는 bytes 의 전체 양에 대해 태그가 지정되고 tagged_packet_limit에 의해 잘리지 않음. \(tag_packet_limit 는 seconds 또는 bytes 카운트가 높은 태그 규칙에 대해 고대역폭 센서에서 DoS 상황을 피하기 위해 도입됨)



alert tcp 10.1.1.4 any -> 10.1.1.1 any \\      </br>
\(content:"TAGMYPACKETS"; tag:host,0,packets,600,seconds,src;) </br>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 예는 텔넷 세션의 처음<span lang="EN-US"> 10 </span>초 또는 태그가 지정된 패킷 제한<span lang="EN-US">(</span>둘 중 먼저 오는 쪽<span lang="EN-US">)</span>을 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp any any -&gt; any 23 (flags:S,CE; tag:session,10,seconds;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i><span lang="EN-US">tag:host
  </span></i><i>에는 하나 이상의 개수와 메트릭이 필요하지만 메트릭없이 배타적인
  <span lang="EN-US">tag:session </span>을 사용하여 이와 같은 전체 세션을 얻을 수 있음<span lang="EN-US">.<o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">pass
  tcp any any -&gt; 192.168.1.1 80 (flags:S; tag:session,exclusive;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>

### 7.6 replace



replace 키워드는 Snort 가 이전에 일치하는 컨텐츠에 주어진 문자열로 바꾸도록 하는 기능으로 인라인 모드에서 사용함.
새 문자열과 교체할 내용은 모두 길이가 같아야 함.
규칙 내에서 컨텐츠당 하나번 여러 개의 교체가 있을 수 있음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">replace:"&lt;string&gt;";<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>




### 7.7 detection_filter

탐지 필터는 규칙이 이벤트를 생성하기 전에 소스 또는 대상 호스트가 초과해야 하는 비율을 정의함.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">detection_filter: \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">track &lt;by_src|by_dst&gt;, \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">count &lt;c&gt;, seconds &lt;s&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">track<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">by_src|by_dst<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">속도는 소스<span lang="EN-US"> IP </span>주소 또는 대상<span lang="EN-US"> IP </span>주소로 추적됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">즉<span lang="EN-US">, </span>각 고유 소스<span lang="EN-US"> IP </span>주소 또는 각 고유 대상<span lang="EN-US"> IP </span>주소에 대해 개수가 유지됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">count c<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">탐지 필터 제한을 초과하기 전에 허용되는 최대 규칙 일치 수<span lang="EN-US">(</span>초<span lang="EN-US">)</span>임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">C </span>는<span lang="EN-US"> 0 </span>이 아니어야
  함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">seconds s<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">실사가 발생하는 기간임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">값은 <span lang="EN-US">0 </span>이 아니어야 함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

Snort는 다른 모든 규칙 옵션을 평가 한 후 탐지 단계의 마지막 단계로 탐지 필터를 평가함. \(규칙 소스 내 필터의 위치에 관계없이)
규칙당 최대 하나의 탐지 필터가 허용됨.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><i>이 규칙은 처음<span lang="EN-US"> 30 </span>회의 로그인 시도가 실패한 후<span lang="EN-US"> 60 </span>초 샘플링 기간 동안<span lang="EN-US"> 10.1.2.100 </span>부터 실패한 모든 로그인 시도에 대해 실행됨<span lang="EN-US">.</span></i><i><span lang="EN-US"><o:p></o:p></span></i></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">drop
  tcp 10.1.2.100 any &gt; 10.1.1.100 22 ( \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">msg:"SSH
  Brute Force Attempt";<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">flow:established,to_server;
  \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">content:"SSH";
  nocase; offset:0; depth:4; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">detection_filter:track
  by_src, count 30, seconds 60; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">sid:1000001;
  rev:1;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


잠재적으로 많은 이벤트가 생성되므로 일반적으로 detection_filter 를 event_filter 와 함께 사용하여 기록된 이벤트 수를 줄임.



노트 : </br>
위에서 언급했듯이 Snort 는 탐지 필터를 사후 탐지가 아닌 탐지의 마지막 단계로 평가함.

### 7.8 Post-Detection Quick Reference

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
Post-Detection </span>규칙 옵션 키워드 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">키워드<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">logto<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">logto </span>키워드는이 규칙을 트리거하는 모든 패킷을 특수 출력 로그 파일에
  기록하도록<span lang="EN-US"> Snort </span>에 지시함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">session<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">session </span>키워드는<span lang="EN-US"> TCP </span>세션에서
  사용자 데이터를 추출하기 위해 작성됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">resp<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">resp </span>키워드는 경고가 트리거 될 때 세션을 닫는 데 사용됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">react<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">이 키워드는 사용자가 연결을 닫고 알림을 전송하여<span lang="EN-US"> Snort </span>규칙과 일치하는 트래픽에 반응할 수 있는 기능을 구현함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">tag<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">tag </span>키워드를 사용하면 규칙이 규칙을 트리거 한 단일 패킷 이상을
  기록할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">replace<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">이전에 일치하는 컨텐츠를 동일한 길이의 주어진 문자열로 바뀜<span lang="EN-US">. </span>인라인 모드에서만 사용할 수 있음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">detection_filter<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">소스 또는 대상<span lang="EN-US"> IP </span>주소로 추적하고
  규칙이 구성된 속도보다 더 많이 일치하면 실행됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

## (8) Rule Thresholds



노트 : </br> 
Rule Thresholds 은 더 이상 사용되지 않으며 향후 릴리스에서 지원되지 않음. </br>
규칙 내에서 detection_filters를 사용하거나 대신 독립형 구성으로 event_filters를 사용하십시오.

</br>

임계값은 규칙의 일부로 포함되거나 적용되는 생성자(generator) 및 SID 를 참조하는 독립 실행 형 임계값을 사용할 수 있음.
규칙에 임계값을 추가하는 것과 동일한 규칙에 적용된 독립형 임계값을 사용하는 것 사이에는 기능적 차이가 없음.
논리적 차이가 있음.일부 규칙은 임계값으로만 이해할 수 있음.이는 임계값을 규칙에 통합해야 함.
예를 들어 너무 많은 로그인 암호 시도를 감지하는 규칙은 5 회 이상의 시도가 필요할 수 있음.
이는 'limit' 유형의 임계값을 사용하여 수행할 수 있음.임계값 기능이 이 규칙의 필수 부분이라는 것은 이치에 맞음.

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>형식 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">threshold: \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">type &lt;limit|threshold|both&gt;, \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">track &lt;by_src|by_dst&gt;, \<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">count &lt;c&gt;, seconds &lt;s&gt;;<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>

<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
</span>사용예 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> 60 </span>초마다 <span lang="EN-US">SID </span>의 첫 번째 이벤트를 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $external_net any -&gt; $http_servers $http_ports \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"web-misc
  robots.txt access"; flow:to_server, established; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">uricontent:"/robots.txt";
  nocase; reference:nessus,10302; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">classtype:web-application-activity;
  threshold:type limit, track \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">by_src,
  count 1 , seconds 60; sid:1000852; rev:1;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은<span lang="EN-US"> 60 </span>초마다 <span lang="EN-US">SID </span>의 첫 번째 이벤트를 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">따라서<span lang="EN-US"> 60 </span>초 동안<span lang="EN-US"> 10 </span>개 미만의 이벤트가 발생하면 아무것도 기록되지
  않음<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이벤트가
  기록되면<span lang="EN-US"> type=threshold </span>에 대한 새 기간이 시작됨<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $external_net any -&gt; $http_servers $http_ports \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"web-misc
  robots.txt access"; flow:to_server, established; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">uricontent:"/robots.txt";
  nocase; reference:nessus,10302; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">classtype:web-application-activity;
  threshold:type threshold, \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">track
  by_dst, count 10 , seconds 60 ; sid:1000852; rev:1;)<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><br></span></p>
  <p class="MsoNoSpacing"><i><span style="font-family: courier;">이 규칙은
  <span lang="EN-US">SID </span>에서<span lang="EN-US"> 10 </span>개 이상의 이벤트가 발생하는 경우<span lang="EN-US"> 60 </span>초마다 최대 하나의 이벤트를 기록함<span lang="EN-US">.<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">alert
  tcp $external_net any -&gt; $http_servers $http_ports \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">(msg:"web-misc
  robots.txt access"; flow:to_server, established; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">uricontent:"/robots.txt";
  nocase; reference:nessus,10302; \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">classtype:web-application-activity;
  threshold:type both, track \<o:p></o:p></span></span></i></p>
  <p class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">by_dst,
  count 10, seconds 60; sid:1000852; rev:1;)<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

</div>


<p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;"><span lang="EN-US">&lt;
Post-Detection </span>규칙 옵션 키워드 <span lang="EN-US">&gt;<o:p></o:p></span></span></p>
<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: rgb(219, 229, 241); border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">옵션<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
  <td style="background: rgb(219, 229, 241); border-left: none; border: 1pt solid windowtext; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">type limit|threshold|both<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">시간 간격 동안 첫 번째<span lang="EN-US"> m </span>이벤트에
  대해<span lang="EN-US"> limit </span>경고를 입력한 다음 나머지 시간 간격 동안 이벤트를 무시함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">시간 간격 동안이 이벤트를 볼 때마다 <span lang="EN-US">threshold
  </span>경고를 입력함<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">m </span>개의 이벤트 발생을 확인한 후 시간 간격당 한 번씩<span lang="EN-US"> both </span>경고를 입력 한 다음 시간 간격 동안 추가 이벤트를 무시함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">track by_src|by_dst<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">속도는 소스<span lang="EN-US"> IP </span>주소 또는 대상<span lang="EN-US"> IP </span>주소로 추적됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">즉<span lang="EN-US">, </span>각 고유 소스<span lang="EN-US"> IP </span>주소 또는 각 고유 대상<span lang="EN-US"> IP </span>주소에 대해 개수가 유지됨<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;">포트 또는 기타 항목은 추적되지 않음<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">count c<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">event_filter </span>한계를
  초과하게 만드는<span lang="EN-US"> s </span>초 단위의 규칙 일치 수임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">c </span>는<span lang="EN-US"> 0 </span>이 아닌 값이어야
  함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 90.45pt;" width="121">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">seconds s<o:p></o:p></span></span></p>
  </td>
  <td style="border-bottom: 1pt solid windowtext; border-left: none; border-right: 1pt solid windowtext; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 370.75pt;" width="494">
  <p class="MsoNoSpacing"><span style="font-family: courier;">실사가 발생하는 기간임<span lang="EN-US">.<o:p></o:p></span></span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">s </span>는<span lang="EN-US"> 0 </span>이 아닌 값이어야
  함<span lang="EN-US">.<o:p></o:p></span></span></p>
  </td>
 </tr>
</tbody></table>

</div>


## (9) 좋은 규칙 작성

- 효율성과 속도를 극대화하기 위해 Snort 규칙을 개발할 때 염두에 두어야 할 몇 가지 일반적인 개념이 있음.


### 9.1 컨텐츠 매칭



Snort 는 프로토콜\(ip, tcp, udp, icmp), 포트\(ip 와 icmp 는 약간 다른 로직 사용), content 가 있는 것과 없는 것 별로 규칙을 그룹화함.
content 가 포함 된 규칙의 경우 단일 컨텐츠를 기준으로 일치 가능성이 있는 규칙을 선택하기 위해 다중 패턴 매처\(multi-pattern matche)가 사용됨.
이 "빠른" 패턴 일치기\("fast" pattern matcher)를 통해 평가할 규칙을 선택하면 특히 HTTP 와 같은 대규모 규칙 그룹에 적용될 때 성능이 향상되는 것으로 나타남.
content 가 길고 고유할수록 해당 규칙과 모든 규칙 옵션이 불필요하게 평가 될 가능성이 줄어듬.
일반적으로 "나쁜" 트래픽보다 "좋은" 트래픽이 더 많다고 말하는 것이 안전함\(safe).
content 가 없는 규칙은 항상 평가되어\(상주하는 프로토콜 및 포트 그룹과 관련하여) 잠재적으로 성능에 영향을 줌.
pcre 및 byte_test 와 같은 검색 옵션은 패킷의 페이로드 섹션에서 검색을 수행하지만 고속 패턴 일치 엔진\(fast pattern matching engine)에서는 사용되지 않음.
가능하면 규칙에 하나 이상의 content\(또는 uricontent) 규칙 옵션을 사용하십시오.





### 9.2 익스플로잇이 아닌 취약점 파악 (Catch the Vulnerability, Not the Exploit)

특정 익스플로잇 대신 취약점을 표적으로 삼는 규칙을 작성하십시오.
예를 들어, 쉘을 바인딩하는 쉘코드 대신 인수가 너무 큰 취약한 명령어를 찾으십시오.
취약점에 대한 규칙을 작성하면 공격자가 익스플로잇을 약간 변경할 때 규칙이 회피에 덜 취약함.





### 9.3 규칙에서 프로토콜의 이상한 점 파악



많은 서비스는 일반적으로 대문자로 명령어을 모냄.
FTP 가 좋은 예임.
FTP 에서 사용자 이름을 보내기 위해 클라이언트는 다음을 보냄.
    </br>
      user username_here



FTP root 로그인 시도를 찾는 간단한 규칙은 다음과 같음.</br>
alert tcp any any -> any any 21 \(content:"user root";) </br>



사용자 이름 root 를 찾는 규칙을 작성하는 것은 사소한 것처럼 보일 수 있지만, 좋은 규칙은 사용자 명령을 수락할 때 프로토콜이 처리 할 수 있는 모든 이상한 일을 처리함.
예를 들어, 다음은 대부분의 FTP 서버에서 허용됨.



   user root </br>
   user root </br>
   user root </br>
   user root </br>
   user\<tab>root </br>



FTP 서버가 처리 할 수 있는 모든 경우를 처리하려면 규칙에 단순한 문자열 일치보다 더 스마트 한 것이 필요함.
ftp 에서 루트 로그인을 찾는 좋은 규칙은 다음과 같음. </br>
alert tcp any any -> any 21 \(flow:to_server,established; \\  </br>
content:"root"; pcre:"/user\s+root/i";)

</br>

이 규칙에서 유의해야 할 몇 가지 중요한 사항이 있음 : </br>
  • 규칙에는 설정된 세션에서 서버로 이동하는 트래픽인지 확인하는 flow 옵션이 있음. </br>
  • 규칙에는 공격에서 가장 길고 고유 한 문자열 인 root 를 찾는 content 옵션이 있음.
  • 이 옵션은 페이로드에서 root 컨텐츠가 발견되는 경우에만 평가를 위해 빠른 패턴 일치자가 이 규칙을 선택할 수 있도록 추가됨. </br>
  • 규칙에는 pcre 옵션이 있으며 user 를 찾고 적어도 하나의 공백 문자\(탭 포함)와 root 가 이어짐. \(대소문자 무시) </br>





### 9.4 규칙 최적화

검색 엔진의 컨텐츠 일치 부분에는 몇 가지 회피 사례를 처리하기 위한 재귀가 있음.
제대로 작성되지 않은 규칙으로 인해 Snort 가 검사를 복사하는\(duplicationg) 데 시간을 낭비 할 수 있음.
이제 재귀가 작동하는 방식은 패턴이 일치하는 경우이고 해당 패턴 이후의 검색 옵션이 실패하면 이전에 발견된 위치에서 다시 패턴을 찾음.
패턴이 다시 발견되지 않거나 opt 기능이 모두 성공할 때까지 반복하십시오.
처음 읽을 때, 그것은 현명한 생각처럼 들리지 않을 수도 있지만 필요함.

</br>

예를 들어, 다음 규칙을 따르십시오 : </br>
alert ip any any -> any any \(content:"a"; content:"b"; within:1;)



이 규칙은 "a" 를 찾고 바로 뒤에 "b" 를 찾음.
재귀가 없으면 페이로드 "aab" 에 "a" 바로 뒤에 "b" 가 있음이 분명하더라도 "aab" 페이로드가 실패함.
왜냐하면 첫 번째 "a" 다음에 "b" 가 바로 뒤따르지 않기 때문임.
재귀는 탐지에 중요하지만 재귀 구현은 그리 똑똑하지 않음.

</br>

예를 들어 다음 규칙 옵션은 최적화되지 않음. </br>
content:"|13|"; dsize:1;

</br>

이 규칙 스니펫\(snippet)을 보면 규칙이 단일 바이트가 0x13 인 패킷을 찾는 것이 분명함.
그러나 재귀로 인해 1024 바이트의 0x13 패킷은 1023 너무 많은 패턴 일치 시도와 1023 너무 많은 dsize 검사를 유발할 수 있음.

</br>

***왜?***

컨텐츠 0x13 이 첫 번째 바이트에서 발견되면 dsize 옵션이 실패하고 재귀로 인해 컨텐츠 0x13 이 이전 0x13 이 발견된 위치부터 다시 발견되고 일단 발견되면 dsize 를 다시 확인함.
페이로드에서 0x13 이 다시 발견되지 않을 때까지 반복함.

</br>

불연속 검사(예 : dsize)가 규칙의 시작 부분으로 이동되도록 규칙 옵션을 재정렬하면 Snort 속도가 빨라짐.

</br>

최적화 된 규칙 스니핑(snipping)은 다음과 같음 : </br>
dsize:1; content:"|13|";



1024 바이트 0x13 패킷은 dsize 검사가 첫 번째 옵션이고 dsize 가 재귀 없는 개별 검사이므로 즉시 실패함.

</br>

다음 규칙 옵션은 개별적이며 일반적으로 규칙의 시작 부분에 배치해야 함.



• dsize

• flags

• flow

• fragbits

• icmp id

• icmp seq

• icode

• id

• ipopts

• ip proto

• itype

• seq

• session

• tos

• ttl

• ack

• window

• resp

• sameip





### 9.5 숫자값 테스트



규칙 옵션 byte_test 및 byte_jump 는 길이 인코딩 데이터가 있는 프로토콜에 대한 쓰기 규칙을 지원하기 위해 작성됨.
RPC 는 데이터 전달에 간단한 길이 기반 인코딩을 사용하기 때문에 RPC 는 이 두 가지 규칙 옵션에 대한 요구 사항을 생성한 프로토콜임.

</br>

byte_test 및 byte jump 가 유용한 이유를 이해하기 위해 sadmind 서비스에 대한 공격 시도를 살펴봄.
이것은 익스플로잇의 페이로드임.

</br>

89 09 9c e2 00 00 00 00 00 00 00 02 00 01 87 88 ................

00 00 00 0a 00 00 00 01 00 00 00 01 00 00 00 20 ...............

40 28 3a 10 00 00 00 0a 4d 45 54 41 53 50 4c 4f @(:.....metasplo

49 54 00 00 00 00 00 00 00 00 00 00 00 00 00 00 it..............

00 00 00 00 00 00 00 00 40 28 3a 14 00 07 45 df ........@(:...e.

00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................

00 00 00 00 00 00 00 06 00 00 00 00 00 00 00 00 ................

00 00 00 00 00 00 00 04 00 00 00 00 00 00 00 04 ................

7f 00 00 01 00 01 87 88 00 00 00 0a 00 00 00 04 ................

7f 00 00 01 00 01 87 88 00 00 00 0a 00 00 00 11 ................

00 00 00 1e 00 00 00 00 00 00 00 00 00 00 00 00 ................

00 00 00 00 00 00 00 3b 4d 45 54 41 53 50 4c 4f .......;metasplo

49 54 00 00 00 00 00 00 00 00 00 00 00 00 00 00 it..............

00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................

00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................

00 00 00 00 00 00 00 06 73 79 73 74 65 6d 00 00 ........system..

00 00 00 15 2e 2e 2f 2e 2e 2f 2e 2e 2f 2e 2e 2f ....../../../../

2e 2e 2f 62 69 6e 2f 73 68 00 00 00 00 00 04 1e ../bin/sh.......

<snip>

</br>

이를 분리하고 각 필드를 설명하고 이 악용을 포착하기 위한 규칙을 작성하는 방법을 알아봄.

RPC 와 관련하여 몇 가지 주의 할 사항이 있음 : </br> 
• 숫자는 4 바이트를 사용하는 uint32s 로 작성됨. 숫자 26 은 0x0000001a로 표시됨. </br>
• 문자열은 문자열, 문자열의 길이를 지정하는 uint32 로 작성되고 4 바이트 경계에서 끝나도록 문자열 길이를 채우는 null 바이트가 있음. </br>
• 문자열 "bob" 은 0x00000003626f6200 으로 표시됨.

</br>

89 09 9c e2 - the request id, a random uint32, unique to each request

00 00 00 00 - rpc type (call = 0, response = 1)

00 00 00 02 - rpc version (2)

00 01 87 88 - rpc program (0x00018788 = 100232 = sadmind)

00 00 00 0a - rpc program version (0x0000000a = 10)

00 00 00 01 - rpc procedure (0x00000001 = 1)

00 00 00 01 - credential flavor (1 = auth\_unix)

00 00 00 20 - length of auth\_unix data (0x20 = 32

</br>

\## the next 32 bytes are the auth\_unix data

40 28 3a 10 - unix timestamp (0x40283a10 = 1076378128 = feb 10 01:55:28 2004 gmt)

00 00 00 0a - length of the client machine name (0x0a = 10)

4d 45 54 41 53 50 4c 4f 49 54 00 00 - metasploit

00 00 00 00 - uid of requesting user (0)

00 00 00 00 - gid of requesting user (0)

00 00 00 00 - extra group ids (0)

00 00 00 00 - verifier flavor (0 = auth\_null, aka none)

00 00 00 00 - length of verifier (0, aka none)

</br>

나머지 패킷은 sadmind 의 프로시저 1 로 전달되는 요청임.
그러나 취약점은 sadmind 가 클라이언트에서 오는 uid 를 신뢰한다는 것임.
sadmind 는 클라이언트의 uid 가 0 인 요청을 root 로 실행함.
따라서 규칙을 작성하기 위해 요청을 충분히 디코딩했음.
먼저 패킷이 RPC 호출인지 확인해야 함.

</br>

content:"|00 00 00 00|"; offset:4; depth:4;

</br>

- 그런 다음 패킷이 sadmind 에 대한 호출인지 확인해야 함.

</br>

content:"|00 01 87 88|"; offset:12; depth:4;

</br>

- 그런 다음 패킷이 취약한 절차 1 에 대한 호출인지 확인해야 함.

</br>

content:"|00 00 00 01|"; offset:20; depth:4;

</br>

- 그런 다음 패킷에 인증 유닉스 자격 증명이 있는지 확인해야 함.

</br>

content:"|00 00 00 01|"; offset:24; depth:4;

</br>

- 호스트 이름은 신경 쓰지 않지만 건너 뛰고 호스트 이름 뒤의 숫자 값을 확인하려고 함.
- 이것은 byte_test 가 유용한 곳임.

</br>

호스트 이름의 길이에서 시작하는 데이터는 다음과 같음 :



00 00 00 0a 4d 45 54 41 53 50 4c 4f 49 54 00 00

00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00 00 00 00



우리는 4 바이트를 읽고 이를 숫자로 바꾸고 그 만큼의 바이트를 앞으로 점프하여 RPC 가 문자열에 요구하는 패딩을 고려함.

</br>

그렇게 한다면 우리는 다음과 같은 위치에 있음 :



00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00 00 00 00



이는 우리가 확인하려는 값인 uid 의 정확한 위치임.
영어로 우리는 패킷 시작 부분에서 4 바이트, 36 바이트를 읽고 4 바이트를 정수로 바꾸고 4 바이트 경계에 맞춰 해당 바이트를 앞으로 점프하려고 함.

Snort 규칙에서 이를 수행하기 위해 다음을 사용함 :



byte_jump:4,36,align;

</br>

- 그런 다음 uid 0을 찾고 싶음.

</br>

content:"|00 00 00 00|"; within:4;

</br>

- 이제 규칙에 대한 모든 검색 기능을 갖추었으므로 모두 통합해봄.

</br>

content:"|00 00 00 00|"; offset:4; depth:4;

content:"|00 01 87 88|"; offset:12; depth:4;

content:"|00 00 00 01|"; offset:20; depth:4;

content:"|00 00 00 01|"; offset:24; depth:4;

byte_jump:4,36,align;

content:"|00 00 00 00|"; within:4;

</br>

세 번째와 네 번째 문자열 일치는 바로 옆에 있으므로 이러한 패턴을 결합해야 함.
우리는 다음과 같이 끝남.

</br>

content:"|00 00 00 00|"; offset:4; depth:4;

content:"|00 01 87 88|"; offset:12; depth:4;

content:"|00 00 00 01 00 00 00 01|"; offset:20; depth:8;

byte_jump:4,36,align;

content:"|00 00 00 00|"; within:4;

</br>

sadmind 서비스가 클라이언트의 호스트 이름을 읽을 때 버퍼 오버플로우에 취약한 경우 호스트 이름의 길이를 읽고 그만큼 앞으로 이동하는 대신 호스트 이름의 길이가 너무 크지 않은지 확인함.
이를 위해 36 바이트에서 시작하여 4 바이트를 패킷으로 읽어서 숫자로 변환한 다음 너무 크지 않은지 확인함. \(200 바이트보다 크지 않은 경우)

Snort에서는 다음을 수행함 :



byte_test:4,>,200,36;

</br>

우리의 전체 규칙은 다음과 같음.

</br>

content:"|00 00 00 00|"; offset:4; depth:4;

content:"|00 01 87 88|"; offset:12; depth:4;

content:"|00 00 00 01 00 00 00 01|"; offset:20; depth:8;

byte_test:4,>,200,36;
