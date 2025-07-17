Linux 파일 관리 명령어 와일드카드 실습 문제
실습 환경 설정
먼저 다음 명령어들을 실행하여 실습 환경을 구성하세요:

# 실습 디렉터리 생성

mkdir wildcard_file_practice

cd wildcard_file_practice

# 테스트 파일들 생성

touch report1.txt report2.txt report3.txt

touch data1.csv data2.csv data3.csv data_old.csv

touch image1.jpg image2.jpg image3.png photo.gif

touch backup_2023.tar backup_2024.tar config.conf

touch log_error.txt log_access.txt log_system.txt

touch temp1.tmp temp2.tmp temp3.tmp

touch file_001.dat file_002.dat file_010.dat

touch script1.sh script2.sh test_script.sh

touch document.pdf presentation.ppt spreadsheet.xls

touch readme.md changelog.md license.txt

touch old_report.txt new_report.txt final_report.txt

```shell
touch report{1..3}.txt
touch data{1,2,3,old}.csv
touch image{1..2}.jpg image.png photo.gif
touch backup_{2023,2024}.tar config.conf
touch log_{error,access,system}.txt
touch temp{1..3}.tmp
touch file_{001,002,010}.dat
touch script{1,2}.sh test_script.sh
touch document.pdf presentation.ppt spreadsheet.xls
touch {read,changelog}.md license.txt
touch {old,new,final}_report.txt
```

# 기본 디렉터리들 생성

mkdir archives backup logs images documents scripts


1. mkdir 명령어 와일드카드 실습
1-1. 연도별 백업 디렉터리 생성
# 2020년부터 2024년까지 백업 디렉터리를 한 번에 생성하세요

# 예: backup_2020, backup_2021, backup_2022, backup_2023, backup_2024

```shell
[im@localhost wildcard_file_practice]$ mkdir backup_{2020..2024}
```

# 명령어를 작성하세요:
1-2. 월별 로그 디렉터리 생성
# logs 디렉터리 안에 01월부터 12월까지 디렉터리 생성

# 예: logs/log_01, logs/log_02, ..., logs/log_12

```shell
[im@localhost wildcard_file_practice]$ mkdir logs/log_{01..12}
[im@localhost wildcard_file_practice]$ ls -l logs
total 0
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_01
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_02
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_03
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_04
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_05
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_06
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_07
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_08
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_09
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_10
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_11
drwxr-xr-x. 2 im im 6 Jul 17 17:52 log_12
```

# 명령어를 작성하세요:
1-3. 프로젝트별 디렉터리 생성
# project_A, project_B, project_C 디렉터리를 한 번에 생성하세요
```shell
[im@localhost wildcard_file_practice]$ mkdir project_{A..C}
```

# 명령어를 작성하세요:
1-4. 계층적 디렉터리 생성
# data/2024/{01,02,03} 구조로 디렉터리를 생성하세요

# (data 디렉터리 안에 2024 디렉터리, 그 안에 01, 02, 03 디렉터리)

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ mkdir -p data/2024/{01,02,03}
```


2. cp 명령어 와일드카드 실습
2-1. 확장자별 파일 복사
# 모든 .txt 파일을 backup 디렉터리로 복사하세요

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ cp *.txt ./backup
```

2-2. 특정 패턴 파일 복사
# "report"로 시작하는 모든 파일을 documents 디렉터리로 복사하세요

# 명령어를 작성하세요:

```shell
[im@localhost wildcard_file_practice]$ cp report*.* documents
[im@localhost wildcard_file_practice]$ ls -l documents
total 0
-rw-r--r--. 1 im im 0 Jul 17 17:59 report1.txt
-rw-r--r--. 1 im im 0 Jul 17 17:59 report2.txt
-rw-r--r--. 1 im im 0 Jul 17 17:59 report3.txt
```

2-3. 숫자가 포함된 파일 복사 (여기까지)
# 파일명에 숫자가 포함된 모든 이미지 파일(.jpg, .png)을 images 디렉터리로 복사하세요

# 명령어를 작성하세요:

```shell
[im@localhost wildcard_file_practice]$ cp *[0-9]*.{jpg,png} images && ls -l images
total 0
-rw-r--r--. 1 im im 0 Jul 17 18:04 image1.jpg
-rw-r--r--. 1 im im 0 Jul 17 18:04 image2.jpg
-rw-r--r--. 1 im im 0 Jul 17 18:04 image3.png
```

2-4. 특정 범위의 파일 복사
# data1.csv, data2.csv, data3.csv 파일만 backup 디렉터리로 복사하세요

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ ls -l backup
total 0
-rw-r--r--. 1 im im 0 Jul 17 22:44 data1.csv
-rw-r--r--. 1 im im 0 Jul 17 22:44 data2.csv
-rw-r--r--. 1 im im 0 Jul 17 22:44 data3.csv
-rw-r--r--. 1 im im 0 Jul 17 22:43 final_report.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 license.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 log_access.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 log_error.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 log_system.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 new_report.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 old_report.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 report1.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 report2.txt
-rw-r--r--. 1 im im 0 Jul 17 22:43 report3.txt
```

2-5. 복합 조건 파일 복사
# "log_"로 시작하는 .txt 파일들을 logs 디렉터리로 복사하세요

# 명령어를 작성하세요:

```shell
[im@localhost wildcard_file_practice]$ cp log_*.txt logs
[im@localhost wildcard_file_practice]$ ls logs
log_01  log_03  log_05  log_07  log_09  log_11  log_access.txt  log_system.txt
log_02  log_04  log_06  log_08  log_10  log_12  log_error.txt
```

3. mv 명령어 와일드카드 실습
3-1. 임시 파일 이동
# 모든 .tmp 파일을 temp 디렉터리로 이동하세요 (mkdir temp 먼저 실행)
```shell
[im@localhost wildcard_file_practice]$ mv *.tmp temp
[im@localhost wildcard_file_practice]$ ls temp
temp1.tmp  temp2.tmp  temp3.tmp
```

# 명령어를 작성하세요:
3-2. 백업 파일 정리
# "backup_"로 시작하는 모든 파일을 archives 디렉터리로 이동하세요
```shell
[im@localhost wildcard_file_practice]$ mv backup_*.* archives
[im@localhost wildcard_file_practice]$ ls -l archives/
total 0
-rw-r--r--. 1 im im 0 Jul 17 22:40 backup_2023.tar
-rw-r--r--. 1 im im 0 Jul 17 22:40 backup_2024.tar
```

# 명령어를 작성하세요:
3-3. 스크립트 파일 정리
# 모든 .sh 파일을 scripts 디렉터리로 이동하세요
```shell
[im@localhost wildcard_file_practice]$ mv *.sh scripts
[im@localhost wildcard_file_practice]$ ls -l scripts/
total 0
-rw-r--r--. 1 im im 0 Jul 17 22:40 script1.sh
-rw-r--r--. 1 im im 0 Jul 17 22:40 script2.sh
-rw-r--r--. 1 im im 0 Jul 17 22:40 test_script.sh
```

# 명령어를 작성하세요:
3-4. 특정 패턴 파일 이동
# "file_"로 시작하고 3자리 숫자가 포함된 .dat 파일들을 data 디렉터리로 이동하세요

# 명령어를 작성하세요

```shell
[im@localhost wildcard_file_practice]$ mv file_[0-9][0-9][0-9].dat data && ls -l data
total 0
drwxr-xr-x. 5 im im 36 Jul 17 22:42 2024
-rw-r--r--. 1 im im  0 Jul 17 22:40 file_001.dat
-rw-r--r--. 1 im im  0 Jul 17 22:40 file_002.dat
-rw-r--r--. 1 im im  0 Jul 17 22:40 file_010.dat
```

3-5. 조건부 파일 이동
# "old_" 또는 "new_"로 시작하는 모든 파일을 archives 디렉터리로 이동하세요

# 명령어를 작성하세요:

```shell
[im@localhost wildcard_file_practice]$ mv {old,new}_*.* archives/
[im@localhost wildcard_file_practice]$ ls -l archives/
total 0
-rw-r--r--. 1 im im 0 Jul 17 22:40 backup_2023.tar
-rw-r--r--. 1 im im 0 Jul 17 22:40 backup_2024.tar
-rw-r--r--. 1 im im 0 Jul 17 22:40 new_report.txt
-rw-r--r--. 1 im im 0 Jul 17 22:40 old_report.txt
```

4. rm 명령어 와일드카드 실습
4-1. 임시 파일 삭제
# 모든 .tmp 파일을 삭제하세요 (주의: 실제로는 신중히 실행)
```shell
[im@localhost wildcard_file_practice]$ rm ./temp/*.tmp
```

# 명령어를 작성하세요:
4-2. 특정 패턴 파일 삭제
# "temp"로 시작하는 모든 파일을 삭제하세요
```shell
[im@localhost wildcard_file_practice]$ rm temp*.*
rm: cannot remove 'temp*.*': No such file or directory
# temp로 시작하는 파일 없음.
```
# 명령어를 작성하세요:
4-3. 백업 파일 정리
# 2023년 백업 파일만 삭제하세요 (backup_2023.tar)
```shell
[im@localhost wildcard_file_practice]$ rm ./archives/backup_2023.tar
```

# 명령어를 작성하세요:
4-4. 조건부 파일 삭제
# 확장자가 3글자가 아닌 파일들을 삭제하세요

# 힌트: 확장자가 .jpg, .png, .gif, .txt, .csv, .tar, .dat, .pdf, .ppt, .xls가 아닌 파일

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ rm *.!(???)
```

5. 복합 명령어 실습
5-1. 파일 정리 시스템
# 1단계: 모든 이미지 파일(.jpg, .png, .gif)을 images 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv *.{jpg,png,gif} images
[im@localhost wildcard_file_practice]$ ls images
image1.jpg  image2.jpg  image3.png  photo.gif
```

# 2단계: 모든 문서 파일(.pdf, .ppt, .xls, .md)을 documents 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv *.{pdf,ppt,xls,md} documents
mv: cannot stat '*.md': No such file or directory
# md 확장자 파일 없음
[im@localhost wildcard_file_practice]$ ls documents
document.pdf  presentation.ppt  report1.txt  report2.txt  report3.txt  spreadsheet.xls

```

# 3단계: 모든 데이터 파일(.csv, .dat)을 data 디렉터리로 이동 (없으면 생성)
```shell
[im@localhost wildcard_file_practice]$ mv *.{csv,dat} data
mv: cannot stat '*.dat': No such file or directory
[im@localhost wildcard_file_practice]$ ls data
2024  data1.csv  data2.csv  data3.csv  data_old.csv  file_001.dat  file_002.dat  file_010.dat

```

# 명령어들을 작성하세요:
5-2. 백업 및 정리 작업
# 1단계: 모든 .txt 파일을 backup/txt_files 디렉터리로 복사 (디렉터리 생성 필요)
```shell
[im@localhost wildcard_file_practice]$ mkdir backup/txt_files
[im@localhost wildcard_file_practice]$ cp *.txt backup/txt_files
[im@localhost wildcard_file_practice]$ ls backup/txt_files
final_report.txt  log_access.txt  log_system.txt  report2.txt
license.txt       log_error.txt   report1.txt     report3.txt
```

# 2단계: 모든 설정 파일(.conf)을 backup/config 디렉터리로 복사
```shell
[im@localhost wildcard_file_practice]$ cp *.conf backup/config
cp: cannot stat '*.conf': No such file or directory
# conf 확장자 파일 없음
```
# 3단계: 원본 설정 파일들을 삭제
```shell
#원본 설정 파일이 무엇인지 확인 필요
```

# 명령어들을 작성하세요:
5-3. 날짜별 로그 정리
# 1단계: logs 디렉터리에 error, access, system 하위 디렉터리 생성
```shell
[im@localhost wildcard_file_practice]$ mkdir -p ./logs/{error,acess,system}
[im@localhost wildcard_file_practice]$ ls -l logs
total 0
drwxr-xr-x. 2 im im 6 Jul 17 23:21 acess
drwxr-xr-x. 2 im im 6 Jul 17 23:21 error
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_01
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_02
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_03
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_04
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_05
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_06
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_07
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_08
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_09
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_10
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_11
drwxr-xr-x. 2 im im 6 Jul 17 22:41 log_12
-rw-r--r--. 1 im im 0 Jul 17 22:46 log_access.txt
-rw-r--r--. 1 im im 0 Jul 17 22:46 log_error.txt
-rw-r--r--. 1 im im 0 Jul 17 22:46 log_system.txt
drwxr-xr-x. 2 im im 6 Jul 17 23:21 system
```

# 2단계: log_error.txt를 logs/error/로 이동
```shell
[im@localhost wildcard_file_practice]$ mv ./logs/log_error.txt ./logs/error/
[im@localhost wildcard_file_practice]$ ls ./logs/error/
log_error.txt
```

# 3단계: log_access.txt를 logs/access/로 이동
```shell
[im@localhost wildcard_file_practice]$ mv ./logs/log_access.txt ./logs/access/
[im@localhost wildcard_file_practice]$ ls ./logs/access/
log_access.txt
```
# 4단계: log_system.txt를 logs/system/로 이동
```shell
[im@localhost wildcard_file_practice]$ mv ./logs/log_system.txt ./logs/system/
[im@localhost wildcard_file_practice]$ ls ./logs/system/
log_system.txt
```


6. 고급 와일드카드 실습
6-1. 복잡한 패턴 매칭
# "report" 또는 "data"로 시작하고 숫자가 포함된 모든 파일을 찾아서 processed 디렉터리로 복사하세요

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ cp {report,data}[0-9]*.* processed
cp: cannot stat 'data[0-9]*.*': No such file or directory
# data로 시작하고 숫자가 포함된 파일이 없음
```

6-2. 제외 패턴 활용
# 모든 파일 중에서 "final_"로 시작하지 않는 .txt 파일들을 draft 디렉터리로 이동하세요

# 명령어를 작성하세요:

```shell
[im@localhost wildcard_file_practice]$ mv !(final_*).txt draft
[im@localhost wildcard_file_practice]$ ls draft
license.txt  log_access.txt  log_error.txt  log_system.txt  report1.txt  report2.txt  report3.txt
```

6-3. 범위 지정 패턴
# 파일명에 001부터 009까지의 숫자가 포함된 파일들을 single_digit 디렉터리로 복사하세요

# 명령어를 작성하세요:
```shell
[im@localhost wildcard_file_practice]$ cp *[0-9][0-9][0-9]*.* single_digit/
cp: cannot stat '*[0-9][0-9][0-9]*.*': No such file or directory
```

7. 실전 시나리오 문제
7-1. 프로젝트 정리 시나리오
# 시나리오: 프로젝트 종료 후 파일 정리

# 1. 완료된 리포트 파일들(report*.txt)을 completed 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv report*.txt completed/

```
# 2. 작업 중인 파일들(temp*, *_draft)을 ongoing 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv temp*.* ongoing/ && mv *_draft.* ongoing/
```

# 3. 백업 파일들(backup_*)을 archive 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv backup_*.* archive/
```

# 4. 불필요한 임시 파일들(*.tmp)을 삭제
```shell
[im@localhost wildcard_file_practice]$ rm *.tmp.*
```

7-2. 로그 관리 시나리오
# 시나리오: 서버 로그 정리

# 1. 2024년 로그 파일들을 logs/2024 디렉터리로 이동

# 2. 에러 로그들을 logs/errors 디렉터리로 복사

# 3. 2023년 로그 파일들을 삭제

# 4. 시스템 로그들을 logs/system 디렉터리로 이동

7-3. 개발 환경 정리 시나리오
# 시나리오: 개발 프로젝트 구조 정리

# 1. 모든 스크립트 파일(*.sh)을 scripts 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv *.sh scripts/
```

# 2. 설정 파일들(*.conf, *.config)을 config 디렉터리로 복사
```shell
[im@localhost wildcard_file_practice]$ cp *.{conf,config}.* config/
```
# 3. 문서 파일들(*.md, *.txt)을 docs 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv *.{md,txt}.* docs/
```

# 4. 데이터 파일들(*.csv, *.dat)을 data 디렉터리로 이동
```shell
[im@localhost wildcard_file_practice]$ mv *.{csv,dat}.* data/
```



# 존재하지 않으면 디렉터리를 생성한 후 이동하는 명령어를 작성하세요

# 명령어를 작성하세요:


힌트
{} 중괄호 확장 활용: mkdir {dir1,dir2,dir3}
[] 문자 범위 활용: [1-3], [a-z]
* 와일드카드 활용: file*, *.txt
? 단일 문자 활용: file?.txt
복합 패턴 활용: *[0-9]*, file[1-3].txt
디렉터리 생성 시 -p 옵션 활용: mkdir -p path/to/directory
