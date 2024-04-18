# findstr
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/03/findstr.html "Go koromoon"
##### 작성자: 김평일 대리
##### 작성일자: 2024년 4월 18일

<br>
<br>

## (1) 설명

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/e0d96175-f3db-430b-9969-d40aa12a6b25)</div>

**파일에서 문자열을 찾습니다.**</br>


</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/781da852-16e3-4f57-a75d-f450323a4215)</div>


/C 옵션을 사용한 경우가 아니면, 찾는 문자열을 여러 개 지정할 때 공백으로 분리하십시오.</br>

예를 들면, 'FINDSTR "hello there" x.y' 명령을 입력하면 파일 x.y에서 "hello"나 "there"을 찾습니다.</br>
반면에 'FINDSTR /C:"hello there" x.y' 명령을 입력하면 파일 x.y에서 "hello there"을 찾습니다.</br>

**정규식에 대한 참고 사항**</br>


</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/504ec4b7-e369-4907-abde-65dc61e1d092)</div>

<br>
<br>

## (2) 사용예

test.txt 파일에서 koromoon 문자열 검색
findstr koromoon test.txt

test.txt 파일에서 koromoon 으로 사작해서 jjang 로 끝나는 문자열 검색
findstr koromoon.*jjang test.txt

test.txt 파일에서 첫 문구에서 koromoon 으로 시작하는 문자열 검색
(앞에 특수 문자열이 있는 것도 출력됨. 순수 koromoon... 으로 시작하는 문자열은 따로 못빼는 것으로 확인됨. ㅠㅠ)
findstr ^koromoon test.txt

test.txt 파일에서 첫 문구에서 <koromoon 으로 시작하는 문자열 검색
findstr ^<koromoon test.txt

현재 위치한 디렉토리의 모든 파일에서 koromoon 문자열 검색
(여기서 /N 옵션은 줄번호를 출력함)
findstr /N koromoon *

현재 위치한 디렉토리의 모든 txt 파일에서 koromoon 문자열 검색
findstr /N koromoon *.txt

C 드라이브 전체에서 대소문자 koromoon 문자열 검색
(여기서 /S 옵션은 하위 디렉토리를 포함시키는 옵션이며 /I 옵션은 대소문자를 구분하지 않는 옵션임)
findstr /S /I koromoon C:\*.*

현재 위치의 하위 폴더까지 포함된 전체 파일에서 대소문자 구분없이 koromoon 문자열 검색
findstr /S /N /I koromoon *





























