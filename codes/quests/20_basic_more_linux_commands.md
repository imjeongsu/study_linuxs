기본 명령어 연습 문제

📁 Level 1: 기본 탐색 및 폴더 조작

문제 1-1: 현재 위치 확인
현재 작업 중인 디렉터리의 경로를 확인하세요

```shell
PS C:\Develops\quests> pwd

Path
----
C:\Develops\quests
```


문제 1-2: 폴더 구조 만들기
다음 폴더 구조를 생성하세요:
powershell_practice/
├── documents/
├── images/
├── backup/
└── temp/

```shell
PS C:\Develops\quests> mkdir powershell_practice


    디렉터리: C:\Develops\quests


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:38                powershell_practice


PS C:\Develops\quests> cd powershell_practice
PS C:\Develops\quests\powershell_practice> mkdir documents


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:38                documents
PS C:\Develops\quests\powershell_practice> mkdir images


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:38                images


PS C:\Develops\quests\powershell_practice> mkdir backup


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:38                backup


PS C:\Develops\quests\powershell_practice> mkdir temp


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:39                temp


PS C:\Develops\quests\powershell_practice> ls


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:38                backup
d-----      2025-07-15   오후 3:38                documents
d-----      2025-07-15   오후 3:38                images
d-----      2025-07-15   오후 3:39                temp


PS C:\Develops\quests\powershell_practice> tree
폴더 PATH의 목록입니다.
볼륨 일련 번호는 52B6-33C5입니다.
C:.
├─backup
├─documents
├─images
└─temp
```

문제 1-3: 폴더 탐색
documents 폴더로 이동하세요
```shell
PS C:\Develops\quests\powershell_practice> cd documents
PS C:\Develops\quests\powershell_practice\documents>
```

현재 폴더의 내용을 확인하세요 (비어있을 것입니다)
```shell
PS C:\Develops\quests\powershell_practice\documents> ls
PS C:\Develops\quests\powershell_practice\documents>
```
다시 상위 폴더로 돌아가세요
```shell
PS C:\Develops\quests\powershell_practice\documents> cd ..
PS C:\Develops\quests\powershell_practice> pwd

Path
----
C:\Develops\quests\powershell_practice
```


📄 Level 2: 파일 생성 및 조작

문제 2-1: 텍스트 파일 생성

documents 폴더에 hello.txt 파일을 생성하고 "Hello PowerShell!" 내용을 입력하세요
```shell
PS C:\Develops\quests\powershell_practice> cd documents
PS C:\Develops\quests\powershell_practice\documents> "Hellow PowerShell!" > hello.txt
```

images 폴더에 photo1.jpg, photo2.png 빈 파일을 생성하세요
```shell
PS C:\Develops\quests\powershell_practice\images> New-Item -ItemType File > photo1.jpg

cmdlet New-Item(명령 파이프라인 위치 1)
다음 매개 변수에 대한 값을 제공하십시오.
Path[0]: C:\Develops\quests\powershell_practice\images
Path[1]: C:\Develops\quests\powershell_practice\images
Path[2]: C:\Develops\quests\powershell_practice\images
Path[3]:
PS C:\Develops\quests\powershell_practice\images> New-Item -ItemType File > photo2.png

cmdlet New-Item(명령 파이프라인 위치 1)
다음 매개 변수에 대한 값을 제공하십시오.
Path[0]: C:\Develops\quests\powershell_practice\images
```
힌트: New-Item -ItemType File 또는 echo "내용" > 파일명 사용
문제 2-2: 파일 내용 확인

hello.txt 파일의 내용을 출력하세요

현재 폴더의 모든 파일과 폴더 목록을 자세히 확인하세요

문제 2-3: 파일 복사

documents/hello.txt 파일을 backup 폴더에 복사하세요
```shell
PS C:\Develops\quests\powershell_practice\documents> cp hello.txt C:\Develops\quests\powershell_practice\backup
PS C:\Develops\quests\powershell_practice\documents> cd ..
PS C:\Develops\quests\powershell_practice> cd backup
PS C:\Develops\quests\powershell_practice\backup> ls


    디렉터리: C:\Develops\quests\powershell_practice\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:44             42 hello.txt
```
images 폴더의 모든 파일을 backup 폴더에 복사하세요

```shell
PS C:\Develops\quests\powershell_practice\backup> cd ..
PS C:\Develops\quests\powershell_practice> cd images
PS C:\Develops\quests\powershell_practice\images> cp photo1.jpg C:\Develops\quests\powershell_practice\backup
PS C:\Develops\quests\powershell_practice\images> cp photo2.png C:\Develops\quests\powershell_practice\backup
PS C:\Develops\quests\powershell_practice\images> cd ..
PS C:\Develops\quests\powershell_practice> cd backup
PS C:\Develops\quests\powershell_practice\backup> ls


    디렉터리: C:\Develops\quests\powershell_practice\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:44             42 hello.txt
-a----      2025-07-15   오후 3:47              0 photo1.jpg
-a----      2025-07-15   오후 3:48              0 photo2.png
```



🔄 Level 3: 파일 이동 및 이름 변경

문제 3-1: 파일 이동

temp 폴더에 test.txt 파일을 생성하세요
```shell
PS C:\Develops\quests\powershell_practice\temp> "" > test.txt
PS C:\Develops\quests\powershell_practice\temp> ls


    디렉터리: C:\Develops\quests\powershell_practice\temp


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:55              6 test.txt

```
이 파일을 documents 폴더로 이동하세요

```shell
PS C:\Develops\quests\powershell_practice\temp> mv test.txt C:\Develops\quests\powershell_practice\documents
PS C:\Develops\quests\powershell_practice\temp> cd ..
PS C:\Develops\quests\powershell_practice> cd documents
PS C:\Develops\quests\powershell_practice\documents> ls


    디렉터리: C:\Develops\quests\powershell_practice\documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:44             42 hello.txt
-a----      2025-07-15   오후 3:55              6 test.txt

```


문제 3-2: 파일 이름 변경

documents/test.txt 파일의 이름을 moved_file.txt로 변경하세요 

images/photo1.jpg 파일의 이름을 picture1.jpg로 변경하세요

문제 3-3: 폴더 이름 변경

temp 폴더의 이름을 temporary로 변경하세요

🗑️ Level 4: 삭제 연습

문제 4-1: 개별 파일 삭제

documents/moved_file.txt 파일을 삭제하세요 #이름변경 X
```shell
PS C:\Develops\quests\powershell_practice\documents> rm test.txt
PS C:\Develops\quests\powershell_practice\documents> ls


    디렉터리: C:\Develops\quests\powershell_practice\documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:44             42 hello.txt
```
images/photo2.png 파일을 삭제하세요
```shell
PS C:\Develops\quests\powershell_practice\images> rm photo2.png
PS C:\Develops\quests\powershell_practice\images> ls


    디렉터리: C:\Develops\quests\powershell_practice\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:47              0 photo1.jpg

```

문제 4-2: 폴더 삭제

temporary 폴더를 삭제하세요 (비어있는 폴더)
```shell
PS C:\Develops\quests\powershell_practice> rm temp
PS C:\Develops\quests\powershell_practice> ls


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:53                backup
d-----      2025-07-15   오후 3:58                documents
d-----      2025-07-15   오후 3:59                images

```
backup 폴더와 그 안의 모든 내용을 삭제하세요
```shell
PS C:\Develops\quests\powershell_practice> rm backup

확인
C:\Develops\quests\powershell_practice\backup의 항목에는 하위 항목이 있으며 Recurse 매개 변수를 지정하지 않았습니다. 계속하면 해당
항목과 모든 하위 항목이 제거됩니다. 계속하시겠습니까?
[Y] 예(Y)  [A] 모두 예(A)  [N] 아니요(N)  [L] 모두 아니요(L)  [S] 일시 중단(S)  [?] 도움말 (기본값은 "Y"): y
PS C:\Develops\quests\powershell_practice> ls


    디렉터리: C:\Develops\quests\powershell_practice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:58                documents
d-----      2025-07-15   오후 3:59                images
```


🚀 Level 5: 종합 응용

문제 5-1: 프로젝트 구조 만들기

다음과 같은 프로젝트 구조를 생성하세요:

my_project/
├── src/
│   └── main.py (내용: "print('Hello World')")
├── docs/
│   └── readme.txt (내용: "This is my project")
├── tests/
└── build/

```shell
PS C:\Develops\quests> cd my_project
PS C:\Develops\quests\my_project> mkdir src


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:14                src


PS C:\Develops\quests\my_project> cd ..
PS C:\Develops\quests> cd .\my_project\src
PS C:\Develops\quests\my_project\src> cd ..
PS C:\Develops\quests\my_project> mkdir docs


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:15                docs


PS C:\Develops\quests\my_project> mkdir tests


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:15                tests


PS C:\Develops\quests\my_project> mkdir build


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:15                build


PS C:\Develops\quests\my_project> cd src
PS C:\Develops\quests\my_project\src> "print('Hello World')" > main.py
PS C:\Develops\quests\my_project> cd src
PS C:\Develops\quests\my_project\src> ls


    디렉터리: C:\Develops\quests\my_project\src


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 4:16             46 main.py

PS C:\Develops\quests\my_project> cd docs
PS C:\Develops\quests\my_project\docs> "This is my project" > readme.txt
PS C:\Develops\quests\my_project\docs> ls


    디렉터리: C:\Develops\quests\my_project\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 4:17             42 readme.txt


PS C:\Develops\quests\my_project\docs> cd ..
PS C:\Develops\quests\my_project> tree
폴더 PATH의 목록입니다.
볼륨 일련 번호는 52B6-33C5입니다.
C:.
├─build
├─docs
├─src
└─tests
```

문제 5-2: 파일 정리

src/main.py 파일을 build 폴더에 복사하세요
```shell
PS C:\Develops\quests\my_project\src> cp main.py C:\Develops\quests\my_project\build
PS C:\Develops\quests\my_project\src> ls


    디렉터리: C:\Develops\quests\my_project\src


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 4:16             46 main.py
```

docs/readme.txt 파일을 project_info.txt로 이름을 변경하세요

tests 폴더를 삭제하세요
```shell
PS C:\Develops\quests\my_project> ls


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:19                build
d-----      2025-07-15   오후 4:17                docs
d-----      2025-07-15   오후 4:16                src
d-----      2025-07-15   오후 4:15                tests


PS C:\Develops\quests\my_project> rm tests
PS C:\Develops\quests\my_project> ls


    디렉터리: C:\Develops\quests\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 4:19                build
d-----      2025-07-15   오후 4:17                docs
d-----      2025-07-15   오후 4:16                src

```

문제 5-3: 최종 확인
my_project 폴더의 모든 하위 내용을 재귀적으로 확인하세요
각 폴더로 이동하여 파일 내용을 확인하세요
