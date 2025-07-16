리눅스 상대 주소 실습 문제
사전 준비: 실습 환경 설정
다음 명령어로 실습 환경을 준비하세요:


```shell
mkdir -p ~/practice/project/{src,docs,tests,config}
mkdir -p ~/practice/project/src/{main,utils}
mkdir -p ~/practice/project/docs/{user,dev}
mkdir -p ~/practice/project/tests/unit
touch ~/practice/project/README.md
touch ~/practice/project/src/main/app.py
touch ~/practice/project/src/utils/helper.py
touch ~/practice/project/docs/user/manual.txt
touch ~/practice/project/docs/dev/api.md
touch ~/practice/project/tests/test_main.py
touch ~/practice/project/config/settings.conf
```

완성된 디렉토리 구조:
~/practice/project/
├── README.md
├── src/
│   ├── main/
│   │   └── app.py
│   └── utils/
│       └── helper.py
├── docs/
│   ├── user/
│   │   └── manual.txt
│   └── dev/
│       └── api.md
├── tests/
│   ├── unit/
│   └── test_main.py
└── config/
    └── settings.conf

```shell
[im@localhost practice]$ tree
.
└── project
    ├── config
    │   └── settings.conf
    ├── docs
    │   ├── dev
    │   │   └── api.md
    │   └── user
    │       └── manual.txt
    ├── README.md
    ├── src
    │   ├── main
    │   │   └── app.py
    │   └── utils
    │       └── helper.py
    └── tests
        ├── test_main.py
        └── unit

```


연습문제 1: 기본 상대 주소 이해
1-1. 현재 위치에서 상대 주소 작성
현재 위치가 ~/practice/project/src/main/일 때, 다음 파일들로 이동하는 상대 주소를 작성하시오:
helper.py 파일
```shell
[im@localhost ~]$ cd ./practice/project/src/main
[im@localhost main]$ pwd
/home/im/practice/project/src/main
[im@localhost main]$ cd ../utils
[im@localhost utils]$ ls
helper.py
```

README.md 파일
```shell
[im@localhost main]$ cd ../../
[im@localhost project]$ ls
config  docs  README.md  src  tests

```

manual.txt 파일
```shell
[im@localhost main]$ cd ../../docs/user
[im@localhost user]$ ls
manual.txt
```

settings.conf 파일
```shell
[im@localhost main]$ cd ../../config
[im@localhost config]$ ls
settings.conf
```

1-2. 상대 주소 검증
위에서 작성한 상대 주소가 정확한지 다음 명령어로 확인하시오:
cd ~/practice/project/src/main/
ls [상대주소]
```shell
[im@localhost practice]$ cd ~/practice/project/src/main
[im@localhost main]$ ls
app.py
```


연습문제 2: 다양한 시작점에서의 상대 주소
2-1. 시작점 변경 실습

현재 위치가 ~/practice/project/docs/user/일 때:
app.py 파일로 이동하는 상대 주소를 작성하시오.
```shell
[im@localhost user]$ cd ../../src/main
[im@localhost main]$ ls
app.py
```

test_main.py 파일로 이동하는 상대 주소를 작성하시오.
```shell
[im@localhost user]$ cd ../../tests
[im@localhost tests]$ ls
test_main.py  unit
```

src/utils/ 디렉토리로 이동하는 상대 주소를 작성하시오.
```shell
[im@localhost user]$ cd ../../src/utils
[im@localhost utils]$ ls
helper.py
[im@localhost utils]$ pwd
/home/im/practice/project/src/utils
```

2-2. 역방향 상대 주소

현재 위치가 ~/practice/project/tests/unit/일 때:
프로젝트 루트(~/practice/project/)로 이동하는 상대 주소를 작성하시오.

```shell
[im@localhost unit]$ pwd
/home/im/practice/project/tests/unit
[im@localhost unit]$ cd /
[im@localhost /]$ pwd
/
```

api.md 파일로 이동하는 상대 주소를 작성하시오.
```shell
[im@localhost unit]$ pwd
/home/im/practice/project/tests/unit
[im@localhost unit]$ cd ../../docs/dev
[im@localhost dev]$ ls
api.md
```

helper.py 파일로 이동하는 상대 주소를 작성하시오.
```shell
[im@localhost unit]$ cd ../../src/utils
[im@localhost utils]$ ls
helper.py
```

연습문제 3: 파일 내용 확인 및 조작
3-1. 상대 주소를 이용한 파일 내용 출력

현재 위치가 ~/practice/project/src/utils/일 때:
프로젝트 루트의 README.md 파일 내용을 출력하시오.
```shell
[im@localhost project]$ cat > README.md

^C #README.md 내용 없음
```
docs/user/manual.txt 파일 정보 자세히 출력하시오.
```shell
[im@localhost user]$ cat > manual.txt

^C #manual.txt 내용 없음
```
config/settings.conf 파일 정보 자세히 출력하시오.
```shell
[im@localhost config]$ cat > settings.conf

^C #settings.conf 내용 없음
```
3-2. 상대 주소를 이용한 파일 생성
현재 위치가 ~/practice/project/src/main/일 때:

현재 디렉토리에 config.py 파일을 생성하고 "# Configuration module"이라는 내용을 작성하시오.
```shell
[im@localhost main]$ echo "# Configuration module" > config.py
[im@localhost main]$ ls
app.py  config.py
```

tests/ 디렉토리에 test_app.py 파일을 생성하고 "# App test file"이라는 내용을 작성하시오.
```shell
[im@localhost main]$ cd ../../tests
[im@localhost tests]$ echo "# App test file" > test_app.py
[im@localhost tests]$ ls
test_app.py  test_main.py  unit
```

연습문제 4: 파일 복사 및 이동
4-1. 상대 주소를 이용한 파일 복사

현재 위치가 ~/practice/project/docs/dev/일 때:
api.md 파일을 docs/user/ 디렉토리에 api_copy.md로 복사하시오.
```shell
[im@localhost user]$ cp api.md api_copy.md
[im@localhost user]$ ls
api_copy.md  api.md  manual.txt

```

src/utils/helper.py 파일을 현재 디렉토리에 복사하시오.
```shell
[im@localhost docs]$ cd ~/practice/project/docs/dev/
[im@localhost dev]$ cd ../../src/utils
[im@localhost utils]$ cp helper.py ../../docs/dev
[im@localhost utils]$ cd ~/practice/project/docs/dev/
[im@localhost dev]$ ls
api.md  helper.py
```

config/settings.conf 파일을 tests/unit/ 디렉토리에 복사하시오.
```shell
[im@localhost config]$ cp settings.conf ../tests/unit
[im@localhost config]$ cd ~/practice/project/tests/unit
[im@localhost unit]$ ls
settings.conf
```

4-2. 상대 주소를 이용한 파일 이동
현재 위치가 ~/practice/project/tests/일 때:
test_main.py 파일을 tests/unit/ 디렉토리로 이동하시오.
```shell
[im@localhost tests]$ mv test_main.py unit
[im@localhost tests]$ ls
test_app.py  unit
[im@localhost tests]$ cd unit
[im@localhost unit]$ ls
settings.conf  test_main.py
```

src/main/config.py 파일을 config/ 디렉토리로 이동하시오.
```shell
[im@localhost main]$ mv  config.py ../../config
[im@localhost main]$ ls
app.py
[im@localhost main]$ cd ../../config
[im@localhost config]$ ls
config.py  settings.conf
```

연습문제 5: 복합 상대 주소 활용
5-1. 다중 파일 조작
현재 위치가 ~/practice/project/일 때:
src/main/ 디렉토리의 모든 파일을 docs/dev/ 디렉토리에 복사하시오.
```shell
[im@localhost project]$ pwd
/home/im/practice/project
[im@localhost project]$ cd src/main
[im@localhost main]$ cp app.py ../../docs/dev
[im@localhost main]$ cd ~/practice/project/docs/dev
[im@localhost dev]$ ls
api.md  app.py  helper.py
```

docs/user/ 디렉토리의 모든 파일을 tests/unit/ 디렉토리로 복사하시오.
```shell
[im@localhost user]$ cp -r *../../tests/unit
cp: missing destination file operand after '*../../tests/unit'
Try 'cp --help' for more information.
[im@localhost user]$ cp api.md manual.txt ../../tests/unit
[im@localhost user]$ cd ..
[im@localhost docs]$ cd ..
[im@localhost project]$ cd tests/unit
[im@localhost unit]$ ls
api.md  manual.txt  settings.conf  test_main.py
```

config/ 디렉토리 전체를 backup_config/로 복사하시오.
```shell
bakcup_config  config  docs  README.md  src  tests
[im@localhost project]$ rm -r bakcup_config/
[im@localhost project]$ mkdir backup_config
[im@localhost project]$ cd config
[im@localhost config]$ cp config.py settings.conf ../backup_config/
[im@localhost config]$ cd ..
[im@localhost project]$ ls
backup_config  config  docs  README.md  src  tests
[im@localhost project]$ cd backup_config
[im@localhost backup_config]$ ls
config.py  settings.conf
```

연습문제 6: 에러 찾기 및 수정
6-1. 잘못된 상대 주소 찾기
현재 위치가 ~/practice/project/docs/user/일 때, 다음 명령어들 중 에러가 있는 것을 찾고 올바른 명령어로 수정하시오:
# A
ls ../../../project/src/main/


# B
cat ../../src/utils/helper.py


# C
cd ../dev/../../config/


# D
cp manual.txt ../../tests/unit/backup.txt


E 오류
# E 
mv api_copy.md ../../../src/main/

```shell
mv api_copy.md ../../src/main/
```

6-2. 경로 최적화
다음 상대 주소를 더 간단하게 최적화하시오:
현재 위치: ~/practice/project/tests/unit/

../../src/main/../utils/helper.py
```shell
[im@localhost unit]$ cd ../../src/utils
[im@localhost utils]$ ls
helper.py
```
../../docs/user/../dev/api.md

```shell
[im@localhost unit]$ cd ../../docs/user
[im@localhost user]$ ls
api.md  manual.txt
```

../../config/../README.md
```shell
[im@localhost unit]$ cd ../../
[im@localhost project]$ ls
backup_config  config  docs  README.md  src  tests
```


연습문제 7: 종합 실습
7-1. 프로젝트 구조 재정리
현재 위치가 ~/practice/project/일 때, 다음 작업을 수행하시오:
src/main/ 디렉토리에 models/ 하위 디렉토리를 생성하시오.
```shell
[im@localhost project]$ cd src/main
[im@localhost main]$ ls
api_copy.md  app.py
[im@localhost main]$ mkdir models
[im@localhost main]$ ls
api_copy.md  app.py  models
```

docs/ 디렉토리에 README.md 파일을 생성하고 "# Project Documentation"이라는 내용을 작성하시오.
```shell
[im@localhost docs]$ echo "# Project Documentation" > README.md
[im@localhost docs]$ ls
dev  README.md  user
```

tests/unit/ 디렉토리의 모든 파일을 tests/ 디렉토리로 이동하시오.
```shell
[im@localhost tests]$ cd unit
[im@localhost unit]$ mv api.md backup.txt manual.txt settings.conf test_main.py ../
[im@localhost unit]$ cd ..
[im@localhost tests]$ ls
api.md  backup.txt  manual.txt  settings.conf  test_main.py  unit
[im@localhost tests]$ 
```

config/ 디렉토리의 모든 파일을 src/ 디렉토리에 복사하시오.
```shell
[im@localhost project]$ cd config
[im@localhost config]$ ls
config.py  settings.conf
[im@localhost config]$ cp config.py settings.conf ../src
[im@localhost config]$ cd ../src
[im@localhost src]$ ls
config.py  main  settings.conf  utils
```

7-2. 백업 및 정리
현재 위치가 ~/practice/project/src/main/일 때:

전체 프로젝트를 ../../project_backup/으로 복사하시오.
```shell
[im@localhost main]$ pwd
/home/im/practice/project/src/main
[im@localhost main]$ cd ../..
[im@localhost project]$ cd ..
[im@localhost practice]$ mkdir project_backup
[im@localhost practice]$ cp -r project ./project_backup/
[im@localhost practice]$ ls
project  project_backup
```

utils/ 디렉토리의 모든 .py 파일을 현재 디렉토리의 models/ 디렉토리로 복사하시오.
```shell
[im@localhost utils]$ cp helper.py ../main/models
[im@localhost utils]$ ls ../main/models
helper.py
```

프로젝트 루트의 README.md 파일을 현재 디렉토리에 PROJECT_INFO.md로 복사하시오.
```shell
[im@localhost project]$ cp README.md PROJECT_INFO.md
[im@localhost project]$ ls
backup_config  config  docs  PROJECT_INFO.md  README.md  src  tests
```

