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


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6e7568cd-f5af-44bf-a6ba-b7613bc57dc9)

[그림 1] OLE 파일 포맷 구조


![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2fd72ee0-5b26-4e65-87ea-d38ce9e27ed4)


[그림 2] OLE형식의 MS 워드 문서 구조

[표 1] OLE 형식의 MS 워드 문서 구조별 설명

|   |   |
|---|---|
|**필수 구성 요소**|**설명**|
|WordDocument|WordDocument 스트림의 내용은 .doc 파일을 Word 문서로 식별하는 코드를 포함하고 있으며 본문의 내용 포함|
|1Table/0Table|WordDocument 스트림이 .doc 파일을 Word 문서로 식별하는 과정에서 오프셋에 존재하는 FIB 내에 base.fWhichtblStm이 1로 설정되어 있으면 1Table을 참조하고 그렇지 않으면 0Table을 참조|
|Data|Data 스트림에는 사전에 정의된 구조가 따로 존재하지 않으며 다른 구조에서 해당 스트림에 대한 참조가 없다면 크게 사용되지 않는 부분|
|CompObj|MS 워드 파일의 버전 정보 포함 예) .doc 형식의 MS 워드 일 경우 ‘Microsoft Word 97-2003 MSWordDoc Word.Document’|

OpenXML 포맷의 MS 워드 문서는 문서별로 다양한 디렉터리 구조를 가질 수 있으며, 기본적으로 ZIP 압축 기술을 사용하여 문서를 작성하고 파일을 저장할 수 있음.
ZIP 형태로 압축해제 및 영역 분리된 OpenXML 형식의 MS 워드 구조 및 설명은 [그림 2]와 같음.

![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/164521627/2dafada9-31c4-4e38-b95f-ca7d56ce3700)


[그림 3] OpenXML형식의 MS 워드 문서 구조

[표 2] OpenXML 형식의 MS 워드 문서 구조별 설명

|   |   |
|---|---|
|**OpenXML** **파일 구성 요소**|**설명**|
|Content_Types.xml|OpenXML 포맷 파일에 필수적으로 포함되는 이 파일은 특정 파일 확장명에 대한 기본값 제공|
|/_rels|모든 패키지는 다른 파트들과 패키지 밖의 리소스들 사이의 관계를 정의|
|/doc/Props/core.xml|Office Open XML 문서의 메타데이터 등 핵심 속성이 포함|
|/word/documents.xml|본문을 구성하는 텍스트와 이를 오피스 문서 내에서 표현하기 위한 각 본문 속성에 맞는 XML, Object 참조에 대한 내용을 담음|
|/word/embeddings/oleObject.bin|다른 포맷의 파일을 삽입하여 참조하기 위해 포함되며, 다양한 형식의 raw binary 파일을 참조|
|/word/vbaProject.bin|vbaProject.bin은 내장된 프로그래밍 언어인 VBA로 작성된 스크립트로서 문서에 포함됨|

 MS 워드의 구조는 해커가 어떤 공격 기법을 사용하느냐에 따라 본문에 내용이 추가되거나, 새로운 구성 요소가 생성되는 등 구조가 변경되어 위협 인자가 포함되는 영역이 각각 다르게 생성됨. 
 이러한 특징 때문에 PE 구조의 exe 악성코드를 탐지할 수 있는 분석 방법과는 달리 버전별로 구분하여 영역을 분리하고 분리된 영역 내에서 위협 인자를 찾아낸 후 이를 추출하는 과정이 필요함.


#### OLE의 정의
각각의 응용프로그램들이 생산한 다양한 자료들을 독립적으로 사용하는 것이 아니라, 각각의 자료들을 서로 엮어놓는 것임.

예시로는, 한글 문서에 도표나 수식, 그림 등을 포함하고 필요에 따라 음향 자료를 함께 문서에 포함하는 것이다. 반대로 음악 전용 프로그램에서 음악 자료에 필요한 설명문을 문서 편집 전용 프로그램을 이용해 만든 다음, 그 자료를 그대로 음악 자료에 포함할 수 있음.

이렇게 각각의 독립적 자료들을 하나의 응용프로그램에서 다양하게 사용할 수 있는 기능을 개체 연결과 포함, 즉 OLE 기능이라고 함.
