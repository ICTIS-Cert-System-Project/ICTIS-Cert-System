# Web Crawler


| 작성자       | 김평일 대리   |
| --------- | ---------------- |
| **작성 일자** | **2024년 4월 18일** |
| **수정 일자** |                  |
| **비고**    |                  |

<br>
<br>

## (1) 웹 크롤러 란?

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/9516a536-1962-4419-92a1-ffd8081ae544)</div>

크롤러란 <ins>**방대한 웹 페이지를 두루두루 방문하여 각종 정보를 자동적으로 수집하는 일을 하는 프로그램으로서 검색 엔진의 근간**</ins>임.</br>

웹 크롤러에 대한 다른 용어로는 앤트(Ants), 자동인덱서(Automatic Indexers), 봇(Bots), 웜(Worms), 웹 스파이더(Web Spider), 웹 로봇(Web Robot) 등이 있음.</br>
웹 크롤러가 하는 작업을 웹 크롤링(web crawling) 혹은 스파이더링(spidering)이라고 부름.</br>

<br>
<br>

## (2) 웹 크롤러 기능

검색 엔진과 같은 여러 사이트에서는 데이터의 최신 상태 유지를 위해 항상 웹 크롤링을 하며 대체로 방문한 사이트의 모든 페이지의 복사본을 생성하는 데 사용됨.<br>
또한 링크 체크나 HTML 코드 검증과 같은 웹 사이트의 자동 유지 관리 작업을 위해 사용되기도 하며 자동 이메일 수집과 같은 웹 페이지의 특정 형태의 정보를 수집하는데도 사용됨.<br>
웹 크롤러는 봇이나 소프트웨어 에이전트의 한 형태로 대개 시드(Seed)라고 불리는 URL 리스트에서부터 시작하며 페이지의 모든 하이퍼링크를 인식 및 URL 리스트를 갱신하여 확인함.<br>

<br>
<br>

## (3) 웹 크롤러 단점

웹 크롤러는 설계(프로그래밍)를 잘못하면 네트워크에 트래픽을 증가시키고 서버에 과부하를 줄 수 있음.<br>
블로그나 카페 등에 게시한 개인정보까지 수집함.<br>
게시한 글을 지우더라도 웹 크롤러가 수집하여 검색엔진 데이터베이스에 저장한 정보는 지워지지 않으며 나중에 다른 사용자가 검색할 수도 있음. (구글이나 네이버 등 검색 시 저장된 페이지 볼 수 있음)<br>

<br>
<br>

## (4) Google Crawler 리스트

대표적인 웹 크롤러 중에 구글 크롤러를 확인함.<br>
아래 표는 2020년 07월 24일 자 기준 구글에서 제공된 정보를 바탕으로 기재함.<br>

##### 링크: [GOOGLE][googlelink]
[googlelink]: https://support.google.com/webmasters/answer/1061943?hl=ko&ref_topic=9426101 "Gogoogle"

<br>

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/18510716/7ca30c90-0e7a-46c2-b447-4a2f1b380f58)</div><br>

**※ 위 표에서 사용자 에이전트의 ‡ Chrome/W.X.Y.Z**<br>

표에 있는 사용자 에이전트 문자열에 Chrome/W.X.Y.Z 문자열이 표시되는 경우 W.X.Y.Z는 사용자 에이전트가 사용하는 Chrome 브라우저의 버전을 나타냄(예: 41.0.2272.96). 이 버전 번호는 Googlebot이 사용하는 최신 Chromium 출시 버전과 일치하도록 시간이 지남에 따라 커짐.<br>
이 패턴이 있는 사용자 에이전트를 위해 로그를 검색하거나 서버를 필터링하는 경우 정확한 버전 번호를 지정하기보다는 버전 번호에 와일드 카드를 사용하는 것이 좋음.<br>

<br>
<br>

## (5) robots.txt 를 이용하여 웹 크롤러 차단 방법

User-Agent 명을 기재해서 사용하며 특정 폴더 및 전체 폴더에 대해서 차단 및 허용함.<br>

**Google 웹 검색에 대해 허용할 경우**<br>
`User-agent: Googlebot`<br>
`Disallow:`<br>

**Google 웹 검색에 대해 전체 폴더 차단할 경우**<br>
`User-agent: Googlebot`<br>
`Disallow: /`<br>

**Google 웹 검색에 대해 /board 폴더만 차단할 경우**<br>
`User-agent: Googlebot`<br>
`Disallow: /board`<br>

**모든 웹 크롤러를 허용할 경우**<br>
`User-agent: * `<br>
`Disallow: `<br>

**모든 웹 크롤러에 대해 특정 폴더만 차단할 경우**<br>
`User-agent: *` <br>
`Disallow: /koromoon_photo/` <br>
`Disallow: /koromoon_diary/`<br>

**특정 웹 크롤러만 차단할 경우 (ex. koromoonbot)**<br>
`User-agent: koromoonbot`<br>
`Disallow:` /<br>

**특정 웹 크롤러만 허용할 경우 (ex. koromoonbot)**<br>
`User-agent: koromoonbot`<br>
`Disallow:`<br>
`User-agent: *`<br>
`Disallow: /`<br>

<br>
<br>

## (6) Meta Tag 를 이용하여 웹 크롤러 차단 방법

특정 페이지에 대해서만 차단할 경우 Meta Tag 를 이용하여 차단함.<br>

해당 페이지에 대해 Google 웹 검색을 차단할 경우<br>

`<meta name="robots" content="nofollow"><meta name="googlebot" content="noindex">`<br>

<br>

##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2020/07/web-crawler.html "Go koromoon"
