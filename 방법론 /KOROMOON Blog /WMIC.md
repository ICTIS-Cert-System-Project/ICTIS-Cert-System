# WMIC
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/11/wmic.html "Go koromoon"
##### 작성자: 김평일 대리
##### 작성일자: 2024년 4월 18일

<br>
<br>

## (1) WMIC 명령어

WMI(Windows Management Instrumentation)란 엔터프라이즈 네트워크에서 관리정보를 액세스하고 공유하는 표준을 만들기 위하여 Microsoft에서 구현한 것을 말함.
WMIC(Windows Management Instrumentation Command-line)란 WMI에 대한 간단한 명령줄 인터페이스를 제공하므로 WMI를 사용하여 윈도우를 실행하는 컴퓨터를 관리하는 명령어임.<br>
Shell 및 유틸리티 명령과 상호 작용하여 한 컴퓨터부터 다수의 컴퓨터까지 원격으로 관리할 수 있으며 관리 스크립팅을 통하여 자동화까지 가능함.<br>
WMIC는 기본적으로 Windows XP 이상에서만 로드됨.<br>

<br>
<br>

## (2) WMIC 명령어 도움말

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/0238e315-bef1-4a15-bb29-cb108d72647a)</div>

<br>

다음 전역 스위치를 사용할 수 있음<br>

|명령어|설명|
|---------------------------|------------------|
|/NAMESPACE&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|별칭이 작동하는 네임 스페이스의 경로&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|
|/ROLE|별칭 정의가 들어있는 역할의 경로|
|/NODE|별칭 서버가 작동함.|
|/IMPLEVEL|클라이언트 가장(impersonation) 레벨|
|/AUTHLEVEL|클라이언트 인증 레벨|
|/LOCALE|클라이언트가 사용해야 하는 언어 ID|
|/PRIVILEGES|모든 권한을 사용 또는 미사용 설정|
|/TRACE|stderr 에 대한 디버깅 정보를 출력함.|
|/RECORD|모든 입력 명령 및 출력을 기록함.|
|/INTERACTIVE|대화식 모드를 설정하거나 재설정함.|
|/FAILFAST|FailFast 모드를 설정하거나 재설정함.|
|/USER|세선 중에 사용되는 사용자|
|/PASSWORD|세선 로그인에 사용할 암호|
|/OUTPUT|출력 경로 재지정을 위한 모드를 저정함.|
|/APPEND|출력 경로 재지정을 위한 모드를 저정함.|
|/AGGREGATE|집계 모드를 설정 또는 재설정함.|
|/AUTHORITY|연결에 대한 <권한 타입> 을 지정함.|
|/?[:<BRIEF|FULL>]|사용 정보|

<br>

특정 글로벌 스위치에 대한 자세한 내용을 보려면 다음을 입력 : switch-name /?<br>

<br>

|명령어|설명|
|------|---|
|ALIAS|로컬 시스템에서 사용 가능한 별칭에 대한 액세스|
|BASEBOARD|베이스 보드(마더 보드 또는 시스템 보드) 관리|
|BIOS|기본 입/출력 서비스(BIOS) 관리|
|BOOTCONFIG|부팅 구성 관리|
|CDROM|CD-ROM 관리|
|COMPUTERSYSTEM|컴퓨터 시스템 관리|
|CPU|CPU 관리|
|CSPRODUCT|SMBIOS 의 컴퓨터 시스템 제품 정보|
|DATAFILE|데이터파일(DataFile) 관리|
|DCOMAPP|DCOM 응용 프로그램 관리|
|DESKTOP|사용자의 데스크톱 관리|
|DESKTOPMONITOR|데스크톱 모니터 관리|
|DEVICEMEMORYADDRESS|장치 메모리 주소 관리|
|DISKDRIVE|물리적 디스크 드라이브 관리|
|DISKQUOTA|NTFS 볼륨의 디스크 공간 사용|
|DMACHANNEL|직접 메모리 액세스(DMA) 채널 관리|
|ENVIRONMENT|시스템 환경 설정 관리|
|FSDIR|파일 시스템 디렉토리 항목 관리|
|GROUP|그룹 계정 관리|
|IDECONTROLLER|IDE 컨트롤러 관리|
|IRQ|인터럽트 요청 라인(IRQ) 관리|
|JOB|일정 서비스를 사용하여 예약된 작업에 대한 액세스를 제공|
|LOADORDER|실행 의존성을 정의하는 시스템 서비스의 관리|
|LOGICALDISK|로컬 저장 장치 관리|
|LOGON|로그온 세션|
|MEMCACHE|캐시 메모리 관리|
|MEMORYCHIP|메모리 칩 정보 제공|
|MEMPHYSICAL|컴퓨터 시스템의 물리적 메모리 관리|
|NETCLIENT|네트워크 클라이언트 관리|
|NETLOGIN|(특정 사용자의) 네트워크 로그인 정보 관리|
|NETPROTOCOL|프로토콜(및 해당 네트워크 특성) 관리|
|NETUSE|활성 네트워크 연결 관리||
|NIC|네트워크 인터페이스 컨트롤러(NIC) 관리|
|NICCONFIG|네트워크 어댑터 관리|
|NTDOMAIN|NT 도메인 관리|
|NTEVENT|NT 이벤트 로그의 항목|
|NTEVENTLOG|NT 이벤트 로그 파일 관리|
|ONBOARDDEVICE&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|마더 보드(시스템 보드)에 내장된 일반 어댑터 장치의 관리|
|OS|설치된 운영 체제 관리|
|PAGEFILE|가상 메모리 파일 스와핑 관리|
|PAGEFILESET|페이지 파일 설정 관리|
|PARTITION|물리적 디스크의 파티션된 영역 관리|
|PORT|입출력 포트 관리|
|PORTCONNECTOR|물리적 연결 포트 관리|
|PRINTER|프린터 장치 관리|
|PRINTERCONFIG|프린터 장치 구성 관리|
|PRINTJOB|작업 관리를 인쇄|
|PROCESS|프로세스 관리|
|PRODUCT|설치 패키지 작업 관리|
|QFE|빠른 수정 엔지니어링|
|QUOTASETTING|볼륨의 디스크 할당량에 대한 설정 정보|
|RDACCOUNT|원격 데스크톱 연결 권한 관리|
|RDNIC|특정 네트워크 어댑터의 원격 데스크톱 연결 관리|
|RDPERMISSIONS|특정 원격 데스크톱 연결에 대한 사용 권한|
|RDTOGGLE|원격 데스크톱 수신기를 원격으로 켜고 끔|
|RECOVEROS|운영 체제가 실패할 때 메모리에서 수집되는 정보|
|REGISTRY|컴퓨터 시스템 레지스트리 관리|
|SCSICONTROLLER|SCSI 컨트롤러 관리|
|SERVER|서버 정보 관리|
|SERVICE|서비스 응용 프로그램 관리|
|SHADOWCOPY|섀도 복사본(Shadow Copy) 관리|
|SHADOWSTORAGE|섀도 복사본(Shadow Copy) 저장 영역 관리|
|SHARE|공유 자원 관리|
|SOFTWAREELEMENT|시스템에 설치된 소프트웨어 제품 요소의 관리|
|SOFTWAREFEATURE|SoftwareElement 의 소프트웨어 제품 하위 집합 관리|
|SOUNDDEV|사운드 장치 관리|
|STARTUP|사용자가 컴퓨터 시스템에 로그온할 때 자동으로 실행되는 명령어의 관리|
|SYSACCOUNT|시스템 계정 관리|
|SYSDRIVER|기본 서비스를 위한 시스템 드라이버 관리|
|SYSTEMENCLOSURE|물리적 시스템 인클로저 관리|
|SYSTEMSLOT|포트, 슬롯, 주변 장치 및 독점적인 연결 지점을 포함한 물리적 연결 지점 관리|
|TAPEDRIVE|테이프 드라이브 관리|
|TEMPERATURE|온도 센서(전자 온도계)의 데이터 관리|
|TIMEZONE|시간대 데이터 관리|
|UPS|무정전 전원 공급 장치(UPS) 관리|
|USERACCOUNT|사용자 계정 관리|
|VOLTAGE|전압 센서(전자 전압계) 데이터 관리|
|VOLUME|로컬 스토리지 볼륨 관리|
|VOLUMEQUOTASETTING|디스크 할당량 설정을 특정 디스크 볼륨과 연관|
|VOLUMEUSERQUOTA|사용자 별로 저장 용량 할당량 관리|
|WMISET|WMI 서비스 운영 매개 변수 관리|

<br>

특정 별칭에 대한 자세한 내용을 보려면 다음을 입력 : alias /?<br>

<br>

|명령어|설명|
|------|---|
|CLASS|전체 WMI 스키마로 이스케이프(Escapes)|
|PATH|전체 WMI 개체 경로로 이스케이프(Escapes)&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|
|CONTEXT|모든 글로벌 스위치의 상태를 표시|
|QUIT/EXIT&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;|프로그램 종료|

<br>

CLASS/PATH/CONTEXT 에 대한 자세한 내용은 다음을 입력 : (CLASS | PATH | CONTEXT) /?<br>

<br>
<br>

## (3) WMIC 명령어 사용예

공격자가 원격 PC에서 WMIC 명령어를 사용하여 막대한 양의 정보를 열거하거나 명령어 실행 등을 할 수 있음.


