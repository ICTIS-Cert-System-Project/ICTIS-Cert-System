# 윈도우 문서형 악성코드 분석 방법론
##### 작성자 : 김평일 대리, 정한울 대리, 김태현 사원, 강하늘 사원
##### 작성일자 : 2024년 6월 1일
</br></br>

##  doc 파일 개요

### 1. MS Word

MS Word는 Doc와 DOCX 두가지 확장자가 사용되고 있음.</br>
Word97-2003 에서 사용된 .doc와 Word 2007 시작 이후 사용된 .docx이며 Word 문서를 저장하기위한 기본 파일 형식임.</br>
</br>
DOC와 DOCX 파일 유형의 주요 차이점은 이러한 문서를 저장하는 데 사용되는 기본 파일 형식임. DOC 파일은 정보를 이진 파일로 저장하는 BIFF (Binary Interchange Files Format)를 기반으로하며, 데이터는 MS-DOC 파일 형식 사양에 설명 된 바와 같이 이진 스트림으로 배열 된 레코드 및 구조 모음으로 DOC 파일로 구성됨.</br>
대조적으로, DOCX 파일은 압축 된 XML 파일의 zip 형식으로 데이터를 저장하는 Office Open XML 형식을 사용함.</br>
</br>

### 2. .doc 구조

**DOC 파일은 OLE(Object Linking and Embedding) 파일 포멧을 사용함.**</br>
</br>
OLE 파일 포멧은 파일 시스템 중 MS의 FAT파일 시스템과 유사한 구조를 지니며, 내부에서 파일과 폴더의 개념 OLE 파일 포멧에서는 이를 각각 Storage, Stream 이라 부르는 복합 문서 파일 형태의 구조를 띄고 있음.</br>

#### OLE의 정의
각각의 응용프로그램들이 생산한 다양한 자료들을 독립적으로 사용하는 것이 아니라, 각각의 자료들을 서로 엮어놓는 것임.

예시로는, 한글 문서에 도표나 수식, 그림 등을 포함하고 필요에 따라 음향 자료를 함께 문서에 포함하는 것임. </br>
반대로 음악 전용 프로그램에서 음악 자료에 필요한 설명문을 문서 편집 전용 프로그램을 이용해 만든 다음, 그 자료를 그대로 음악 자료에 포함할 수 있음.

이렇게 각각의 독립적 자료들을 하나의 응용프로그램에서 다양하게 사용할 수 있는 기능을 개체 연결과 포함, 즉 OLE 기능이라고 함.




![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6e7568cd-f5af-44bf-a6ba-b7613bc57dc9)

[그림 1] OLE 파일 포맷 구조


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2fd72ee0-5b26-4e65-87ea-d38ce9e27ed4)


[그림 2] OLE형식의 MS 워드 문서 구조




|**필수 구성 요소**|**설명**|
|---|---|
|WordDocument|WordDocument 스트림의 내용은 .doc 파일을 Word 문서로 식별하는 코드를 포함하고 있으며 본문의 내용 포함|
|1Table/0Table|WordDocument 스트림이 .doc 파일을 Word 문서로 식별하는 과정에서 오프셋에 존재하는 FIB 내에 base.fWhichtblStm이 1로 설정되어 있으면 1Table을 참조하고 그렇지 않으면 0Table을 참조|
|Data|Data 스트림에는 사전에 정의된 구조가 따로 존재하지 않으며 다른 구조에서 해당 스트림에 대한 참조가 없다면 크게 사용되지 않는 부분|
|CompObj|MS 워드 파일의 버전 정보 포함 예) .doc 형식의 MS 워드 일 경우 ‘Microsoft Word 97-2003 MSWordDoc Word.Document’|

[표 1] OLE 형식의 MS 워드 문서 구조별 설명


### 3. .docx 구조


OpenXML 포맷의 MS 워드 문서는 문서별로 다양한 디렉터리 구조를 가질 수 있으며, 기본적으로 ZIP 압축 기술을 사용하여 문서를 작성하고 파일을 저장할 수 있음.
ZIP 형태로 압축해제 및 영역 분리된 OpenXML 형식의 MS 워드 구조 및 설명은 [그림 3]와 같음.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2dafada9-31c4-4e38-b95f-ca7d56ce3700)


[그림 3] OpenXML형식의 MS 워드 문서 구조




|**OpenXML** **파일 구성 요소**|**설명**|
|---|---|
|Content_Types.xml|OpenXML 포맷 파일에 필수적으로 포함되는 이 파일은 특정 파일 확장명에 대한 기본값 제공|
|/_rels|모든 패키지는 다른 파트들과 패키지 밖의 리소스들 사이의 관계를 정의|
|/doc/Props/core.xml|Office Open XML 문서의 메타데이터 등 핵심 속성이 포함|
|/word/documents.xml|본문을 구성하는 텍스트와 이를 오피스 문서 내에서 표현하기 위한 각 본문 속성에 맞는 XML, Object 참조에 대한 내용을 담음|
|/word/embeddings/oleObject.bin|다른 포맷의 파일을 삽입하여 참조하기 위해 포함되며, 다양한 형식의 raw binary 파일을 참조|
|/word/vbaProject.bin|vbaProject.bin은 내장된 프로그래밍 언어인 VBA로 작성된 스크립트로서 문서에 포함됨|

[표 2] OpenXML 형식의 MS 워드 문서 구조별 설명


 MS 워드의 구조는 해커가 어떤 공격 기법을 사용하느냐에 따라 본문에 내용이 추가되거나, 새로운 구성 요소가 생성되는 등 구조가 변경되어 위협 인자가 포함되는 영역이 각각 다르게 생성됨. 
 이러한 특징 때문에 PE 구조의 exe 악성코드를 탐지할 수 있는 분석 방법과는 달리 버전별로 구분하여 영역을 분리하고 분리된 영역 내에서 위협 인자를 찾아낸 후 이를 추출하는 과정이 필요함.


| **분류**           | **현황** |
| ---------------- | ------ |
| Macro            | 246    |
| Oleobject        | 171    |
| DDE              | 18     |
| Stream & Storage | 14     |
| ETC              | 4      |

[표 3] 수집된 MS 워드 문서형 악성코드 현황



----------


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/98f6e151-85fa-40c6-aa23-065e9f2be8f8)


[그림 4] MS-Word 구조 내 스트림 구조

(OLE 형식)
MS-Word 문서형 악성코드를 분석 및 탐지하기 위해서 첫째, **구조 내에서 스트림을 추출한 후 위협 인자가 포함된 영역이 구조 내에 존재하는지 확인**.

둘째, **위협 인자가 포함된 스트림에서 텍스트 형식으로 데이터를 추출**한 후 셋째, **Yara-Rule를 활용하여 탐지**를 진행. 

MS-Word 문서형 악성코드로 활용되는 기법 중 가장 빈번히 사용되는 공격을 대상으로 위협 인자 추출 방안 및 탐지 방법에 관련하여 설명하겠음.

## **_1) VBA_** **_매크로 형태의 악성코드 분석 및 탐지 방법_**

MS-Word 내에 VBA 매크로가 포함될 경우 [그림 5]와 같이 _VBA 스토리지 하위에 _VBA_PROJECT 등 이와 관련된 스트림이 추가적으로 생성됨. 하지만 _VBA 스토리지가 존재한다고 해서 MS-Word 문서 파일이 악성코드라고 판단할 수 없기 때문에 바이너리 파일 내에서 스크립트를 텍스트 형식으로 재추출하고, 코드 분석을 통해 악의적인 행위를 위해 작성된 스크립트인지 확인하는 심층 검증 작업을 거쳐야 함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/f2aa6ac7-475c-4b9e-bf68-a8c5018549d6)


[그림 5] 매크로가 포함된 MS-Word 문서 파일 스트림 구조

 MS-Word 문서 구조 내에 매크로 바이너리 파일이 존재할 경우 파일이 포함된 경로명까지 모두 텍스트 형식으로 추출함. 추출된 텍스트 파일 내에 Macros, VBA와 같은 키워드가 존재할 경우 MS-Word 문서 파일 내에 VBA 매크로 스크립트가 존재한다고 가정하고 추출하게 됨. 

 추출된 스크립트 중 난독화 되어있는 구문을 데이터 전처리 과정을 통해 코드 분석이 가능한 수준의 평문으로 변환하여 추출함. 데이터 전처리 과정을 거치는 이유는 매크로 스크립트 내에서 정상적인 행위의 매크로와 악성 행위를 수행하는 매크로를 구분하기 위함임.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/5814ac49-abd2-4298-ae1d-6f03e3c785ff)


[그림 6] 추출된 MS-Word 내 매크로 스크립트

MS-Word 내에서 추출된 매크로 스크립트의 예시는 그림 3과 같으며, 추출된 텍스트 형식의 매크로 스크립트의 악성 여부를 판단하기 위해서는 스크립트 내에서 사용된 메소드를 주목하여야 함.

일반적으로 정상 MS-Word 문서 내에 포함된 매크로 스크립트는 MS의 의도에 맞게 특정 문구나 행위에 대한 반복적인 기능을 빠르고 효율적으로 사용할 수 있도록 하는 메소드(기능)를 사용하지만, 매크로를 활용한 문서형 악성코드의 경우에는 악성 행위를 수행하는 일반적으로 사용하지 않는 특정 메소드를 사용하게 됨.

---

### – oletools 라이브러리 내 mraptor 도구의 알고리즘 –

매크로 스크립트의 악성 여부를 판단하는 탐지 알고리즘은 oletools 라이브러리 내 mraptor 도구의 알고리즘을 참고했으며, mraptor는 일반 휴리스틱 기반의 탐지 기법을 사용하여 악성 VBA 매크로 스크립트를 탐지하도록 설계된 도구임. 

간단히 설명하자면 mraptor는 일반 텍스트로 존재하는 스크립트가 존재할 경우 3가지 유형의 해당하는 키워드를 감지하게 됨.

A : 자동 실행 트리거

W : 파일 시스템 또는 메모리에 쓰기

X : VBA 스크립트 외부에서 파일 실행 및 다운로드 또는 페이로드 실행

Mraptor는 A(자동실행트리거)가 기본적으로 포함되어있고 W또는 X가 존재할 때 해당 매크로가 악성 행위를 수행하는 것이라고 판단하게 됨.

(예) Document_Open과 같은 자동 실행 트리거(A)가 존재하고 URLDownloadToFileA와 같은 드롭퍼 형식의 파일 다운로드(X) 행위가 동시에 존재한다면 이를 악성으로 판단함. (판단 기준 : A-X, AW-, AWX)

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/d1630664-0c5b-4d6c-b102-e818f7a08f1c)


---

Mraptor의 탐지 알고리즘을 기반으로 Yara-Rule을 생성할 때 String 형식의 **자동실행트리거 메소드(AutoOpen, Document_Open, DocumentOpen)**가 존재하며, **파일 시스템 또는 메모리의 데이터를 수정할 수 있는 메소드(Write, Put, Output, Print 등)**나 **외부에서 파일 실행 및 다운로드 또는 페이로드 실행 메소드(Powershell, URLDownloadToFileA, Shell, Wscript.shell, run 등)**가 포함되어있다면 악성 행위를 수행하는 MS-Word 문서를 악성으로 판단하여 탐지함.

## **_2)_** **_삽입된 외부_** **_oleobject_** **_형태의 악성코드 분석 및 탐지 방법_**

MS-OFFICE는 문서 내부에 다른 문서 파일이나 PDF, 이미지 파일, 실행 파일 등 32가지의 파일을 삽입할 수 있으며, 삽입된 파일을 객체라고 칭하며 이를 외부 oleobject 객체 삽입이라고 부름름. 공격자는 MS-Word 문서 내에서 다른 OLE 객체를 참조할 때 문서 내에서 파일이 실행되는 것을 악용하여 악성코드 실행 및 URL 리다이렉트와 같은 비정상 행위를 수행할 수 있음.

외부 oleobject 객체가 문서 내에 삽입될 경우 [그림 7]와 같이 ObjectPool 스토리지 내 ‘_Ole*’ 형태나 ‘_CompObj’ 형식으로 저장됨. 
 매크로와 마찬가지로 외부 oleobject 객체가 삽입된 MS-Word 파일 내에서 스토리지와 스트림 경로를 모두 텍스트 형식으로 파싱했을 때 ObjectPool 또는 ‘CompObj’, ‘Ole10Native’, ‘ObjInfo’ 등의 키워드가 포함되어 있다면 삽입되어 있는 oleobject의 악성 여부를 검증하게 됨.
 
![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/7edc66ae-c860-47ba-b60f-e69392986714)


[그림 7] MS-Word 구조 내 oleobject가 포함된 스트림 구조

[그림 8]은 악성 행위를 수행하는 Javascript가 oleobject 형태로 삽입되어 있는 모습임.
Javascript 내에서 악성 행위를 실행하기 위해서는 ‘eval’ 함수가 반드시 실행되어야 하므로, 이러한 키워드를 활용하여 Yara-Rule을 생성해서 탐지를 진행함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/c69cdcff-bd46-4f10-8506-2e7291e5a081)


[그림 8] 악성 oleobject MS-Word 구조 내 스트림 구조 및 eval function

[그림 9]은 사용자를 특정 사이트로 접속시키기 위해 공격자가 IP 또는 URL 형태로 삽입한 oleobject 입니다. IP 또는 URL 형태의 악성 oleobject는 Yara-Rule 정규표현식을 활용하여 탐지를 진행함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/d6ba3eb2-15ae-4649-91f6-e4c5ba81cd87)


[그림 9] 공격자 IP 및 URL

[그림 10]은 문서 내에 PE 형태의 실행 파일을 oleobject 형식으로 삽입하여 클릭을 유도하여 악성코드를 실행시키는 oleobject 형태임. 앞서 설명되었던 Javascript나 IP, URL의 형태가 아닌 파일이 삽입되어있는 경우에는 oletool 라이브러리 내 포함되어있는 oleobj라는 도구를 활용하여 분석 및 유효 악성 인자를 식별(추출)하여 탐지함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/22cfa885-b623-4537-9ca8-193d40d9acf4)


[그림 10] PE 바이너리 삽입

## **_3) DDE(Dynamic Data Exchange)_** **_형태의 악성코드 분석 및 탐지 방법_**

### DDE의 정의

DDE란 ‘Dynamic Data Exchange’의 약어로 윈도우 응용 프로그램 간의 동일한 데이터를 공유하도록 허용하는 방법 중 하나임. 
MS-OFFICE 문서, Visual Basic 등 다양한 응용 프로그램에서 사용되고 있으며, 해당 기능을 활용하여 다른 파일을 실행시킬 수 있어 이 기능을 악용하여 악성코드를 다운받거나 실행시키는 행위가 가능함.

다음의 코드는 MS-Word 본문 내에서 CMD 명령 프롬프트를 이용해 계산기를 실행시키는 스크립트임. 예시는 매우 간단한 코드이지만 DDE 필드 코드를 계산기 실행이 아닌 Powershell을 이용할 경우 DDE는 매우 강력한 악성 인자가 됨.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/c63603b9-ba2c-4821-81c8-a605fc99926c)


앞서 매크로와 외부 oleobject 객체가 삽입된 MS-Word 문서형 악성코드를 탐지하기 위해 기본적으로 문서 내의 포맷을 분석해 스트림 목록을 출력하였음. [그림 11]와 같이 MS-Word는 공통적으로 WordDocument 라는 스트림이 존재하며 해당 스트림은 MS-Word의 본문 내용을 포함하고 있음.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/d99be29a-dc56-49c3-a582-5db9c1491f4e)


[그림 11] MS-Word 구조 내 스트림 구조

본문의 내용을 포함하고 있는 ‘WordDocument’라는 스트림을 텍스트 형식으로 파싱하여 Yara-Rule을 통해 String 형식으로 DDE와 같은 키워드로 탐지할 수도 있겠지만, 본문 내에 포함된 내용인 만큼 DDE 필드가 아니더라도 ‘DDE’라는 키워드가 본문 내에 포함될 여지가 있기 때문에 DDE 스크립트를 직접 추출하여 분석 및 탐지하였음.

[그림 12]은 oletool 라이브러리 내에 존재하는 msodde라는 도구를 활용하여 MS-Word 내에 포함된 DDE 스크립트를 추출한 결과 화면임.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/94f32de4-2fe0-4058-bdc1-1b7c7f1fc5b2)


[그림 12] DDE 스크립트

다만 실제로 DDE를 악용한 MS-Word 문서형 악성코드가 배포될 때는 백신에서 미리 탐지하지 못하도록 스크립트를 난독화하는 경우가 대부분인데, 이는 전처리 과정을 msodde 도구를 활용하여 해결이 가능함함. msodde를 활용해 텍스트 형식으로 DDE 스크립트가 출력되는 것을 Yara-Rule을 통해 String 형식으로 “DDEAUTO”와 같은 키워드를 시그니처로하여 탐지할 수 있음.

## **_4) MS-Word 기본 구조 내 위협 인자가 포함된 악성코드 분석 및 탐지 방법_**

MS-Word 문서는 공격자가 악용할 수 있는 다양한 기능을 제공하기도 하지만 동시에 문서 포맷의 유연성으로 인해 구조 내 위협 인자를 은닉할 수 있는 공간을 제공하여 공격에 자주 사용되는데, 기본 스트림 영역을 확인해보았을 때 ‘CompObj’, ‘DocumentSummaryInformation’, ‘SummaryInformation’, ‘WordDocument’와 같이 공통적인 요소가 있으며, 공격자는 이러한 공통 요소를 활용하여 악성인자를 은닉하기도 함.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/936e08a7-cd2b-4a53-be60-5c68b4042da4)


[그림 13] 공통 요소 활용

[그림 13]는 공통적인 요소 중 ‘DocumentSummaryInformation’ 스트림 내에 실행 파일이 포함되어있는 모습임. 해당 영역에서 발견된 실행 파일을 추출하여 Virustotal에 검사한 결과 워너크라이 랜섬웨어인 것을 확인할 수 있었고 MS-Word 문서를 구성하는 기본 요소라 할지라도 악성 여부에 대한 검증이 필요함.

