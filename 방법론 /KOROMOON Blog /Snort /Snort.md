# Snort 규칙 헤더 및 옵션 정보 _(Snort Rule Header & Option Information)_
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][KOROMOONlink]
[KOROMOONlink]: https://koromoon.blogspot.com/2020/10/snort-snort-rule-header-option.html "Go KOROMOON"
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 4월 3일 
</br>

## (1) 기본 사항
- Snort 는 유연하면서 강력한 그리고 간단한 규칙 기술 언어를 사용함.
- 대부분의 Snort 규칙은 한 줄로 작성됨.
- 1.8 버전 이상에서는 줄 끝 부분에 백슬래시(\)를 추가하여 규칙을 여러 줄로 확장할 수 있음.
- *규칙이 길지 않은 이상 가독성을 위해서 한 줄로 작성하는 걸 추천함.*
</br>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/5fcd3392-0a88-4e3a-bb37-7930e363348f) </br>
<Snort 규칙 구성 요소>

**Snort 규칙은 두 개의 논리적 섹션으로 나뉘는데 각각 규칙 헤더와 규칙 옵션임.** </br>
규칙 헤더에는 행위(Action), 프로토콜, 출발지 주소, 출발지 포트, 방향성, 목적지 주소, 목적지 포트가 포함됨. </br>
규칙 옵션에는 경고 메시지와 패킷의 어느 부분을 검사하여 규칙 행위을 수행해야 하는지 결정하는 정보가 들어 있음.

**규칙을 구성하는 모든 요소는 표시된 규칙 행위를 실행할 때 참(True)이어야 함.** </br>
**실행할 때 요소들은 논리적인 AND 문으로 형성하는 것으로 간주함.** </br>
**동시에 다양한 Snort 규칙 라이브러리 파일들은 논리적인 OR 문으로 구성하는 것으로 간주함.**
