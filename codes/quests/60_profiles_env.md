각 실습 후 su - 사용자명, ls -R ~/Downloads, cat 등을 통해 적용 여부를 확인하십시오.

🧪 환경 변수 및 초기화 스크립트 실습 문제
🔹 문제 1. 로그인 시마다 "Welcome, USERNAME" 메시지를 출력하시오.
조건:
현재 로그인한 사용자명을 포함할 것 ($USER)
#### nano .bash_profile 내부 
```shell
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs
echo "Welcome, $USER"
```
#### 명령어 + 결과
로그인할 때마다 자동으로 출력되도록 설정할 것
```shell
[im@localhost ~]$ su im -
Password: 
[im@localhost ~]$ echo "Welcome, $USER"
Welcome, im
```

🔹 문제 2. 로그인 시 사용자의 Downloads/ 폴더 내 일반 파일을 삭제하시오.
조건:
경로: ~/Downloads/


일반 파일만 삭제 (서브디렉토리, 숨김파일은 삭제하지 않음)


로그인 시 자동 실행
#### nano .bash_profile 내부 
```shell
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs
echo "Welcome, $USER"
rm -- ~/Downloads/*
```

```shell

#### 명령어 + 결과
[im@localhost Downloads]$ ls -l 
total 0
-rw-r--r--. 1 im im 0 Jul 22 12:04 test1.txt
-rw-r--r--. 1 im im 0 Jul 22 12:04 test2.txt
-rw-r--r--. 1 im im 0 Jul 22 12:04 test3.txt
-rw-r--r--. 1 im im 0 Jul 22 12:04 test4.txt
-rw-r--r--. 1 im im 0 Jul 22 12:04 test5.txt
[im@localhost Downloads]$ su - im
Password: 
Welcome, im
[im@localhost ~]$ ls -l Downloads/
total 0
```

🔹 문제 3. 로그인할 때마다 ~/Downloads/ 경로에 다음 구조로 디렉토리 및 파일을 자동 생성하도록 설정하시오.
생성 구조:
~/Downloads/
 └── auto_created/
      ├── info.txt
      └── logs/
           └── log.txt

조건:
파일에는 임의의 간단한 문자열이 들어갈 것


매 로그인마다 자동 생성

#### nano .bash_profile 내부 
```shell
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs
echo "Welcome, $USER"
rm Downloads/*
mkdir -p ~/Downloads/auto_created/logs && echo "Hello" >> ~/Downloads/auto_created/logs/log.txt && echo "Say Hi" >>  ~/Downloads/auto_created/info.txt
```
#### 명령어 + 결과
```shell
[im@localhost ~]$ cat Downloads/auto_created/logs/log.txt
Hello
[im@localhost ~]$ cat Downloads/auto_created/info.txt
Say Hi

```



🔹 문제 4. /etc/profile을 수정하여, 로그인 시 모든 사용자에게 공지 메시지 /etc/login_notice.txt를 출력하도록 설정하시오.
조건:
출력 방식은 cat, echo 등 자유


시스템 전체 사용자에게 적용


/etc/login_notice.txt는 임의의 내용을 사전에 작성해 둘 것


sudo 권한 필요


#### nano etc/profile 내부 

```shell
sudo cat /etc/login_notice.txt
```

#### 명령어 + 결과
```shell
[root@localhost etc] echo "대상 : 모든사용자 / 모든 사용자에게 공지합니다." > login_notice.txt

[im@localhost ~]$ su - im
Password: 
[sudo] password for im: 
대상 : 모든사용자 / 모든 사용자에게 공지합니다.

```shell


