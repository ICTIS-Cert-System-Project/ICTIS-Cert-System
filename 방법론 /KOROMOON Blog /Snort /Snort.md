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
- **현재 Snort 에서는 TCP, UDP, ICMP, IP 이렇게 4가지 프로토콜 분석 가능함. (규칙에 기재할 때 소문자로 기재할 것!)**
- 앞으로 다른 프로토콜이 추가할 수 있을 것으로 전망됨. (ex. ARP, IGRP, GRE, OSPF, RIP, IPX)

### 2.3 IP 주소
- IP 주소는 IP 와 CIDR 블록 형식으로 기재하며 any 키워드는 임의의 주소를 정의하는데 사용됨.
- 부정연산자 ! 를 사용할 경우 표시된 IP 주소 이외의 IP 주소만 적용됨. 
- 쉼표로 구분된 IP 주소 목록을 대괄호 기호로 이용하여 표시함.
- _참고로 Snort 는 IP 주소 필드에 대한 호스트 이름 조회를 제공하는 매커니즘이 없음._




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
- 포트 번호는 포트, 범위연산자 :, 부정 연산자 ! 를 이용한 여러 가지 방법으로 지정함.
- any 키워드는 모든 포트를 의미하는 와일드카드 값임.

### 2.5 방향 연산자
- 일방향 연산자 -> 와 양방향 연산자 <> 를 사용함.
- **참고로 규칙 일관성을 위해서 <- 기호는 사용하지 않음.**


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
- 규칙 옵션은 Snort 침입 탐지 엔진의 핵심이며 편의성과 유연성을 결합함.
- **모든 Snort 규칙 옵션은 세미콜론 문자(;)를 사용하여 서로 구분함.**
- **규칙 옵션 키워드는 콜론 문자(:)를 사용하여 인수와 구분함.**

</br>

- 규칙 옵션에는 아래 4 가지 주요 범주가 있음.

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
- msg 키워드는 로깅 및 경고 엔진에 패킷 덤프 또는 경고와 함께 인쇄할 메시지를 알려줌.
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
- reference 키워드를 사용하면 규칙에 대해서 외부 공격 식별 시스템에 대한 참조를 포함할 수 있음.
- 플러그인은 고유 URL 뿐만 아니라 여러 특정 시스템을 지원함.
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
- gid 키워드(generator id)는 특정 규칙이 발생할 때 Snort 가 어떤 이벤트를 생성하는 지 식별하는데 사용됨.
- 현재 사용 중인 gid 에 대해서는 /etc/generators 파일을 참조 바람.
- gid 키워드는 선택사항이며 규칙에 지정되지 않은 경우 기본값은 1 이며 규칙은 일반 규칙 하위시스템의 일부가 됨.
- Snort 에 정의된 gid 와 잠재적인 충돌을 피하기 위해서 1,000,000 부터 사용하는 것이 좋음.
- 일반적인 규칙 작성할 경우, gid 키워드를 사용할 것!
- 이 옵션은 sid 키워드와 함께 사용해야 함.
- etc/gen-msg.map 파일에 Preprocessor 및 Decoder gid 에 대한 자세한 정보가 들어 있음.

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
- sid 키워드는 Snort 규칙을 고유하게 식별하는 데 사용됨.
- 이 정보는 출력 플러그인이 규칙을 쉽게 식별할 수 있게 함.
- 이 옵션은 rev 키워드와 함께 사용해야 함.

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

- sid-msg.map 파일에는 Snort 규칙 ID 에 대한 경고 메시지 매핑이 들어 있음.
- 이 정보는 경고를 사후 처리하여 ID 를 경고 메시지에 매핑할 때 유용함.


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
- rev 키워드는 Snort 규칙의 수정 버전을 고유하게 식별하는 데 사용됨.
- Snort 규칙 ID 와 함께 개정이 허용되며 서명 및 설명을 수정하여 업데이트 된 정보를 대체할 수 있음.
- 이 옵션은 sid 키워드와 함께 사용해야 함.


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

- classtype 키워드는 규칙에 대한 공격 범주화하는데 사용함.
- Snort 는 기본적으로 제공하는 규칙에 대해서 공격 범주를 제공함.

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

- Snort 가 정의한 공격 범주 분류는 classification.config 파일에 있음.
- 이 파일은 다음과 같은 구문을 사용함.
  + config classification: \<class name>,\<class description>,\<default priority>

- 이러한 공격 범주 분류는 아래 표에 나열되어 있음.
- 현재 4 가지 기본 우선 순위로 기재하였으며 1(높음) 은 가장 심각하고 4(매우 낮음) 는 가장 덜 심각함.

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
