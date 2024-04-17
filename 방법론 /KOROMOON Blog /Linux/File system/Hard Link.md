# Hard Link
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2018/05/inode-symbolic-link-hard-link.html "Go KOROMOON"
##### 작성자: 김평일 대리
##### 작성일자: 2024년 4월 17일
</br>


## 하드 링크(Hard Link)

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/d09d66d2-986a-46bd-833e-d34474192c73)</div>


하드 링크는 디렉토리 구조에 대한 항목만 파일 생성되지만 원본 파일의 inode 위치를 가리킴.
즉, 하드 링크에는 새로운 inode 생성이 없으며 파일 시스템에 있는 데이터를 복사한 것이 아니라 inode 번호가 원본과 동일하기 때문에 파일 시스템 내의 데이터 자체가 여전히 1개만 존재함.
또한 하드링크 수정 시 원본도 수정되며, 원본파일을 삭제하는 경우 하드링크는 inode를 통하여 원본파일이 저장된 주소로 데이터를 찾아내어 원본파일이 지워지지 않고 유지됨.


하드 링크 생성 명령어
</br>
`ln [원본 파일] [링크 파일]`
</br>
