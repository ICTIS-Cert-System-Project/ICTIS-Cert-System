# passwd

| 작성자       | 김평일 대리   |
| --------- | ---------------- |
| **작성 일자** | **2024년 4월 17일** |
| **수정 일자** |                  |
| **비고**    |                  |

</br>

## /etc/passwd 파일 구조

</br>

/etc/passwd 은 시스템에 로그인하는 사용자 계정을 관리하는 text 파일임.</br>
root 계정 뿐만 아니라 다른 계정에게도 읽기 권한이 있어 누구나 읽을 수 있지만, 수정은 root 만 가능함.</br>

</br>

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/45b7b49f-893d-48e4-86e1-4561a9ac5d8d)</div>
<div align="center">< passwd 파일 ></div>


</br>
</br>

</br>**/etc/passwd 파일 기본구조**</div></br>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/94a44f66-5ddf-4dbe-84d9-679e3cb6af1d)</br>

</br>

각 항목은 콜론 문자(:)에 의하여 구분되며 다음과 같은 의미를 가지고 있음.</br>
(1) 사용자 계정</br>
(2) 사용자 패스워드. x 문자가 들어있는 경우 패드워드 정보는 암호화 되어 `/etc/shadow` 파일에 저장됨.</br>
(3) 사용자 ID를 의미하며 root 의 경우 0임.</br>
(4) 사용자가 속한 그룹 ID를 의미하며 root의 경우 0 . 대부분의 경우 그룹 ID와 사용자 ID가 같음.</br>
(5) 사용자 코멘트 정보</br>
(6) 사용자 홈 디렉터리</br>
(7) 사용자가 기본으로 사용하는 Shell 정보</br>

</br>

##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/02/passwd-shadow.html "Go koromoon"
