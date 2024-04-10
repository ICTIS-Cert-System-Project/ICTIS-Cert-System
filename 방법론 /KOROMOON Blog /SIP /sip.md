# SIP
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/sip.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 10일 

## (1) SIP의 정의
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/154ab895-39f8-4ee4-9e99-f48dbb240527)
- Session Initiation Protocol 의 약자로서 **매우 간단한 텍스트 기반의 응용계층 제어 프로토콜**로서 HTTP 프로토콜의 응답/요청 트랙잭션 모델임.
- SIP는 SMTP와 HTTP 이후에 설계되었으며 SMTP나 HTTP처럼 텍스트 기반의 인터넷 표준을 따름으로서 고장 수리와 네트워크 디버깅이 쉬움.
- 쉽게 설명하자면 두 개의 엔드 포인트 간의 통신 세션을 시작하는 데 필요한 확장 가능하고 가벼운 요청/응답 프로토콜임.
- 여기서 엔드 포인트를 사용자 에이전트라고 함. 이는 소프트폰, 인스턴트 메신저, IP폰, 심지어 휴대폰일 수 있음.
- SIP는 두 엔드 포인트에서 호출을 협상하기 위해 사용됨. 협상이라 하면 매체(텍스트, 음성, 기타), 전송 프로토콜(주로 RTP) 및 인코딩(코덱)에서 각기 적합한 것을 결정한다는 것을 의미함. 협상이 성공하면 양 엔드 포인트에서는 SIP와 상관없이 선택된 방식을 사용하여 서로 대화함.
- 호출이 종료되면 연결 해제를 알리기 위해서 SIP가 사용됨.
- 둘 이상의 참가자들이 함께 세션을 만들고 수정하고 종료할 수 있게 함. 이러한 세션들은 인터넷을 이용한 원격 회의, 전화, 면회, 이벤트 통지, 인스턴트 메시지 등에 사용할 수 있으며 회의나 전화 통화에 상대방을 쉽게 초대할 수 있게 하기 위해 만들어진 프로토콜임.
- 각 사용자들을 구분하기 위해 **이메일 주소와 비슷한 SIP URL을 사용함**으로써 IP주소에 종속되지 않고 서비스를 받음. HTTP와 SMTP의 많은 부분을 그대로 사용하여 개발된 텍스트 기반으므로 구현이 용이하며 인터넷에서 사용되는 다른 많은 프로토콜과 결합하여 다양한 서비스들을 만들 수 있는 유연성과 확장성이 있음.

## (2) SIP 특징
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/4348916c-4b3c-4121-81ae-cacd8c44c7fc)
- SIP 프로토콜은 패킷 교환망에서 회선 교환망 방식의 호(call) 제어가 가능하도록 세션을 제어함.
- 패킷망의 인터넷 상에서 멀티미디어 어플리케이션이 가능하게 함.
- URL 및 E-Mail 형식의 텍스트 기반 어드레싱 방법을 사용하므로 메시지 파싱이나 확장이 용이함.

## (3) SIP 중요성

- 통신에 있어서 SIP 프로토콜의 역할은 HTTP 프로토콜이 웹에서 수행하는 역할에 비견할 수 있음.
- SIP 프로토콜이 통신 산업에 엄청난 반향을 일으키고 있음. 셀률러 기술 기업들은 향후의 모든 어플리케이션을 SIP 프로토콜로 표준화하기로 결정함.
- VoIP 벤더, 인터넷 텔레폰 및 인스턴트 메시징 어플리케이션(ex. MSN Messenger)이 모두 SIP 프로토콜로 표준화되고 있음.

## (4) SIP 구성 요소

- SIP 시스템의 구성 요소는 SIP 클라이언트와 SIP 서버로 나누어짐.

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
