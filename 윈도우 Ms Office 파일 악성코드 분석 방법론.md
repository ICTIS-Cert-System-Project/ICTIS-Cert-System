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


(![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/6e7568cd-f5af-44bf-a6ba-b7613bc57dc9)
)
