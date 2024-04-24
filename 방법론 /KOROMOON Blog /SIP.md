# SIP
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/sip.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 10일 

## (1) SIP의 정의
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/154ab895-39f8-4ee4-9e99-f48dbb240527)
Session Initiation Protocol 의 약자로서 **매우 간단한 텍스트 기반의 응용계층 제어 프로토콜**로서 HTTP 프로토콜의 응답/요청 트랙잭션 모델임.
SIP는 SMTP와 HTTP 이후에 설계되었으며 SMTP나 HTTP처럼 텍스트 기반의 인터넷 표준을 따름으로서 고장 수리와 네트워크 디버깅이 쉬움.
쉽게 설명하자면 두 개의 엔드 포인트 간의 통신 세션을 시작하는 데 필요한 확장 가능하고 가벼운 요청/응답 프로토콜임.
여기서 엔드 포인트를 사용자 에이전트라고 함.
이는 소프트폰, 인스턴트 메신저, IP폰, 심지어 휴대폰일 수 있음.
SIP는 두 엔드 포인트에서 호출을 협상하기 위해 사용됨. 협상이라 하면 매체(텍스트, 음성, 기타), 전송 프로토콜(주로 RTP) 및 인코딩(코덱)에서 각기 적합한 것을 결정한다는 것을 의미함.
협상이 성공하면 양 엔드 포인트에서는 SIP와 상관없이 선택된 방식을 사용하여 서로 대화함.
호출이 종료되면 연결 해제를 알리기 위해서 SIP가 사용됨.
둘 이상의 참가자들이 함께 세션을 만들고 수정하고 종료할 수 있게 함. 이러한 세션들은 인터넷을 이용한 원격 회의, 전화, 면회, 이벤트 통지, 인스턴트 메시지 등에 사용할 수 있으며 회의나 전화 통화에 상대방을 쉽게 초대할 수 있게 하기 위해 만들어진 프로토콜임.
각 사용자들을 구분하기 위해 **이메일 주소와 비슷한 SIP URL을 사용함**으로써 IP주소에 종속되지 않고 서비스를 받음. HTTP와 SMTP의 많은 부분을 그대로 사용하여 개발된 텍스트 기반으므로 구현이 용이하며 인터넷에서 사용되는 다른 많은 프로토콜과 결합하여 다양한 서비스들을 만들 수 있는 유연성과 확장성이 있음.

## (2) SIP 특징
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/4348916c-4b3c-4121-81ae-cacd8c44c7fc)
SIP 프로토콜은 패킷 교환망에서 회선 교환망 방식의 호(call) 제어가 가능하도록 세션을 제어함.
패킷망의 인터넷 상에서 멀티미디어 어플리케이션이 가능하게 함.
URL 및 E-Mail 형식의 텍스트 기반 어드레싱 방법을 사용하므로 메시지 파싱이나 확장이 용이함.

## (3) SIP 중요성

통신에 있어서 SIP 프로토콜의 역할은 HTTP 프로토콜이 웹에서 수행하는 역할에 비견할 수 있음.
SIP 프로토콜이 통신 산업에 엄청난 반향을 일으키고 있음. 셀률러 기술 기업들은 향후의 모든 어플리케이션을 SIP 프로토콜로 표준화하기로 결정함.
VoIP 벤더, 인터넷 텔레폰 및 인스턴트 메시징 어플리케이션(ex. MSN Messenger)이 모두 SIP 프로토콜로 표준화되고 있음.

## (4) SIP 구성 요소

SIP 시스템의 구성 요소는 SIP 클라이언트와 SIP 서버로 나누어짐.

</br>

SIP 클라이언트
<div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" valign="top" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">구분<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">설명<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">UAC<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">(User Agent Clinet)<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">세션 종단에 위치하여 호<span lang="EN-US">(call)</span>를 생성하고 설정을 요청함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">UAS<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">(User Agent Server)<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">UAC</span>로부터 호<span lang="EN-US">(call)</span>를 수락하거나 거절
  또는<span lang="EN-US"> Redirect</span>함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>
</div>

SIP 서버 : UA간 직접 호출이 가능하지만 SIP 서버를 둠으로써 확장성을 제공함.
<div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" valign="top" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">구분<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">설명<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Proxy Server<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">UAC</span>로부터<span lang="EN-US"> SIP </span>콜을 받아 자신이 콜을
  대신 만들어 주는 역할을 함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Register Server<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자의 에이전트로부터 레지스터 요청을
  수신하여 사용자의 위치 정보를 유지함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Redirect Server<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자가 직접 요청을 할 수 있는
  상대방의<span lang="EN-US"> URL</span>을 알려줌<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Location Server<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Proxy
  Server</span>나<span lang="EN-US">
  Redirect Server</span>로부터<span lang="EN-US"> SIP </span>콜의 목적지 노드의 주소가 요청되면 이를<span lang="EN-US"> Resolution(</span>변환<span lang="EN-US">) </span>해주는 역할을 함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>
</div>

## (5) SIP 패킷 구조
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/b39e6848-8ef6-4575-b15e-aaa67e7a9faf)
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/e51e3c9f-464f-4430-9dba-cf0c4be1b8ff)

위 그림은 일반적인 SIP를 포함한 패킷의 구조이며 IP Header (20 Byte) / UDP Header (8 Byte) / SIP Header / SIP Message Body 로 이루어짐. 
SIP Message Body 는 있을 수도 있고 없을 수도 있는 옵션이며 주로 SDP(Session Description Protocol : 멀티미디어 세션 파라미터)의 내용이 첨가된다고 보면 됨.
위 그림에서는 Transport Layer 프로토콜로 UDP로 되어 있으며 UDP가 일반적이지만 TCP 또는 SCTP가 사용될 수 있음.


*참고*) SDP Lines Message 설명
SDP도 SIP 마찬가지로 텍스트 기반이며 다음의 내용을 포함함.
관심 가질 사항은 딱 2개이며 m, a 임. 실제 사용될 코덱과 코덱의 속성에 대해 설명함.


v = protocol version </br>
o = owner/creator and session identifier )  </br>
s = session name </br>
c = connection information – not required if included in all media </br>
k = encryption keys </br>
t = time the session is active </br>
m = media description and transport address </br>
a = (zero or more) media attributes lines </br>

## (6) SIP Header Field
- 주요 필드만 소개함.
<div>
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" valign="top" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">필드<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">설명<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">From<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">SIP </span>요청 발신자<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">To<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">요청 수신자<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">이는 종종<span lang="EN-US"> SIP URI("</span>별칭<span lang="EN-US">" </span>또는 실제 주소일 수
  있음<span lang="EN-US">)</span>와 동일함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Contact<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자 에이전트의 실제 주소<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Call-ID<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">두 사용자 에이전트 간의 전체 호출<span lang="EN-US">, </span>즉 대화를 나타냄<span lang="EN-US">.<o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">주의<span lang="EN-US">! </span>절대로 발신자의 전화 번호가 아님<span lang="EN-US">.<o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">모든 관련<span lang="EN-US"> SIP </span>메시지는 동일한<span lang="EN-US"> Call-ID</span>를 사용함<span lang="EN-US">.<o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">예를 들어 사용자 에이전트가<span lang="EN-US"> BYE </span>메시지를 수신하면<span lang="EN-US"> Call-ID</span>에 따라 종료할 호출을 알게
  됨<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Cseq<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">메시지의 순차 번호<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">이는 단일 대화나<span lang="EN-US"> Call-ID </span>내에서만 사용되며 새 메시지와 재시도를 구분하기 위해 사용됨<span lang="EN-US">.<o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">재시도는 초기 메시지가 해당 시간
  내에<span lang="EN-US"> OK</span>되지 못할 때 발생하며 일정 간격으로 실행됨<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Content-Type<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">메시지 내부 페이로드의<span lang="EN-US"> MIME </span>타입<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Content-Length<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">페이로드의 바이트 크기<span lang="EN-US"><o:p></o:p></span></span></div>
<div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">엔빌로프<span lang="EN-US">(envelope)</span>와 페이로드는 한 줄을 띄어 구분함<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>
</div>

## (7) SIP 요청 메시지
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" valign="top" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">메시지<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">설명<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">INVITE<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자 에이전트에게 호출 요청<span lang="EN-US">, </span>호출 전송<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">ACK<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">호출 확인<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">BYE<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">호출 종료<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">CANCEL<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">아직<span lang="EN-US"> OK</span>되지 않은 호출 종료<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">REGISTER<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">등록 서비스에 연락 주소와 대신 사용할
  수 있는 별칭 제공<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 104.65pt;" width="140"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">OPTIONS<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 356.55pt;" valign="top" width="475"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자 에이전트에게 가능한 옵션<span lang="EN-US">(</span>해당 에이전트가 이해하는 메시지와 코덱<span lang="EN-US">)</span>을 요청<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## (8) SIP 응답 메시지
- 자주 사용되는 응답 메시지만 소개함.
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" valign="top" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">메시지<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid black 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid black .5pt; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-themecolor: text1; mso-border-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div align="center" class="MsoNormal" style="text-align: center;">
<b><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">설명<span lang="EN-US"><o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">100 Trying<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">이 메시지가 수신되어도 최종 사용자
  에이전트에 의해 아직 처리되지 않습니다<span lang="EN-US">. </span>기다리십시오<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">180 Ringing<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">이 메시지가 최종 사용자 에이전트에
  의해 수신되어 해당 사용자에게 나타납니다<span lang="EN-US">. </span>기다리십시오<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">200 OK<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">이 메시지가 최종 사용자에 의해 수락되었습니다<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">301 Moved Permanently<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">&amp;<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">302 Moved Temporarily<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">사용자 에이전트의 주소가 변경되었습니다<span lang="EN-US">. Contact </span>필드에 새 영구 주소 또는 임시 주소가 있습니다<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">400 Bad Request<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">일반 오류 메시지<span lang="EN-US">. </span>클라이언트가 이 메시지를 이해하지 못합니다<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">401 Unauthorized<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">&amp;<o:p></o:p></span></span></div>
<div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">407 Proxy Authentication Require<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">자격을 증명하고 다시 시도하십시오<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">404 Not Found<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">연결하려는 사용자가 존재하지 않거나
  등록되지 않았습니다<span lang="EN-US">.<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid black 1.0pt; mso-border-alt: solid black .5pt; mso-border-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168"><div align="center" class="MsoNormal" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">408 Request Timeout<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid black 1.0pt; border-left: none; border-right: solid black 1.0pt; border-top: none; mso-border-alt: solid black .5pt; mso-border-bottom-themecolor: text1; mso-border-left-alt: solid black .5pt; mso-border-left-themecolor: text1; mso-border-right-themecolor: text1; mso-border-themecolor: text1; mso-border-top-alt: solid black .5pt; mso-border-top-themecolor: text1; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" valign="top" width="447"><div class="MsoNormal">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">상대방이 응답하지 않습니다<span lang="EN-US">. </span>이는<span lang="EN-US"> SIP </span>메시지가<span lang="EN-US"> OK</span>되지
  않았을 뿐 아니라 모든 재시도가 실패했음을 의미합니다<span lang="EN-US">. </span>전화 벨이 너무 오랫동안 울렸다는 것을 의미하는
  것이 아닙니다<span lang="EN-US">. (</span>전화 벨은 계속해서 울릴 수 있습니다<span lang="EN-US">)<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## (10) SIP 인증 절차
SIP는 HTTP 인증 방식에 기반을 둔 Stateless, Challenge-Based 인증 매커니즘을 제공함.
Inbound Proxy Server  또는 UAS가 SIP 요청 메시지를 수신하면 UAC에게 Identity Assurance 제공을 요청함.
UAC가 인증되면 해당 SIP 요청을 수신한 UAS는 UAC가 권한이 있는지를 확인해야 함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/aa0cb629-f953-4c7a-a963-c67c2aa05faf)

① REGISTER : UAC -> SIP Server

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/274a2fec-3422-4709-a0df-537c661beeb2)
먼저 UAC가 SIP Server로 자기좀 등록해 달라고 SIP REGISTER 요청 메시지를 전송함.

② 401 Unauthorized : SIP Server -> UAC

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/80af4c5e-71b7-408e-bd45-1edfff1461aa)

UAC가 전송한 REGISTER 요청 메시지를 수신한 SIP Server는 해당 Authorization 헤더값을 체크함.
만약 Authorization 헤더값이 설정되어 있지 않아 인증 정보가 없을 경우 SIP Server는 UAC에게 nonce 헤더값을 설정하여 challenge 함.
이때 SIP 메시지 상의 WWW-Authenticate 헤더값에 생성된 nonce 항목과 algorithm 항목에 암호화 알고리즘 방식등을 설정하여 UAC가 SIP Server로의 인증시 참조할 정보들을 기술함.

③ REGISTER : UAC -> SIP Server

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/62d36ce0-2b7b-4321-aca5-526a779efde9)

UAC는 SIP Server가 전송한 nonce 값의 체크섬(checksum)을 계산하여 해당 값을 참조하여 SIP 메시지의 Authorization 헤더값을 설정한 후 다시 서버로 전송하여 인증절차를 밟음. (credentials)

④ 200 OK : SIP Server -> UAC

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/9df3dbcc-91d7-493f-88f2-8e155d22ffa1)


UAC로부터 인증 정보가 재첨부된 SIP REGISTER 요청 메시지를 수신한 SIP Server는 수신된 인증 정보로 인증 과정이 문제없이 통과되었을 경우 UAC에게 인증이 성공적으로 완료되었음을 알리는  200 OK 메시지를 전송함.

### 참고 사이트 : 
[1] SIP의 이해 </br>
http://www.nexpert.net/category/SIP%EC%9D%98%20%EC%9D%B4%ED%95%B4 </br>
[2] SIP이란 </br>
http://blog.daum.net/mun850515/18259412 </br>
[3] SIP Header Field </br>
http://blog.daum.net/notime/16711061 </br>
http://blog.acronym.co.kr/125 </br>
[4] 몽키몽키님의 이동통신 기초 </br>
http://blog.naver.com/PostList.nhn?blogId=cache798&from=postList&categoryNo=47 </br>
[5] Penetration Testing VOIP with Backtrack </br>
http://dayatcempoe.blogspot.kr/2012/01/penetration-testing-voip-with-backtrack.html </br>
[6] [단독] KT 고객에게 걸려온 SIPVicious 전화의 정체? </br>
http://www.boannews.com/media/view.asp?idx=33548&page=16&kind=1&search=title&find=%C8%A3%BE%D6%C1%F8%B1%E2%C0%DA </br>
[7] SIPVicious 블로그 </br>
http://blog.sipvicious.org/
