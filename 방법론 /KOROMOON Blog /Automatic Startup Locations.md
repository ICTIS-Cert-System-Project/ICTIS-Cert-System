# 윈도우 자동 시작 위치
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2019/01/blog-post_18.html "Go koromoon"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 24일

</br>


참고 사이트 : [http://www.ghacks.net/2016/06/04/windows-automatic-startup-locations/](http://www.ghacks.net/2016/06/04/windows-automatic-startup-locations/)




![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/5cbdac21-1a53-4114-9e10-15e328eaaf5f)

< Autoruns 툴 >

윈도우 자동 시작 기능을 이용하여 관리 작업에 유용하게 쓰일 수 있지만 악성코드에서는 악의적으로 쓰일 수 있음.  
해당 기능을 알아보고자 아래 내용들을 조사하였으며 포렌식이나 악성코드 분석에 있어서 필요한 개념이므로 숙지 바람.  
참고로 자동 시작 분석에 유용한 툴로는 Autoruns 툴이 있음.  
( Autoruns 다운로드 위치 : [https://technet.microsoft.com/en-us/sysinternals/bb963902.aspx](https://technet.microsoft.com/en-us/sysinternals/bb963902.aspx) )  
  
  
  
## **( 1 ) 윈도우 자동 시작 폴더 위치**

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/3089912c-d87e-4620-b5ca-6d47993ef751)

< 윈도우 시작 메뉴를 통해 시작프로그램 확인 >

  
해당 위치에 악성코드 파일이 있는 경우가 있으며 윈도우 시작 메뉴를 통해서도 확인할 수 있음.  
  
현재 사용자의 자동 시작 폴더  


   %appdata%\Microsoft\Windows\Start Menu\Programs\Startup<br><br>C:\Users\USERNAME\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

  
모든 사용자의 자동 시작 폴더  


   %programdata%\Microsoft\Windows\Start Menu\Programs\Startup<br><br>C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp

  
  
  
## **( 2 ) 윈도우 자동 시작 레지스트리 위치**  
  
자동 시작 위치의 대부분은 윈도우 레지스트리에서 발견됨.  
참고로 레지스트리 편집기 열기 : 시작 -> 실행(단축키 : Windows + R) -> regedit 입력, 명령 프롬프트에서 regedit 입력  
  
개인 사용자 레지스트리 키  


   HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run<br><br>HKCU\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run (64 비트 시스템)<br>    <br>              HKCU\Software\Microsoft\Windows NT\CurrentVersion\Windows\Run<br><br>HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce<br><br>  <br><br>(한 번만 프로그램     및 명령 실행, 즉시 실행이 되어야 클리어)<br><br>HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnceEx<br><br>  <br><br>(한 번만 프로그램 및 명령 실행, 실행 완    료가 되어야 클리어)<br><br>HKCU\Software\Microsoft\Windows\CurrentVersion\RunServices<br><br>HKCU\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce|

  
모든 사용자 레지스트리 키  


    HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run<br><br>HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run (64 비트 시스템)<br>                      <br>HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce<br><br>  <br><br>(한 번만 프로그램 및 명령 실행, 즉시 실행이 되어야 클리어)<br>             <br>         HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnceEx<br><br>  <br><br>(한 번만 프로그램 및 명령 실행, 실행 완료가 되어야 클리어)<br>    <br>                    HKLM\System\CurrentControlSet\Services<br><br>HKLM\Software\Microsoft\Windows\CurrentVersion\RunServices<br>   <br>                                                HKLM\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce

  
  
  
## **( 3 ) 기타 윈도우 자동 시작 레지스트리 위치**   
  
Active 설치가 로그온하는 동안 사용자당 한번 명령을 실행하도록 설계됨.  


   HKLM\SOFTWARE\Microsoft\Active Setup\Installed Components<br><br>HKLM\SOFTWARE\Wow6432Node\Microsoft\Active Setup\Installed Components

  
문서화되지 않은 자동 시작 기능  


   HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\SharedTaskScheduler<br>         <br>HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\SharedTaskScheduler

  
쉘 자동 시작 항목 (ex. 관련 파일이나 폴더를 마우스 오른쪽 버튼으로 클릭 시 항목이 표시되는 기등 등)  

|   |
|---|
|HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellServiceObjects<br><br>HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\ShellServiceObjects<br><br>HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\ShellServiceObjectDelayLoad<br><br>HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ShellServiceObjectDelayLoad<br><br>HKCU\Software\Classes\*\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Wow6432Node\Classes\*\ShellEx\ContextMenuHandlers<br><br>HKCU\Software\Classes\Drive\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Drive\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Classes\*\ShellEx\PropertySheetHandlers<br><br>HKLM\Software\Wow6432Node\Classes\*\ShellEx\PropertySheetHandlers<br><br>HKCU\Software\Classes\Directory\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Classes\Directory\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Directory\ShellEx\ContextMenuHandlers<br><br>HKCU\Software\Classes\Directory\Shellex\DragDropHandlers<br><br>HKLM\Software\Classes\Directory\Shellex\DragDropHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Directory\Shellex\DragDropHandlers<br><br>HKLM\Software\Classes\Directory\Shellex\CopyHookHandlers<br><br>HKCU\Software\Classes\Directory\Background\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Classes\Directory\Background\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Directory\Background\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Classes\Folder\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Folder\ShellEx\ContextMenuHandlers<br><br>HKLM\Software\Classes\Folder\ShellEx\DragDropHandlers<br><br>HKLM\Software\Wow6432Node\Classes\Folder\ShellEx\DragDropHandlers<br><br>HKLM\Software\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers<br><br>HKLM\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers|

  
아래 키가 시작하는 동안 로드되는 드라이버를 지정함.  

|   |
|---|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Font Drivers<br><br>HKLM\Software\Microsoft\Windows NT\CurrentVersion\Drivers32<br><br>HKLM\Software\Wow6432Node\Microsoft\Windows NT\CurrentVersion\Drivers32|

  
기타 시작 키  

|   |
|---|
|HKLM\Software\Classes\Filter<br><br>HKLM\Software\Classes\CLSID\{083863F1-70DE-11d0-BD40-00A0C911CE86}\Instance<br><br>HKLM\Software\Wow6432Node\Classes\CLSID\{083863F1-70DE-11d0-BD40-00A0C911CE86}\Instance<br><br>HKLM\Software\Classes\CLSID\{7ED96837-96F0-4812-B211-F13C24117ED3}\Instance<br><br>HKLM\Software\Wow6432Node\Classes\CLSID\{7ED96837-96F0-4812-B211-F13C24117ED3}\Instance<br><br>HKLM\System\CurrentControlSet\Control\Session Manager\KnownDlls<br><br>HKCU\Control Panel\Desktop\Scrnsave.exe<br><br>HKLM\System\CurrentControlSet\Services\WinSock2\Parameters\Protocol_Catalog9\Catalog_Entries<br><br>HKLM\System\CurrentControlSet\Services\WinSock2\Parameters\Protocol_Catalog9\Catalog_Entries64|

  
  
  
## **( 4 ) 윈도우 자동 시작 그룹 정책 위치**

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/80a0e317-2fe0-45e7-889f-89a3d5a1c6e8)

< 로컬 그룹 정책 편집기 >

  
정책과 관련된 레지스트리 키는 모든 버전에서 사용할 수 있지만, 로컬 그룹 정책 편집기는 윈도우 Pro 버전 이상에서만 사용할 수 있음.  
참고로 로컬 그룹 정책 편집기 열기 : 시작 -> 실행(단축키 : Windows + R) -> gpedit.msc 입력, 명령 프롬프트에서 gpedit.msc 입력  
로컬 그룹 정책 편집기에서 아래 위치에 있음.  

|   |
|---|
|컴퓨터 구성 -> 관리 템플릿 -> 시스템 -> 로그온 -> 사용자 로그온할 때 다음 프로그램 실행<br><br>사용자 구성 -> 관리 템플릿 -> 시스템 -> 로그온 -> 사용자 로그온할 때 다음 프로그램 실행|

  
위 위치와 관련된 레지스트리 키는 다음과 같음.  

|   |
|---|
|HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run<br><br>HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run|

  
  
  
## **( 5 ) 윈도우 자동 시작 작업 위치**

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/042d2f12-1fe6-4ca5-81fe-8174ef8cbaf4)

< 작업 스케줄러 >

  
작업 스케줄러에서 확인하거나 Tasks 폴더에서 확인할 수 있음.  

|   |
|---|
|작업 스케줄러 열기 : 시작 -> 실행(단축키 : Windows + R) -> Taskschd.msc 입력, 명령 프롬프트에서 Taskschd.msc 입력<br><br>C:\Windows\Tasks<br><br>C:\Windows\System32\Tasks|

  
  
  
## **( 6 ) 윈도우 자동 시작 파일 위치**  
  
다음 파일은 윈도우 시작 시 프로그램을 자동으로 시작하는 데 사용할 수 있음.  

|   |
|---|
|c:\autoexec.bat<br><br>c:\config.sys<br><br>c:\windows\winstart.bat<br><br>c:\windows\wininit.ini<br><br>c:\windows\dosstart.bat<br><br>c:\windows\system.ini<br><br>c:\windows\win.ini<br><br>c:\windows\system\autoexec.nt<br><br>c:\windows\system\config.nt|

  
  
  
아래 사이트는 자동 시작과 관련된 특정 레지스트리 키에 대한 자세한 정보를 제공함.  
  
Active Setup Explained  
[https://helgeklein.com/blog/2010/04/active-setup-explained/](https://helgeklein.com/blog/2010/04/active-setup-explained/)  
Active Setup Registry Key  
[https://blogs.msdn.microsoft.com/aruns_blog/2011/06/20/active-setup-registry-key-what-it-is-and-how-to-create-in-the-package-using-admin-studio-install-shield/](https://blogs.msdn.microsoft.com/aruns_blog/2011/06/20/active-setup-registry-key-what-it-is-and-how-to-create-in-the-package-using-admin-studio-install-shield/)  
Bleeping Computer on Windows Autostart  
[http://www.bleepingcomputer.com/tutorials/windows-program-automatic-startup-locations/](http://www.bleepingcomputer.com/tutorials/windows-program-automatic-startup-locations/)  
Registering File Handlers  
[https://msdn.microsoft.com/en-us/library/windows/desktop/dd940433(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/desktop/dd940433(v=vs.85).aspx)  
The Windows 7 Boot Process  
[http://social.technet.microsoft.com/wiki/contents/articles/11341.the-windows-7-boot-process-sbsl.aspx](http://social.technet.microsoft.com/wiki/contents/articles/11341.the-windows-7-boot-process-sbsl.aspx)  
Understand and Control Startup Apps with the System Configuration Utility  
[https://technet.microsoft.com/en-us/magazine/ee851671.aspx](https://technet.microsoft.com/en-us/magazine/ee851671.aspx)
