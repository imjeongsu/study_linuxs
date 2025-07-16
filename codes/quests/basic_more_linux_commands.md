~~연습문제 1: 기본 파일 시스템 탐색

1-1. 현재 위치 확인 및 이동

현재 작업 디렉터pw리의 절대 경로를 출력하시오.
```shell
[im@localhost ~]$ pwd
/home/im
```

홈 디렉터리로 이동하시오.
```shell
[im@localhost ~]$ cd /home
[im@localhost home]
```

루트 디렉터리(/)로 이동하시오.
```shell
[im@localhost home]$ cd /
[im@localhost /]$ pwd
```

다시 홈 디렉터리로 돌아가시오.
```shell
[im@localhost /]$ cd /home
[im@localhost home]$ ls
```

1-2. 디렉터리 내용 확인

현재 디렉터리의 파일과 폴더 목록을 출력하시오
```shell
[im@localhost home]$ ls
im
```

숨김 파일을 포함한 모든 파일의 상세 정보를 출력하시오.
```shell
[im@localhost home]$ ls -al
total 4
drwxr-xr-x.  3 root root   16 Jul 16 10:52 .
dr-xr-xr-x. 18 root root  235 Jul 16 10:12 ..
drwx------. 15 im   im   4096 Jul 16 11:19 im
```

/etc 디렉터리의 내용을 확인하시오.

연습문제 2: 디렉터리 및 파일 생성

2-1.  디렉터리 구조 생성

다음과 같은 디렉터리 구조를 생성하시오:
```
practice/

├── documents/
│   ├── reports/ls
│   └── notes/
├── images/
└── backup/””
```

```shell
[im@localhost practice]$ mkdir documents
[im@localhost practice]$ cd documents/
[im@localhost documents]$ mkdir reports
[im@localhost documents]$ mkdir notes
[im@localhost documents]$ cd ..
[im@localhost practice]$ mkdir images
[im@localhost practice]$ mkdir backup
[im@localhost practice]$ ls
backup  documents  images
[im@localhost practice]$ cd documents/
[im@localhost documents]$ ls
notes  reports

[im@localhost practice]$ ls
backup  documents  images

```

2-2. 파일 생성 및 내용 작성

practice/documents/ 디렉터리에 readme.txt 파일을 생성하고 "Hello Linux!"라는 내용을 작성하시오.
```shell
[im@localhost documents]$ cat > readme.txt
Hello Linux!
```

practice/notes/ 디렉터리에 memo.txt 파일을 생성하고 "Linux 명령어 연습 중"이라는 내용을 작성하시오.

```shell
[im@localhost documents]$ cd notes/
[im@localhost notes]$ cat > memo.txt
Linux Commang Practicing
```
연습문제 3: 파일 내용 확인 및 조작

3-1. 파일 내용 출력

앞서 생성한 readme.txt 파일의 내용을 출력하시오.
```shell
[im@localhost documents]$ cat readme.txt
Hello Linux!
```

memo.txt 파일의 내용을 출력하시오.
```shell
[im@localhost notes]$ cat memo.txt
Linux Commang Practicing
```

3-2. 파일 복사

readme.txt 파일을 backup/ 디렉터리에 복사하시오.
```shell
[im@localhost documents]$ cp readme.txt /home/im/practice/backup
[im@localhost documents]$ cd ..
[im@localhost practice]$ cd backup
[im@localhost backup]$ ls
readme.txt
```

documents/ 디렉터리 전체를 backup/ 디렉터리에 복사하시오.
```shell
[im@localhost practice]$ cp -r /home/im/practice/documents /home/im/practice/backup
[im@localhost practice]$ cd backup
[im@localhost backup]$ ls
documents  readme.txt
```

연습문제 4: 파일 이동 및 이름 변경

4-1. 파일 이동

memo.txt 파일을 documents/ 디렉터리로 이동하시오.

images/ 디렉터리를 practice/media/로 이름을 변경하시오.

4-2. 파일 이름 변경

readme.txt를 introduction.txt로 이름을 변경하시오.
```shell
[im@localhost documents]$ rename readme.txt introduction.txt /home/im/practice/documents/readme.txt
[im@localhost documents]$ ls
introduction.txt  notes  reports
```

memo.txt를 study_notes.txt로 이름을 변경하시오.
```shell
im@localhost documents]$ rename memo.txt study_notes.txt /home/im/practice/documents/notes/memo.txt
[im@localhost documents]$ ls
introduction.txt  notes  reports
[im@localhost documents]$ cd notes
[im@localhost notes]$ ls
study_notes.txt
```

연습문제 5: 종합 실습

5-1. 프로젝트 디렉터리 생성

다음 요구사항에 따라 프로젝트 디렉터리를 생성하시오:

my_project/라는 최상위 디렉터리 생성
```shell
[im@localhost practice]$ mkdir my_project
```

하위에 src/, docs/, tests/, config/ 디렉터리 생성
```shell
[im@localhost my_project]$ mkdir src docs tests config
[im@localhost my_project]$ ls
config  docs  src  tests
[im@localhost my_project]$ tree
.
├── config
├── docs
├── src
└── tests
```

src/ 디렉터리에 main.py 파일 생성 (내용: "# Main Python File")
```shell
[im@localhost src]$ touch main.py
[im@localhost src]$ ls
main.py
[im@localhost src]$ echo "# Main Python File") > main.py
[im@localhost src]$ cat main.py

```
docs/ 디렉터리에 README.md 파일 생성 (내용: "# My Project Documentation")
```shell
[im@localhost my_project]$ cd docs
[im@localhost docs]$ touch README.md
[im@localhost docs]$ ls
README.md
[im@localhost src]$ echo "# My Project Documentation" > README.md
[im@localhost src]$ cat README.md

```
config/ 디렉터리에 settings.conf 파일 생성 (내용: "# Configuration File")
```shell
[im@localhost my_project]$ cd config
[im@localhost config]$ touch settings.conf
[im@localhost config]$ ls
settings.conf
[im@localhost src]$ echo "# Configuration File" > settings.conf
[im@localhost src]$ cat settings.conf


```
5-2. 백업 및 정리

전체 my_project/ 디렉터리를 my_project_backup/으로 복사하시오.
```shell
[im@localhost practice]$ cp -r /home/im/practice/my_project /home/im/practice/my_project_backup
[im@localhost practice]$ ls
backup  documents  images  my_project  my_project_backup
```

my_project/src/main.py 파일을 my_project/src/app.py로 이름을 변경하시오.
```shell
[im@localhost practice]$ rename main.py app.py /home/im/practice/my_project/src/main.py
[im@localhost practice]$ cd my_project
[im@localhost my_project]$ cd src
[im@localhost src]$ ls
app.py
```

my_project/docs/README.md 파일을 my_project/ 디렉터리로 이동하시오.
```shell
[im@localhost practice]$ mv /home/im/practice/my_project/docs/README.md /home/im/practice/my_project
```