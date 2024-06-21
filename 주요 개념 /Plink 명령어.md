# Plink 명령어
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2019/02/plink.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 15일 


## (1) 설명

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ec0f898f-be5b-4db9-9352-aab6d59b0bf1)

Plink 는 PuTTY 제품군 하나로 임의의 포트를 사용하여 다른 시스템에 대한 SSH 네트워크 연결을 설정하는 데 사용하는 툴임.  
PuTTY 홈페이지 : [https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)  
  
  
  
## **( 2 ) 사용법**  
  
C:\Program Files\PuTTY>plink.exe  
  
Plink: 명령어 라인 연결 유틸리티  
Release 0.70  
  
사용법: plink [options] [user@]host [command]  
       ("host" 는 세션 이름으로 저장된 PuTTY 일 수도 있음)  
  
옵션 :  
  -V        버전 정보를 출력하고 종료함  
  -pgpfp    PGP 키 지문을 인쇄하고 종료함  
  -v        자세한 메시지 표시  
  -load sessname  저장된 세션의 설정로드  
  -ssh -telnet -rlogin -raw -serial  
            특정 프로토콜의 강제 사용  
  -P port   지정된 포트에 연결  
  -l user   지정된 사용자 이름으로 연결  
  -batch    모든 대화형 프롬프트 비활성화  
  -proxycmd command  
            명령어를 로컬 프록시로 사용  
  -sercfg configuration-string (e.g. 19200,8,n,1,X)  
            직렬 구성 지정 (직렬 전용)  
다음 옵션은 SSH 연결에만 적용됨 :   
  -pw passw 지정된 비밀번호로 로그인  
  -D [listen-IP:]listen-port  
            동적 SOCKS 기반 포트 포워딩  
  -L [listen-IP:]listen-port:host:port  
            로컬 포트를 원격 주소로 전달  
  -R [listen-IP:]listen-port:host:port  
            원격 포트를 로컬 주소로 전달  
  -X -x     X11 포워딩 활성화 / 비활성화  
  -A -a     에이전트(agent) 포워딩 활성화 / 비활성화  
  -t -T     pty 할당 활성화 / 비활성화  
  -1 -2     특정 프로토콜 버전 강제 사용  
  -4 -6     IPv4 또는 IPv6 강제 사용  
  -C        압축 허용  
  -i key    사용자 인증을 위한 개인 키 파일  
  -noagent  Pageant 사용 중지  
  -agent    Pageant 사용 가능  
  -hostkey aa:bb:cc:...  
            수동으로 호스트키를 지정 (반복될 수 있음)  
  -m file   파일로부터 원격 명령 읽기  
  -s        원격 명령은 SSH 서브 시스템 (SSH-2 전용)  
  -N        쉘 / 명령어를 시작하지 않기 (SSH-2 전용)  
  -nc host:port  
            세션 대신 오픈 터널 (SSH-2 전용)  
  -sshlog file  
  -sshrawlog file  
            로그 프로토콜 세부 정보를 파일에 기록  
  -shareexists  
            연결 공유 업스트림의 존재 여부 테스트  
  
Plink 0.70 버전에서 확인함.  
  
## **( 3 ) 사용예**  
  
원격 SSH 호스트에 명령어 입력하기  
(plink.exe 유저이름@호스트주소 -m 수행할명령어가담긴파일 -pw 비밀번호)  
plink koromoon@hacker.com -m commands.txt -pw koromoon1004  
  
포트 포워딩  
(공격자 PC:4444 ---> 중개 PC:SSH ---> 피해자 PC:3389)  
plink.exe [중개 PC] -P 22 -C -L 127.0.0.1:4444:[피해자 PC]:3389 -l 계정명 -pw 암호  

참고 사이트 :   
[http://hkashfi.blogspot.com/2008/04/bypassing-firewalls-with-port_23.html](http://hkashfi.blogspot.com/2008/04/bypassing-firewalls-with-port_23.html)
