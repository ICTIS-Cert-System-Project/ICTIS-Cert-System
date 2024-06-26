# ICMP

| 작성자       | 강하늘 사원   |
| --------- | ---------------- |
| **작성 일자** | **2024년 4월 18일** |
| **수정 일자** |                  |
| **비고**    |                  |

<br>

## ( 1 ) ICMP 정의
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/04230e68-cc14-49cd-8a53-b9da94c67ab1)

< TCP/IP 프토로콜, 출저 - http://www.tcpipguide.com/free/t_TCPIPProtocols.htm >

인터넷 제어 메시지 프로토콜(Internet Control Message Protocol)로 호스트 서버와 인터넷 게이트웨이 사이에서 메시지를 제어하고 에러를 알려주는 프로토콜임.
RFC 792 에 정의되어 있음.
( 링크 : http://www.ietf.org/rfc/rfc792.txt )

IP(Internet Protocol)에는 오로지 패킷을 목적지에 도달시키기 위한 내용들로만 구성되어 있음. 따라서 정상적으로 목적지 호스트에 도달하는 경우에는 IP로서 통신을 성공하고 종료되므로 아무런 문제가 없음. 그러나 만일 전달해야 할 호스트가 꺼져 있거나 선이 단절될 경우 같은 비정상적인 경우에 이 패킷 전달을 의뢰한 출발지 호스트에 이러한 사유를 알려야 하지만 IP에는 그러한 에러에 대한 처리 방법이 명시되어 있지 않음. 이러한 IP의 부족한 점을 보안하기 위하여 사용되는 것이 바로 ICMP 임.

ICMP는 해당 호스트가 없거나 해당 포트에 대기 중인 서버 프로그램이 없는 등 에러 상황이 발생할 경우 IP 헤더에 기록되어 있는 출발지 호스트로 이러한 에러에 대한 상황을 보내주는 역할을 수행함. 물론 이 외에도 메시지를 제어하는 추가적인 기능들이 있음.

## ( 2 ) ICMP 패킷 구조

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/119f3063-42b9-432e-8169-895cbf3e4e7b)

8 바이트의 헤더와 데이터 부분으로 구성됨.
Type 필드 : ICMP 메시지 타입
Code 필드 : ICMP 메시지 타입별로 추가적인 코드 제공
Checksum 필드 : ICMP 헤더의 손상여부 확인
Data Section 필드 : 오류보고 및 질의에 따라서 다름


## ( 3 ) ICMP Type 유형

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><b><span lang="EN-US" style="font-size: 11pt;">Type</span></b><b><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></b></span></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><b><span lang="EN-US" style="font-size: 11pt;">Name</span></b><b><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></b></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">0</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span style="color: red;"><span lang="EN-US" style="font-size: 11pt;">Echo Reply (Echo&nbsp;</span><span style="font-size: 11pt;">응답<span lang="EN-US">)</span></span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">1</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Unassigned</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">2</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Unassigned</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace; font-size: 14.6667px;"><span style="color: red;">3</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Destination Unreachable (</span><span style="font-size: 11pt;">목적지 도달 불가<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">4</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Source Quench (Deprecated) (</span><span style="font-size: 11pt;">출발지 억제<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">5</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span style="color: red;"><span lang="EN-US" style="font-size: 11pt;">Redirect (</span><span style="font-size: 11pt;">경로 변경<span lang="EN-US">)</span></span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">6</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Alternate Host Address (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">7</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Unassigned</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">8</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Echo (Echo&nbsp;</span><span style="font-size: 11pt;">응답<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">9</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Router Advertisement</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">10</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Router Solicitation</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">11</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Time Exceeded (</span><span style="font-size: 11pt;">시간 초과<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">12</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Parameter Problem (</span><span style="font-size: 11pt;">파라미터 문제<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">13</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Timestamp (</span><span style="font-size: 11pt;">타임스탬프 요청<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">14</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Timestamp Reply (</span><span style="font-size: 11pt;">타임스탬프 응답<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">15</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Information Request (Deprecated) (</span><span style="font-size: 11pt;">정보 요청<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">16</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Information Reply (Deprecated) (</span><span style="font-size: 11pt;">정보 응답<span lang="EN-US">)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">17</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Address Mask Request (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="color: red; font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">18</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;"><span style="color: red;">Address Mask Reply (Deprecated)</span></span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">19</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Reserved (for Security)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">20-29</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Reserved (for Robustness Experiment)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">30</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Traceroute (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">31</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Datagram Conversion Error (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">32</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Mobile Host Redirect (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">33</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">IPv6 Where-Are-You (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">34</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">IPv6 I-Am-Here (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">35</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Mobile Registration Request (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">36</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Mobile Registration Reply (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">37</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Domain Name Request (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">38</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Domain Name Reply (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">39</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">SKIP (Deprecated)</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">40</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Photuris</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">41</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">ICMP messages utilized by experimental mobility
  protocols such as Seamoby</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">42-252</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Unassigned</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">253</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">RFC3692-style Experiment 1</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">254</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">RFC3692-style Experiment 2</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm; text-align: center;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">255</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" width="494"><div align="left" class="MsoNormal" style="line-height: normal; margin-bottom: 0.0001pt;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US" style="font-size: 11pt;">Reserved</span><span lang="EN-US" style="font-size: 11pt;"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

참고로 Type 은 그 기능에 따라 Qurey 와 Error 로 나뉘지며 몇몇 Type 은 고유의 필드 구조를 가짐.
\(참고 사이트 : http://www.ktword.co.kr/abbr_view.php?m_temp1=2405&m_search=I)
자세히 알고 싶다면 아래 두 사이트에서 참고하길 바람.
http://tools.ietf.org/html/rfc792
http://www.iana.org/assignments/icmp-parameters/icmp-parameters.xml

위 빨간색으로 된 Type 은 주요 Type 임.



## ( 4 ) ICMP 주요 Type 설명

Type 0, Type 8
IP 노드와 네트워크 간의 통신이 가능한지를 확인 하기 위해 사용됨.
Echo Request(0) 을 보내면 Echo Reply(8) 이 응답하는 방식으로 동작함.
(ex : ping 프로그램)

Type 3
IP 패킷이 목적지에 제대로 전달되지 않은 경우 일반적으로 라우터에게 탐지가 되는데 이때 라우터가 출발지 호스트에게 보낼때 사용됨.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Codes<o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Description<o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">0</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Net Unreachable (</span>네트워크 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">1</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Host Unreachable (</span>호스트 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">2</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Protocol Unreachable (</span>프로토콜 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">3</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Port Unreachable (</span>포트 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">4</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Fragmentation Needed and Don't
  Fragment was Set (</span>단편화 필요 및 단편화 안함<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">5</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Source Route Failed (</span>출발지 경로 선정 실패<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">6</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Destination Network Unknown (</span>목적지
  네트워크 알 수 없음<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">7</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Destination Host Unknown (</span>목적지 호스트
  알 수 없음<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">8</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Source Host Isolated (</span>출발지 호스트가 격리됨<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">9</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Communication with Destination Network
  is Administratively Prohibited (</span>목적지 네트워크 간의 통신이 관리상 금지<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">10</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Communication with Destination Host is
  Administratively Prohibited (</span>목적지 호스트 간의 통신이 관리상 금지<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">11</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Destination Network Unreachable for
  Type of Service (</span>서비스 유형에 대한 목적지 네트워크 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">12</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Destination Host Unreachable for Type
  of Service (</span>서비스 유형에 대한 목적지 호스트 미도달<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">13</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Communication Administratively
  Prohibited (</span>통신이 방화벽 때문에 관리상 금지<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">14</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Host Precedence Violation (</span>호스트 우선권
  위반<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">15</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Precedence cutoff in effect (</span>우선권의
  효력이 차단됨<span lang="EN-US">)</span></span></div>
</td>
 </tr>
</tbody></table>

Type 4
라우터에서 받는 패킷의 전송 속도가 보내는 전송 속도보다 클 경우 임시로 패킷을 버퍼에 임시로 저장을 하게 됨.
버퍼가 다 차버릴 경우 그 뒤에 받는 패킷은 버릴수 밖에 없게 됨.
그렇기 때문에 버퍼가 다 차기 전에 어느정도 버퍼를 비워줘야 하는데 그러기 위해 라우터에게 패킷을 보내는 호스트에게 패킷을 천천히 보낼 것을 요청을 해야 할 때 사용됨.

Type 5
좀 더 최적에 가까운 경로가 탐지 되었을 경우 패킷을 보내는 호스트에게 이를 알림으로 패킷이 좀 더 최적의 가까운 경로로 보내질 수 있도록 유도할 때 사용됨.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Codes<o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Description<o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">0</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Redirect for Network (</span>네트워크에 전송하기
  위한 최선의 방법이 아님<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">1</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Redirect for Host (</span>호스트에 전송하기 위한
  최선의 방법이 아님<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">2</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Redirect for Type of Service and
  Network (</span>목적지 네트워크에 대한 경로를 제공하지 않음<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">3</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Redirect for Type of Service and Host
  (</span>목적지 호스트에 대한 경로를 제공하지 않음<span lang="EN-US">)</span></span></div>
</td>
 </tr>
</tbody></table>

Type 9
라우터에서 동적으로 생성되어 있는 라우터를 탐지하기 위해 사용됨.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/e6bb2c83-c952-495d-9680-ac157f1b3704)

위 그림은 Type 9 의 패킷 구조임. (톡특한 구조!)
Num Addrs : 패킷을 발생시키는 라우터의 주소
Addr Entry Size : 라우터 주소에 대한 정보의 32 비트 워드 수
Lifetime : 라우터가 올바로 작동하고 있는지 신뢰할 수 있는 최대의 시간으로 명시된 시간이 지나면 자동으로 삭제됨.
Router Address : 응답한 라우터의 주소
Preference Level : 이 값이 클 수록 최적

Type 10
호스트에서 해당 지역에 존재하는 라우터 IP 주소를 획득하기 위해 사용됨.

Type 11
TTL값이 0이 되어 패킷을 폐기해야 하거나 단편화된 패킷이 모두 도달하지 않아 재조립이 불가능할 때  출발지 호스트에게 이를 알리기 위해 사용됨.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Codes<o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Description<o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">0</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Time to live Equals 0 During Transit
  (TTL </span>전송 시간 초과<span lang="EN-US">)</span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">1</span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Time to live Equals 0 During
  Reassembly (</span>단편화 재조립 시간 초과<span lang="EN-US">)</span></span></div>
</td>
 </tr>
</tbody></table>

Type 12
파라미터 문제가 발생시 사용됨

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Codes<o:p></o:p></span></span></b></div>
</td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<b><span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">Description<o:p></o:p></span></span></b></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">0<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">IP Header Bad (</span>옵션 분실<span lang="EN-US">)<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 90.45pt;" width="121"><div align="center" class="MsoNoSpacing" style="text-align: center;">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">1<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 370.75pt;" valign="top" width="494"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">IP Required Option Missing (</span>패킷 길이가
  좋지 않음<span lang="EN-US">)<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

Type 15, Type 16
저장매체가 없는 요청 호스트의 IP 주소를 알아내기 위해 사용됨.
RARP, BOOTP 또는 DHCP에서 사용할 것을 권장하고 있음.
Type 15 : 요청한 호스트의 IP 주소를 알기 위한 질문
Type 16 : 요청한 호스트이 IP 주소에 대한 응답

Type 17, Type 18
저장매체가 없는 특정 호스트가 서브넷 마스크를 획득하기 위해 사용됨.
Type 17 : 요청한 호스트의 서브넷 마스크를 알기 위한 질문
Type 18 : 요청한 호스트의 서브넷 마스크를 알기 위한 응답



( 5 ) ICMP 동작 방식

참고 사이트 : http://blog.daum.net/tlos6733/38
(저작권 문제시 삭제하겠습니다.)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/dc42f172-d92c-42cd-b457-e5504351f93c)

ICMP는 일반적으로 IP 메시지 전송에 대한 피드백을 제공하는 데 쓰임.
위 그림에서 장비 A는 장비 B에 IP 데이터그램을 송신하고자 가정할 때 데이터그램이 R2에 도달했을 때 어떤 문제가 발생하여 데이터그램이 손실됨.
라우터 R2는 ICMP 메시지를 장비 A에게 보내 문제가 발생했다는 사실을 알림.
이 때 가능하면 장비 A가 그 문제를 고치는 데 필요한 정보까지 같이 보냄.
라우터 R2는 오직 장비 A로만 ICMP 메시지를 송신할 수 있고, 라우터 R1이나 R3로는 송신할 수 없음.

ICMP 동작의 한가지 특성은 어떤 에러가 발생하여 ICMP를 통해 그 사실을 알릴 때, 오직 데이터그램의 최초 출발지로만 알릴 수 있다는 것!
사실 이것은 ICMP 동작 방법의 큰 단점임.
위의 그림에서 호스트A 가 호스트B에게 메시지를 보내는데 라우터 R2에서 데이터그램의 문제를 탐지했다고 하자.
라우터 R2는 그 문제가 이전에 메시지를 처리한 라우터 중 하나에서 (예를 들어 R1) 발생했다고 의심할 수 있지만 그 사실을 라우터 R1에게 보고할 수 없음.
R2는 ICMP 메시지를 오직 호스트 A로만 보낼 수 있음.

이러한 제한은 IP 동작 방식 때문에 생김.
IP 데이터그램 포맷에 있는 주소 필드는 오직 최초 출발지 주소와 최종 목적지 밖에 없음.
라우터 R2 가 라우터 R1 으로부터 데이터그램을 받았을 때 그 데이터그램 안에 들어있는 것은 오직 장비 A의 주소임.
그래서 라우터 R3 는 문제 보고를 장비 A 로만 송신해야 하며 장비 A 는 그 보고를 보고 어떻게 해야 할지 결정해야 함.
장비 A 는 사용하는 경로를 바꿀 수도 있고 관리자가 라우터 R1 이 문제를 해결하는 데 사용할 수 있는 에러 보고서를 생성할 수도 있음.

##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/icmp.html "Go koromoon"
