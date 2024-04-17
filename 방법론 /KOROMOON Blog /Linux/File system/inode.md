# inode
##### 원작자: 문광일 PM
##### 링크: [KOROMOON][koromoonlink]
[koromoonlink]: https://koromoon.blogspot.com/2018/05/inode-symbolic-link-hard-link.html "Go koromoon"
##### 작성자: 김평일 대리
##### 작성일자: 2024년 4월 17일

##  아이노드(inode)

</br><div align="center">![image](https://github.com/ICTIS-Cert-System-Project/ICTIS-Cert-System/assets/165347210/69ba9e79-0c2a-40c3-b4aa-4074599b3c65)</div>
<div align="center">< 출처 - commons.wikimedia.org ></div></br>
</br>
</br>
</br>
심볼릭 링크와 하드 링크를 이해하기 위해서는 우선 inode에 대한 이해가 필요함.</br>
아이노드(inode)는 UFS 와 같은 전통적인 유닉스 계통 파일 시스템에서 사용하는 자료 구조로 정규 파일, 디렉터리 등 파일 시스템에 관한 정보를 보유하고 있음.</br>
</br>
파일들은 각자가 1개의 아이노드를 가지고 있으며, 아이노드는 소유자 그룹, 접근 모드(읽기, 쓰기, 실행 권한), 파일 형태, 아이노드 숫자(inode number, i-number, 아이넘버) 등 해당 파일에 관한 정보를 가지고 있음.</br>
또한 파일 시스템 내에서 파일이나 디렉토리는 고유한 inode 를 가지고 있으며 inode 번호를 통해 구분이 가능함.</br>
</br>
사용자가 파일 또는 파일과 관련된 정보에 액세스하려고 하면 파일 이름을 사용하지만 내부적으로 파일 이름은 먼저 디렉토리 테이블에 저장된 inode 번호로 매핑된 후 inode 번호를 통해 해당 inode 에 액세스 됨.</br>
</br>
</br>
inode 에 포함된 정보는 아래와 같음.
  
- **파일 모드(퍼미션)**</br>
- **링크 수**</br>
- **소유자명**</br>
- **그룹명**</br>
- **파일 크기**</br>
- **파일 주소**</br>
- **마지막 접근 정보**</br>
- **마지막 수정 정보**</br>
- **아이노드 수정 정보**</br>
</br>
inode 포인터 구조를 통해 파일의 실제 데이터가 저장된 블록의 정보를 포함하여 파일의 메타 데이터 정보만 저장시킴.</br>
</br>
</br>

##  아이노드 블록의 구조

1) Mode, ID, Size, Links, Timestamps</br>
inode 메타 데이터가 기록되는 영역</br>
</br>
2) Direct Blocks(12개)</br>
각 주소 공간은 실제 데이터 블록을 가리키게 됨.</br>
12개의 주소공간을 갖으며 각 데이터 블록은 4KB 크기를 갖으으며 전체 12개로 구성되어 있기에 총 48KB 용량의 영역을 갖음.</br>
</br>
3) Single Indirect Block</br>
Single indirect block은 1개로 구성되어 있으며 전체 4KB의 크기를 갖음.</br>
데이터 블록의 주소를 가리키는 4byte 단위의 포인터로 구성되어 있으므로 4KB의 공간을 포인터로 채운다면, 총 1024개의 포인터를 채울 수 있음.</br>
1024개의 포인터가 4KB짜리 데이터 블록을 가리키므로, `1024 * 4KB = 4MB`의 용량의 관리가 가능함.</br>
</br>
4) Double Indirect Block</br>
Double indirect block은 1개로 구성되어 있으므로 총 4KB의 크기를 갖음.</br>
Single indirect block을 가리키는 포인터로 구성되어 있으므로 `1024 * 1024 * 4KB = 4GB` 의 용량의 관리가 가능함.</br>
</br>
5) Triple Indirect Block</br>
Single indirect block, Double indirect block과 동일한 방식으로 작동함</br>
Double indirect block을 가리키는 포인터로 구성되어 있으므로 `1024 * 1024 * 1024 * 4KB = 4TB` 의 용량의 관리가 가능함.</br>
</br>
