# CyberChef *(암호화, 인코딩, 압축 및 데이터 분석을 위한 웹 앱)*
#####  원작자: 문광일 PM
#####  링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2021/01/cyberchef.html "Go koromoon"
#####  작성자: 강하늘 사원
#####  작성일자: 2024년 4월 10일

</br>

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/b67b3250-8336-419a-b242-3cdc9149f49a)

## (1) 설명
영국 정보기관인 GCHQ 에서 만든 암호화, 인코딩, 압축 및 데이터 분석을 위한 웹 응용 프로그램임.
해당 프로그램 기능은 XOR 또는 Base64 와 같은 간단한 인코딩, AES, DES 및 Blowfish 와 같은 보다 복잡한 암호화, 바이너리 및 16 진수 덤프 생성, 데이터 압축 및 압축 해제, 해시 및 체크섬 계산, IPv6 및 X.509 구문 분석, 문자 인코딩 변경 등이 포함됨.
또한, 복잡한 도구나 알고리즘을 다루지 않고도 간단한 드래그 앤 드롭 방식으로 복잡한 데이터를 쉽게 분석할 수 있어 비전문가나 전문가도 모두 유용하게 사용할 수 있음.
HTML 페이지로 제공되며 온라인으로 액세스하거나 로컬 시스템에 복사본을 다운로드하여 인터넷 연결 없이도 사용 가능함.
현재 최신 버전은 9.21.0 버전으로 Google Chrome 50 이상, Mozilla Firefox 38 이상에서 사용이 가능함.



홈페이지 : <https://github.com/gchq/CyberChef>

</br>

*특히, CTF나 워게임을 하는 사람이라면 해당 툴은 필수로 가지고 다님.* </br>
*보안 업무에도 유용하게 사용이 가능하며 특히 인터넷 없이도 로컬 PC에서 사용이 가능하다는 장점이 있음.*

## (2) 화면 설명
화면은 크게 Operations, Recipe, Input, Output 영역으로 나뉘며 각 항목의 역할은 아래와 같음.

<div align="center">

<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><b><span style="font-family: courier;">영역 구분<span lang="EN-US"><o:p></o:p></span></span></b></p>
  </td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><b><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></b></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Operations</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;">작업 메뉴 목록</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Recipe</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;">작업 지정</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Input</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;">데이터 입력</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Output</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 230.6pt;" width="307">
  <p class="MsoNoSpacing"><span style="font-family: courier;">결과값 출력</span></p>
  </td>
 </tr>
</tbody></table>

</div>

- 사용법은 오른쪽 상단 Input 입력란에 변환할 데이터를 입력한 후 왼쪽 Operations 메뉴에서 작업하고자 하는 메뉴를 중앙 Recipe 영역으로 드래그 앤 드롭하면 됨.
- 그리고 중앙 하단의 BAKE 버튼을 누르면 오른쪽 하단 Output 창에 결과값이 출력됨.

## (3) 작업 메뉴 설명
- 왼쪽 Operations 에 대한 작업 메뉴들을 설명함.
<table border="1" cellpadding="0" cellspacing="0" class="MsoTableGrid" style="border-collapse: collapse; border: none; mso-border-alt: solid windowtext .5pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 1184;">
 <tbody><tr>
  <td style="background: #DBE5F1; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><b><span style="font-family: courier;">작업 메뉴 구분<span lang="EN-US"><o:p></o:p></span></span></b></p>
  </td>
  <td style="background: #DBE5F1; border-left: none; border: solid windowtext 1.0pt; mso-background-themecolor: accent1; mso-background-themetint: 51; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p align="center" class="MsoNoSpacing" style="text-align: center;"><b><span style="font-family: courier;">설명<span lang="EN-US"><o:p></o:p></span></span></b></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Favourites</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">즐겨 찾기</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Data format</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">Hex, Base64, URL Encode </span>등 다양한 데이터
  형식을 변환</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Encryption / Encoding</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">AES, DES, XOR </span>등 다양한 알고리즘을 사용하여 데이터
  암호화 및 복호화</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Public Key</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">공개키 조작</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Arithmetic / Logic</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">논리 연산</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Networking</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">네트워크 작업</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">(</span>예<span lang="EN-US"> : HTTP </span>헤더
  제거<span lang="EN-US">, IP </span>범위 구문 분석<span lang="EN-US">, URI </span>구문 구분 등<span lang="EN-US">)</span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Language</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">서로 다른 문자 인코딩 간의 데이터 변환</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Utils</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">텍스트에 대한 다양한 작업 수행</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">(</span>예<span lang="EN-US"> : </span>공백
  작업<span lang="EN-US">, </span>줄 번호 추가<span lang="EN-US">, </span>대소문자 변경 등<span lang="EN-US">)</span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Data / Time</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">시간 형식 변경</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Extractors</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">문자열<span lang="EN-US">, IP </span>주소<span lang="EN-US">, </span>이메일
  주소 등 특정 데이터 추출</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Compression</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">다양한 압축 형식을 사용하여 데이터 압축 및 해제</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Hashing</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">해시를 분석하고 생성</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Code tidy</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">언어 코드 조작</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">(</span>예<span lang="EN-US"> : </span>축소<span lang="EN-US">, </span>파서<span lang="EN-US">, </span>가독성 높게 인쇄<span lang="EN-US">, </span>직렬화<span lang="EN-US">, </span>역직렬화 등<span lang="EN-US">)</span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Forensics</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">파일 유형 감지 및 검색</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Multimedia</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">멀티미디어 작업</span></p>
  <p class="MsoNoSpacing"><span style="font-family: courier;"><span lang="EN-US">(</span>예<span lang="EN-US"> : </span>이미지
  렌더링<span lang="EN-US">, </span>미디어 재생<span lang="EN-US">, </span>이미지 생성 등<span lang="EN-US">)</span></span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Other</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">그 외 기타</span></p>
  </td>
 </tr>
 <tr>
  <td style="border-top: none; border: solid windowtext 1.0pt; mso-border-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 125.9pt;" width="168">
  <p class="MsoNoSpacing"><span lang="EN-US"><span style="font-family: courier;">Flow control</span></span></p>
  </td>
  <td style="border-bottom: solid windowtext 1.0pt; border-left: none; border-right: solid windowtext 1.0pt; border-top: none; mso-border-alt: solid windowtext .5pt; mso-border-left-alt: solid windowtext .5pt; mso-border-top-alt: solid windowtext .5pt; padding: 0cm 5.4pt 0cm 5.4pt; width: 335.3pt;" width="447">
  <p class="MsoNoSpacing"><span style="font-family: courier;">복합된 작업 메뉴 조작</span></p>
  </td>
 </tr>
</tbody></table>

## (4) 지원 기능

01. 드래그 앤 드롭

작업은 Recipe 영역(작업 지정)으로 드래그하거나 재구성할 수 있음.
최대 2GB 의 파일을 Input 영역(데이터 입력)에 드래그하여 브라우저에 직접 로드할 수 있음.



02. 자동 베이킹

입력 또는 레시피를 수정할 때마다 CyberChef 가 자동으로 "Bake!" 하여 출력을 즉시 생성함.
성능에 영향을 미치는 경우(예 : 입력이 매우 큰 경우) 수동으로 끄고 조작할 수 있음.
여기서 베이킹이란? 데이터 변환을 위해 Bake! 버튼을 클릭하여 작업을 수행하는 행위를 말함.



03. 자동화된 인코딩 감지 (강추!!!)

CyberChef 는 여러 기술을 사용하여 데이터가 어떤 인코딩으로 되어 있는지 감지할려고 시도함.
데이터를 이해할 수 있는 적절한 작업을 찾고싶다면 "Magic" 메뉴을 이용하여 자동으로 Output 영역에 표시됨.



04. 중단점

레시피의 모든 작업에 중단점을 설정하여 실행하기 전에 실행을 일시 중지할 수 있음.
레시피를 한 번에 하나씩 작업을 통해 각 단계에서 데이터가 어떻게 보이는지 확인할 수도 있음.



05. 레시피 저장 및 로드

다시 사용하고 싶은 멋진 레시피가 나오면 "Save recipe"(레시피 저장)을 클릭하고 로컬 저장소에 추가함.
레시피와 입력이 포함된 URL 을 복사하여 다른 사람들과 쉽게 공유할 수 있음.



06. 검색

원하는 작업의 이름이나 관련 단어를 알고있는 경우 Operations 영역의 검색 필드에 입력하기 시작하면 일치하는 작업이 즉시 표시됨.



07. 파일에 저장하고 파일에서 로드

언제든지 출력을 파일에 저장하거나 파일을 입력 필드로 로드할 수 있음.
최대 약 2GB 파일이 지원되지만(브라우저에 따라 다름) 일부 작업은 이렇게 많은 데이터를 실행하는 데 시간이 오래 걸릴 수 있음.



08. CyberChef 는 전적으로 클라이언트 실행 파일임.

레시피 구성이나 입력(텍스트 또는 파일)은 CyberChef 웹 서버로 전송되지 않음.
모든 처리는 사용자 컴퓨터의 브라우저 내에서 수행됨.
이 기능으로 인해 CyberChef 를 다운로드하여 로컬에서 실행할 수 있음.
인터넷 앱( https://gchq.github.io/CyberChef/ )의 왼쪽 상단 모서리에 있는 링크를 사용하여 CyberChef 전체 사본을 다운로드하여 가상 머신에 놓거나 다른 사람과 공유하거나 폐쇄된 네트워크에서 호스팅할 수 있음.

## (5) 사용예
01. Base64 로 인코딩된 문자열 디코딩

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/f5382650-d07c-4548-9df7-34904d388c19)

02. 날짜와 시간을 다른 시간대로 변환

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/9c386369-6b33-40ea-85d0-5a3fe2ad326d)

03. Teredo IPv6 주소 구문 분석

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/1f1e3c7e-e9cd-425a-9362-2c694e53d764)

04. 16 진수 덤프에서 데이터를 변환한 다음 압축해제

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/438af126-456b-471d-a97c-698d69cae995)

05. 쉘코드 복호화와 디스어셈블리

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/4d080385-d3cb-4efc-94ca-a23aeb873a95)

06. 여러 타임 스탬프를 전체 날짜로 표시

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/20a532a6-73d7-4352-99ba-2fc9eff3c845)

07. 서로 다른 유형의 데이터에 대해 서로 다른 작업 수행

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2c33a04a-03fa-444c-8447-e3988ea11ba5)

08. 입력의 일부를 연산에 대한 인수로 사용

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/45845b95-e8a7-46ce-8610-722cd6ed765b)

09. AES 암호 해독을 수행하여 암호 스트림의 시작 부분에서 IV 추출

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/5f2a6dd4-730a-4500-b9c8-a0cab83c3b74)

10. 여러 계층의 중첩 인코딩을 자동으로 감지

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2aa8bf55-7745-4c8d-9f9e-ebb65cd2a834)
