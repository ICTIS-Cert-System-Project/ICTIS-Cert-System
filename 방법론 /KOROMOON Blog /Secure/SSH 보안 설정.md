# SSH 보안 설정
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2021/12/ssh.html "Go KOROMOON"
##### 작성자: 김태현 사원
##### 작성일자: 2024년 4월 9일 
</br>

<div align="center"><img src="https://blogger.googleusercontent.com/img/a/AVvXsEgcMr3mHogFvhbp9imsxYa4iAJsyy51bv5eyni27jD_p2CYrAARqINW3ccccE8x3F88quPJUlMXXwKV8eUcRj1nGSBEIHuwH01PXP1DfqizuAHdSTRC-5P2EF534nAbahBeH4Ry4akfSOrSfdZhnS14f4SbVXrNFTDZzVfqX9wtRFk4mG1yrf3CsA6v=w640-h419"></div>

## (1) 강력한 사용자 이름과 비밀번호
- SSH를 실행하고 외부에 노출될 경우 공격자로부터 추측 가능한 사용자 이름과 비밀번호를 이용한 무차별 대입 공격 시도를 할 수 있음.
- 추측하지 못하도록 강력한 사용자 이름과 비밀번호를 설정해야 함.
- 특히 비밀번호는 대소문자, 특수문자, 숫자로 조합된 최소 8자리 이상으로 생성하길 바람.p>

## (2) 유휴 시간 초과 간격 구성
- SSH 세션의 무한한 시간을 방지하기 위해 유휴 초과 간격을 설정할 수 있음.
- `etc/ssh/sshd_config` 파일을 열고 다음 줄을 추가함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ClientAliveInterval 360<br>
  
  ClientAliveCountMax 0<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

- 설정 중인 유휴 시간 초과 간격은 초 단위임. (위 설정은 360초 = 6분)
- 간격이 지나면 유휴 사용자는 자동으로 로그아웃됨.

## (3) 비어있는 비밀번호 비활성화
- 보안 강화를 위해 비밀번호가 비어 있는 계정의 원격 로그인을 방지해야 함.
- `etc/ssh/sshd_congfig` 파일을 열고 다음 줄을 업데이트 함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">PermitEmptyPasswords no<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

## (4) 비인가 사용자의 SSH 접근 제한
- 원격 접속이 필요한 특정 사용자에게만 SSH 로그인을 허용함.
- 약한 암호를 사용하는 영향을 최소화할 수 있으며 SSH 접속 관리에 있어서도 용이함.
- `etc/ssh/sshd_config` 파일을 열어 `AllowUsers` 줄을 추가하고, 그 뒤에 허용할 사용자 이름 목록을 추가함. 참고로 공백으로 구분함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">AllowUsers user1 user2<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 SSH 서비스를 다시 시작함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">/etc/init.d/sshd restart<br>or<br>service sshd restart<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>


## (5) root 로그인 비활성화
- SSH 서비스에서 가장 위험한 보안 허점 중 하나로, root 계정이 직접 ssh 서버에 로그인하는 것을 허용하는 것임.
- 이렇게 하면 root 비밀번호에 대한 무차별 대입 공격을 시도하는 공격자에게 좋은 먹잇감이 됨.
- 만약 공격당한 경우 해당 시스템의 모든 권한을 얻게 되므로 가장 위험한 상황에 처하게 됨.

`etc/ssh/sshd_config` 파일에서 `PermitRootLogin` 줄을 찾아서 아래와 같이 변경해야 함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">PermitRootLogin no<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 SSHD 서비스를 다시 시작함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">/etc/init.d/sshd restart<br>or<br>service sshd restart<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

혹, ssh 서비스에서 root 계정 권한을 얻고 싶다면 일반 사용자 계정으로 ssh 서비스에 접속한 후 su 명령어를 이용하여 root 권한을 얻을 수 있음.

## (6) SSH 프로토콜 버전 2를 사용
- SSH에 사용할 수 있는 프로토콜은 버전 별로 1과 2가 있음.
- 프로토콜 버전 1은 더 오래되었고 보안상 취약하므로 버전 2만 사용해야함.
- 또한, 서버가 PCI와 호환되도록 하려면 프로토콜 버전 1을 비활성화해야 함.

`/etc/ssh/sshd_config` 파일을 열고 다음 행을 찾음.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">#Protocol 2, 1<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

1과 # 문자(주석처리)를 제거하여 다음과 같이 설정함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">Protocol 2<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 SSHD 서비스를 다시 시작함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">/etc/init.d/sshd restart<br>or<br>service sshd restart<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

## (7) 다른 포트 사용
- 대부분 공격자는 기본적은 SSH 서비스 포트인 22번 포트를 스캔 한 후 공격을 시도함.
- 만약 포트를 변경할 경우 공격 받을 가능성이 줄어듦.
- 그러나 잘 알려진 포트 외에 다른 포트를 선택해서 변경해야함.

포트를 변경하려면 `/etc/ssh/sshd_config` 파일을 열고 다음 행을 추가함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">#Run SSH on a non standard port<br>Port 2025 #Change me<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 SSHD 서비스를 다시 시작함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">/etc/init.d/sshd restart<br>or<br>service sshd restart<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

추가로 포트 변경 후에는 라우터 포트 포워딩과 방화벽 규칙을 설정하는 것을 잊으면 안됨. 그리고 변경된 사항에 대해서 사용자들에게 공지할 필요가 있음.

## (8) 특정 클라이언트만 허용
- 포트 22번에 대해 특정 IP 주소에서만 서버에 연결할 수 있도록 방화벽 규칙을 추가할 수 있음.
- 아래 규칙은 포트 22번으로 지정된 IP만 연결하도록 하는 iptables 규칙임.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ptables -A INPUT -p tcp -s [YourIP] --dport 22 -j ACCEPT<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

다음 규칙은 포트 22번에 대한 엑세스를 새로 시도할 때마다 IP 주소를 기록함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name ssh –rsource<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

또 다른 규칙은 특정 Ip 주소에서 90초 동안 3회 이상 연결을 시도했는지 확인하는 iptables 규칙임. 그렇지 않은 경우 패킷이 허용됨.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent ! --rcheck --seconds 90 --hitcount 3 --name ssh --rsource -j ACCEPT<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

방화벽에서 필터링하는 것은 SSH 서버에 대한 접근을 보호하는데 매우 유용한 방법임.

## (9) 이중 인증 활성화
- 서비스 비용을 투자할 수 있다면 SSH 서버에 2단계 인증이 구성된 보안을 유지하는게 좋음.
- 각 사용자 로그인은 구성된 2FA 사용자와 연결되어야 하므로 무단 접근으로부터 SSH 보호하는데 탁월함.
- 공격자가 특정 사용자의 게정 정보를 알아내거나 SSH 서버에 침입하더라도 2FA 기능에 의해 차단됨

## (10) 인증을 위해 공개/개인키 사용
- 공개/개인키 인증은 암호 인증보다 더 안전하고 효과적인 방법임.
- 각 키는 각기 다른 수학적 속성을 가진 숫자로 이루어짐.
- 개인키는 SSH 서버에 저장되고 공개키는 사용자 컴퓨터의 .ssh/authorized_keys 파일에 저장됨.
<br><br>
- 이는 외부로부터 공개된 인터넷상에서 특히 중요함.
- 인증에 암호화된 키를 사용하면 더 이상 일반적인 암호를 입력할 필요가 없으므로 유용함.
- 공개/개인 키 쌍 인증이 서버에 구성되면 암호 인증을 완전히 비활성화할 수 있음.
- 이는 인증된 키가 없는 사람은 접근 권한을 얻을 수 없음을 의미함.
<br>
- 공격자가 통신 중 세션을 방해하거나 몰래 잠입할 수 없으며 더 이상 무차별 대입 공격이 무의미함.
<br>
- 공격/개인 키 쌍을 만들고 SSh 서버에서 사용하기 위해 설치하는 방법은 다음과 같음.
- 키 쌍, 즉 공개키와 개인키를 생성하여 시작함.
- 공개키는 서버에서 배치하고 개인키로 로그인함.
- 이는 연결하는 각 클라이언트 시스템에서 수행해야 함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">$ ssh-keygen -t rsa<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

- 위와 같이 멍령어를 입력하면 ~/.ssh 디렉토리에 id_rsa 및 rsa.pub라는 두 개의 파일이 생성됨.
- id_rsa는 개인키이고 id_rsa.pub는 공개키임.

<br>
- 그런 다음 연결할 때마다 주어진 공개키를 잠금 해제하기 위한 암호를 입력하라는 메시지가 표시됨.
- 키를 생성할 때 암호 보호 암호화를 키에 추가하는 것은 사용자의 선택임.
- 하나를 사용하지 않으려면 키 쌍을 만들 때 암호를 묻는 메시지가 표시될 때 Enter 키를 누르기만 하면 됨.
- 암호로 키를 보호하지 않으면 SSh 서버에 접근하는 모든 사람이 자동으로 SSh 접근 권한을 갖게 됨.

<br>
- 공개키(id_rsa.pub)를 서버에 복사함.
- 원격 사용자는 절대 루트가 아니어야 함. 기본 루트가 아닌 사용자는 원격 사용자로 선택함.


<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">Scp -p id_rsa.pub remoteuser@remotehost:<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 SSH로 로그인하고 공개키를 올바른 위치에 복사함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">ssh remoteuser@remotehost mkdir ~/.ssh chmod 700 ~/.ssh cat id_rsa.pub >> ~/.ssh/authorized_keys chmod 600 ~/.ssh/authorized_keys mv id_rsa.pub ~/.ssh logout<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

그런 다음 서버에서 공개 키를 삭제함.
그렇지 않으면 SSH 클라이언트에서 서버에 로그인할 수 없음.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">rm id_rsa.pub<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

마지막으로 서버에서 파일 권한을 설정함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;">$ chmod 700 ~/.ssh<br>$ chmod 600 ~/.ssh/authorized_keys<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

`etc/ssh/sshd.config` 파일에서 `StrictModes` 가 `yes`로 설정되어 있으면 위의 권한이 필요함.

서버에 로그인할 때 키 암호를 입력하라는 메시지가 표시됨. (구성에 따라 다름)

공개/개인 키를 사용하여 성공적으로 로그인할 수 있음을 확인한 후 비밀번호 인증을 완전히 비활성화할 수 있음.
`/etx/ssh/ssh_config` 파일을 열고 다음 행을 추가.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="border: 1pt solid windowtext; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt; width: 461.2pt;" valign="top" width="615">
  <p align="left" class="MsoNoSpacing"><i><span lang="EN-US"><span style="font-family: courier;"># Disable password authentication forcing use of keys<br>PasswordAuthentication no<o:p></o:p></span></span></i></p>
  </td>
 </tr>
</tbody></table>

참고 사이트:<br>[https://blog.devolutions.net/2017/04/10-steps-to-secure-open-ssh/](https://blog.devolutions.net/2017/04/10-steps-to-secure-open-ssh/)
