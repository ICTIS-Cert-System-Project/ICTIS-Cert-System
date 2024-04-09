 SSH 보안 설정
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
