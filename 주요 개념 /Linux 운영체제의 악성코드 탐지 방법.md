# Linux 운영체제의 악성코드 탐지 방법
##### 작성자: 김태현 사원
##### 작성일자: 2024년 4월 24일
</br>


## (1) 방법
리눅스 운영체제의 경우 성능 혹은 인식 문제로 백신 설치가 미흡한 경우가 많으므로 침해사고 발생 시 피해가 겉잡을 수 없이 커질 수 있음.
<br><br>
이에 빠르게 대응하고자, 쉘 스크립트를 구동하여 웹 페이지 디렉토리 내에 악성 md5 해시값을 가진 파일이 있는지 탐지가 가능함.
<br><br>
```sh
#!/bin/bash

# 탐지할 디렉토리 지정
TARGET_DIRECTORY="/target_directory"

# 악성 파일의 MD5 해시값 목록
# 예시: MD5_VALUES=("e4d909c290d0fb1ca068ffaddf22cbd0" "another-md5-value")
MD5_VALUES=("md5-value-1" "md5-value-2" "md5-value-3")

# 타겟 디렉토리 안의 모든 파일에 대해 반복
find "$TARGET_DIRECTORY" -type f | while read -r file
do
  # 파일의 MD5 해시값 계산
  FILE_MD5=$(md5sum "$file" | awk '{ print $1 }')

  # 계산된 해시값이 악성 파일의 해시값 목록에 있는지 확인
  for md5 in "${MD5_VALUES[@]}"; do
    if [[ "$FILE_MD5" == "$md5" ]]; then
      echo "악성 파일 탐지: $file"
    fi
  done
done
```
<br><br>
다음은 리눅스 환경에서 실행할 수 있는 쉘 스크립트임. 이 스크립트는 특정 디렉토리(/target_directory) 안에 있는 모든 파일에 대해 MD5 해시값을 계산하고, 미리 정의된 악성 파일의 MD5 해시값 목록과 비교하여 일치하는 경우 해당 파일의 경로를 출력함. 다음과 같은 설정을 추가해야함.
<br><br>
1. TARGET_DIRECTORY 변수에 탐지할 디렉토리 경로를 정확히 설정
2. MD5_VALUES 배열에 탐지하고자 하는 악성 파일의 MD5 해시값을 정확히 입력
3. 터미널에서 chmod +x detect_malware.sh 명령을 사용하여 실행 권한을 부여
