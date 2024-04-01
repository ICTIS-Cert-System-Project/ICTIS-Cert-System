# **Feedly 이용한 정보보안 동향 파악 방법론**
##### 작성자: 강하늘 사원
##### 작성일자: 2024년 3월 30일

<img src="https://cdn.icon-icons.com/icons2/2699/PNG/512/feedly_logo_icon_169177.png" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="Feedly"></img><br/>

## RSS(Really Simple Syndication)정의
- RSS는 뉴스나 블로그에서 주로 사용하는 콘텐츠 표현 방식으로서, 컨텐츠 업데이트가 자주 일어나는 웹사이트에서 직접 방문하지 않아도 업데이트된 정보를 쉽게 구독자들에게 제공하는 서비스임.

## 왜 Feedly로 동향 파악을 해야 하는가?
- 정보보안 동향 파악을 위해서는 여러 기관 사이트나 뉴스, 블로그를 통해 정보를 접하게 되는데 여러 웹 사이트를 직접 방문하기 보다 Feedly의 RSS 서비스를 이용하여 최신 정보보안 동향 정보를 한데 모아 빠르게 파악하여 전달하고 보고하기 용이함.
 
## 업무 효율을 높일 수 있는 사이트 정리
- 정보보안 동향 파악을 위해 참고하는 기관, 정보보안 기업 블로그, 기사 등으로 분류해 RSS 서비스를 제공하는 사이트를 바탕으로 정리함.

  
### [Alerts]
1. [CISA Alerts | 국외] <https://www.cisa.gov/news-events/cybersecurity-advisories>
2. [CISA - Known exploited vulnerabilities catalog | 국외] <https://www.cisa.gov/known-exploited-vulnerabilities-catalog>
   
### [Analysis]
1. [이스트시큐리티 알약 블로그 | 국내] <https://blog.alyac.co.kr>
2. [잉카인터넷 시큐리티 대응센터 블로그 | 국내] <https://isarc.tachyonlab.com>
3. [ASEC 블로그 | 국내] <https://asec.ahnlab.com> 
4. [Mandiant Blog | 국외] <https://www.mandiant.com/resources/blog>
5. [Imperva Blog | 국외] <https://www.imperva.com/blog>
6. [Cyble Blog | 국외] <https://cyble.com/blog>
7. [Research Check Point | 국외] <https://research.checkpoint.com>
8. [Cisco Talos Blog | 국외] <https://blog.talosintelligence.com>
9. [Cofense Blog | 국외] <https://cofense.com/blog>
10. [CrowdStrike Blog | 국외] <https://www.crowdstrike.com/blog>
11. [FortiGuard Labs - 위협 신호 보고서 | 국외] <https://fortiguard.fortinet.com/threat-signal-report>
12. [Huntress Blog | 국외] <https://www.huntress.com/blog>
13. [Kaspersky Blog | 국외] <https://www.kaspersky.com/blog>
14. [MarewareByte Blog | 국외] <https://www.kaspersky.com/blog>
15. [Morphisec Blog | 국외] <https://blog.morphisec.com>
16. [Reversing Labs Blog | 국외] <https://www.reversinglabs.com/blog>
17. [Sucuri Blog | 국외] <https://blog.sucuri.net>
18. [TAG Blog | 국외] <https://blog.google/threat-analysis-group>
19. [TrendMicro - Research, News, and Perspective | 국외] <https://www.trendmicro.com/en_us/research.html>

### [News]
1. [데일리시큐 | 국내] <https://www.dailysecu.com>
2. [보안뉴스 | 국내] <https://www.boannews.com>
3. [Packet Storm | 국외] <https://packetstormsecurity.com>
4. [The Hacker News | 국외] <https://thehackernews.com>
5. [Secwiki | 국외] <https://www.sec-wiki.com>
6. [SecurityWeek | 국외] <https://www.securityweek.com>
7. [Hackread | 국외] <https://www.hackread.com>
8. [GBHackers | 국외] <https://gbhackers.com>
9. [BleepingComputer | 국외] <https://www.bleepingcomputer.com>
    
## OPML의 정의
- OPML은 Outline Processor Markup Language(HTML 또는 XML과 같은 마크업 언어를 의미함)를 나타냄.
- OPML은 RSS 구독 목록을 백업하고 교환하기 위한 범용 표준임. 

## Feedly의 OPML Import와 Export 사용법

### Feedly의 OPML Import(OPML 파일을 Feedly로 가져오기)
- [Feedly](https://Feedly.com, "Feedly link")로 이동.
- Feedly 로그인.
- <https://feedly.com/i/cortex> 로 이동하여 OPML 파일 선택 버튼을 클릭하거나 OPML 파일을 표시된 공간으로 끌어다 놓음.
- 소스와 피드가 Feedly에 자동으로 추가됨.
  
### Feedly의 OPML Export (OPML 파일을 통해 피드 내보내기)

*Opml Export의 두가지 방법*

#### 첫번째 방법 
-  <http://feedly.com/i/opml> 링크로 이동하면 바로 *Export*가 가능함.
#### 두번째 방법
- [Feedly](https://Feedly.com, "Feedly link")로 이동.
- *Feedly* 로그인.
  
- 톱니바퀴 아이콘을 클릭하여 *Organize Sources* 페이지를 열어야 함.

<img src="https://images.ctfassets.net/lzny33ho1g45/1eMBV5VfVSaHTBRJH148sY/1648ee28dbb1bb28575ff35898bbaacc/Click_on_the_gear_icon_in_the_Feeds_section?w=1400&fm=avif" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="Feedly gear icon"></img><br/>

- 맨 오른쪽에서 곡선 화살표 버튼( OPML 가져오기 버튼 옆)을 클릭함.

<img src="https://images.ctfassets.net/lzny33ho1g45/1laXaqSJRgspmmKlNQkKge/3ee6afbbcd979e23644dd66838d12ae7/Click_on_arrow_button?w=1400&fm=avif" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="Feedly curved arrow icon"></img><br/>

- OPML 내보내기 페이지가 열림.

<img src="https://images.ctfassets.net/lzny33ho1g45/1JFR8F5fljjLxWCoOATqE6/0e290832e1c3eefb9aabd043cca6df29/Download_Feedly_OPML_button?w=1400&fm=avif" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="Feedly opml export page"></img><br/>

- 위 이미지에서 Feedly OPML 다운로드를 클릭하여 다운로드 프로세스를 시작함.

*파일이 다운로드되면 저장하고 이를 사용하여 다른 RSS 서비스로 가져올 수 있음.*
