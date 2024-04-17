# shadow
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/02/passwd-shadow.html "Go koromoon"
##### 작성자: 김평일 대리
##### 작성일자: 2024년 4월 17일

</br>

## (1) /etc/shadow 파일 구조

</br>

`/etc/shadow`는 계정의 패스워드 정보와 계정의 만료기간, 비밀번호의 변경 일자등의 정보를 담고 있으며 루트 계정 이외의 계정은 읽을 수 없도록 설정되어 아무나 접근할 수 없음.

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/ead48255-97bf-4276-aa05-9ec2e1b37ba0)</div>
<div align="center">< shadow 파일 ></div></br>

</br>

**/etc/shadpw 파일 구조**</br>
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6ed95d49-b8e2-4777-ad5b-d0c43c2a0517)</div>

각 항목은 콜론 문자(:)에 의하여 구분되며 다음과 같은 의미를 가지고 있음</br>

1 : 사용자 계정</br>
2 : 패스워드를 암호화시킨 값($&#126;$&#126;$&#126; 3개의 부분으로 구성 : $id $salt $hashed 순서로 구성)</br>
&ensp;&emsp;패스워드를 암호화하는경우 본문의 E2loH6yC 와 같은 salt 값을 이용하여 암호화를 진행하게 됨.</br>
&ensp;&emsp;(::)이처럼 비어있는 경우에는 로그인시 패스워드가 불필요하다는 것을 뜻함.</br>
&ensp;&emsp;(:*:)이처럼 별표가 들어있는 경우에는 해당 계정을 막아두었다는 것을 뜻함.</br>
&ensp;&emsp;$ id : 해싱 알고리즘</br>
&ensp;&emsp;$ salt : 해싱에 사용된 솔트(salt)값</br>
&ensp;&emsp;$ hashed : 해싱된 비밀번호 값</br>
3 : 1970년 1월 1일부터 패스워드가 수정된 날짜의 일수를 계산한 값</br>
4 : 패스워드가 변경되기 전 최소사용기간(일수)</br>
&ensp;&emsp;0 인경우 언제든지 변경이 가능하다는 의미임.</br>
5 : 패스워드 변경 전 최대사용기간(일수)</br>
6 : 패스워드 사용 만기일 전 경고 메세지를 제공하는 일수</br>
7 : 로그인 접속 차단 일 수</br>
8 : 로그인 사용을 금지하는 일 수 (월/일/연)</br>
9 : 예약 필드로 사용되지 않음</br>

</br>
</br>

## (2) /etc/shadow 파일에서 2번째 항목은 패스워드 부분


</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/18dde9a2-9455-4879-9196-1bf205c9d7ab)</div>
</br><div align="center">< /etc/shadow 파일의 hashid 에 따른 해시 방법 ></div></br>

</br>

shadow는 패스워드 크랙에 있어서 주요한 개념이며 2번 패스워드 항목의 $ 구분자에서 다음과 같은 분류가 가능함.</br>

**$hashid $salt $hash value**</br>
HashID 는 어떤 Scheme 를 이용하여 Hash 하였는지를 보여주며 주로 많이 사용하는 HashID 는 $1, $5, $6 임.</br>

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/60962236-1639-411a-875c-59bc6e9dad83)</div>
<div align="center">< cript(Salt, 설정한 암호) ></div></br>

</br>
Salt 는 패스워드를 암호화하는데 있어서 OS 내에서 생성하는 임의의 값임.</br>
Salt 값과 설정한 암호를 Cript() 함수를 이용하여 암호화함.</br>
형식 : cript(Salt, 설정한 암호)</br>

passwd 명령어를 통해 설정한 암호를 동일한 암호로 변경한 후 shadow 파일을 확인해보면 값이 달라진 것을 확인할 수 있는데 이는 패스워드를 변경하는 명령어를 사용할 때마다 Salt 값이 변하기 때문임.</br>
따라서 패스워크 크랙하기 위해서는 Salt 값을 알아야 하며 해당 Salt 값을 모르면 레인보우 테이블을 가지고 있어도 의미가 없음.</br>

Hash Value 는 HashID 에 따른 해시 방법과 Salt 값을 가지고 암호화된 결과임.</br>

Hash 는 단방향 함수로 A -> B 는 가능하지만 B -> A 는 불가능한 함수이기 때문에, 해시를 하고 난 값을 가지고 해시하기 전의 값을 못 구하므로 이를 공격하기 위해서 레인보우 테이블이 필요함.</br>
레인보우 테이블은 모든 해시 쌍들을 구해놓은 것으로 이를 통해 해시값들을 대입하여 고속으로 패스워드 크랙을 시도함.</br>

</br>
</br>

## (3) shadow 패스워드와 관련된 리눅스 명령어

</br>

**pwconv 명령어**</br>
일반 패스워드에서 shadow 패스워드로 변경하는 명령어</br>
이 명령어가 수행되고 나면 /etc/passwd 의 내용 중 두 번째 필드에 있는 암호화된 패스워드 부분만이 /etc/shadow 파일에 따로 저장되게 됨.</br>

</br>

**pwunconv 명령어**</br>
shadow 패스워드에서 일반 패스워드로 되돌리는 명령어</br>
이 명령어는 /etc/shadow 파일에 보관되었던 패스워드를 다시 /etc/passwd 파일에 저장 하게 됨.</br>

</br>



