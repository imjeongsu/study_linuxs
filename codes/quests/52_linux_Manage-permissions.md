Linux 권한 관리 실습 문제
실습 환경 설정
먼저 다음 명령어들을 실행하여 실습 환경을 구성하세요:
# 실습 디렉터리 생성(/root 사용)
mkdir permission_practice
cd permission_practice


# 사용자 및 그룹 생성 (관리자 권한 필요)
sudo useradd -m -s /bin/bash alice
sudo useradd -m -s /bin/bash bob
sudo useradd -m -s /bin/bash charlie
sudo useradd -m -s /bin/bash diana
sudo useradd -m -s /bin/bash eve


# 그룹 생성
sudo groupadd developers
sudo groupadd managers


# 사용자를 그룹에 추가
sudo usermod -a -G developers alice
sudo usermod -a -G developers bob
sudo usermod -a -G developers charlie
sudo usermod -a -G managers diana
sudo usermod -a -G managers alice
# eve는 기타 사용자로 어떤 그룹에도 속하지 않음


# 복잡한 디렉터리 구조 생성
mkdir -p {company/{departments/{dev,hr,finance,marketing},projects/{project_a,project_b,project_c}},shared/{documents,resources,tools},private/{alice,bob,charlie,diana,eve},backup/{daily,weekly,monthly},logs/{2023/{01..12},2024/{01..12}}}


# 다양한 파일 생성
touch company/departments/dev/{main.py,test.py,config.py,README.md}
touch company/departments/hr/{employees.xlsx,contracts.pdf,policies.txt}
touch company/departments/finance/{budget.xlsx,reports.pdf,invoices.csv}
touch company/projects/project_a/{spec.doc,code.zip,data.json}
touch company/projects/project_b/{requirements.txt,source.tar.gz,notes.md}
touch shared/documents/{manual.pdf,guidelines.txt,templates.docx}
touch shared/resources/{images.zip,fonts.tar,icons.png}
touch private/alice/{personal.txt,settings.conf,backup.tar}
touch private/bob/{notes.md,config.json,archive.zip}
touch backup/daily/{backup_$(date +%Y%m%d).tar.gz,log_$(date +%Y%m%d).txt}
touch logs/2024/06/{access.log,error.log,debug.log,system.log}


# 실행 가능한 스크립트 파일 생성
echo '#!/bin/bash' > shared/tools/deploy.sh
echo 'echo "Deployment script"' >> shared/tools/deploy.sh
echo '#!/bin/bash' > shared/tools/backup.sh
echo 'echo "Backup script"' >> shared/tools/backup.sh
echo '#!/bin/bash' > company/departments/dev/build.sh
echo 'echo "Build script"' >> company/departments/dev/build.sh


# 설정 파일 생성
echo "database_host=localhost" > company/departments/dev/database.conf
echo "api_key=secret123" > company/departments/dev/api.conf
echo "salary_data=confidential" > company/departments/hr/salaries.txt


echo "실습 환경이 구성되었습니다!"
tree permission_practice


1. 기본 권한 설정
1-1. 개발팀 파일 권한 설정
개발팀(developers 그룹) 관련 파일들의 권한을 다음과 같이 설정하세요:

A. company/departments/dev/ 디렉터리: 개발팀만 접근 가능, 소유자와 그룹은 읽기/쓰기/실행 가능

# 1-1 답안 작성란

```shell
# dev 디렉터리에 user / group을 alice / developers로 변경
[root@localhost departments]# chown -R alice:developers dev
[root@localhost departments]# ls -l
total 0
drwxr-xr-x. 2 alice developers 123 Jul 21 16:49 dev
drwxr-xr-x. 2 root  root        64 Jul 21 16:48 finance
drwxr-xr-x. 2 root  root        89 Jul 21 16:49 hr
drwxr-xr-x. 2 root  root         6 Jul 21 16:48 marketing

# root 디렉터리 접속을 위해 Others x권한 부여
[root@localhost ~]# chmod o+x /root
[root@localhost ~]# ls -l
total 4
-rw-------. 1 root root 818 Jul 16 10:21 anaconda-ks.cfg
drwxr-xr-x. 7 root root  76 Jul 21 16:48 permission_practice

# dev 디렉터리의 소유자인 alice 계정으로 /dev의 절대경로를 통해 접근
[alice@localhost /]$ ls -l /root/permission_practice/company/departments/dev
total 12
-rw-r--r--. 1 alice developers 18 Jul 21 16:49 api.conf
-rw-r--r--. 1 alice developers 32 Jul 21 16:49 build.sh
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 config.py
-rw-r--r--. 1 alice developers 24 Jul 21 16:49 database.conf
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 main.py
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 README.md
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 test.py

# developers Group인 bob 계정으로 /dev의 절대경로를 통해 접근
[bob@localhost /]$ ls -l /root/permission_practice/company/departments/dev
total 12
-rw-r--r--. 1 alice developers 18 Jul 21 16:49 api.conf
-rw-r--r--. 1 alice developers 32 Jul 21 16:49 build.sh
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 config.py
-rw-r--r--. 1 alice developers 24 Jul 21 16:49 database.conf
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 main.py
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 README.md
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 test.py

# developers Group이 아닌 diana 계정으로 /dev의 절대경로를 통해 접근
# root 디렉터리 내부의 접근을 위해 others 접근권한을 가지고 있기에
# /dev 의 접근이 가능함

[diana@localhost /]$ ls -l /root/permission_practice/company/departments/dev
total 12
-rw-r--r--. 1 alice developers 18 Jul 21 16:49 api.conf
-rw-r--r--. 1 alice developers 32 Jul 21 16:49 build.sh
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 config.py
-rw-r--r--. 1 alice developers 24 Jul 21 16:49 database.conf
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 main.py
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 README.md
-rw-r--r--. 1 alice developers  0 Jul 21 16:48 test.py

B. company/departments/dev/main.py: 개발팀은 읽기/쓰기, 기타는 읽기만 가능


# main.py : chmod 664 -> developers group : rw- , other r-- 
[root@localhost dev]# chmod 664 main.py && ls -l main.py
-rw-rw-r--. 1 alice developers 0 Jul 21 16:48 main.py


C. company/departments/dev/build.sh: 개발팀만 실행 가능
명령어를 작성하세요:

# build.sh : chmod 754 -> developers group : r-x , other r-- 
-rw-r--r--. 1 alice developers 32 Jul 21 16:49 build.sh
[root@localhost dev]# chmod 754 build.sh && ls -l build.sh
-rwxr-xr--. 1 alice developers 32 Jul 21 16:49 build.sh
```

1-2. 개인 디렉터리 보안 설정
각 사용자의 개인 디렉터리와 파일을 다음과 같이 설정하세요:
A. private/alice/ 디렉터리: alice만 접근 가능

```shell
[root@localhost private]# ls -l
total 0
drwx------. 2 alice root 65 Jul 21 16:48 alice
drwxr-xr-x. 2 root  root 60 Jul 21 16:48 bob
drwxr-xr-x. 2 root  root  6 Jul 21 16:48 charlie
drwxr-xr-x. 2 root  root  6 Jul 21 16:48 diana
drwxr-xr-x. 2 root  root  6 Jul 21 16:48 eve
```

private/alice/personal.txt: alice만 읽기/쓰기 가능
private/bob/config.json: bob만 읽기/쓰기 가능
명령어를 작성하세요:
# 1-2 답안 작성란







2. 그룹 기반 권한 관리
2-1. 공유 리소스 접근 권한
shared/ 디렉터리의 권한을 다음과 같이 설정하세요:
shared/documents/: developers와 managers 그룹 모두 읽기 가능, 소유자만 쓰기 가능
shared/resources/: developers 그룹만 접근 가능
shared/tools/: 모든 사용자가 읽기 가능, developers 그룹만 실행 가능
명령어를 작성하세요:
# 2-1 답안 작성란





2-2. 프로젝트별 협업 권한
프로젝트 디렉터리의 권한을 다음과 같이 설정하세요:
company/projects/project_a/: developers 그룹 구성원들이 협업할 수 있도록 설정
company/projects/project_b/: alice와 bob만 접근 가능하도록 설정
명령어를 작성하세요:
# 2-2 답안 작성란






3. 고급 권한 설정





3-2. 숫자 표기법으로 복합 권한 설정
다음 파일들의 권한을 숫자 표기법으로 설정하세요:
company/departments/finance/budget.xlsx: 소유자(rw-), 그룹(r--), 기타(---)
shared/documents/manual.pdf: 소유자(rw-), 그룹(r--), 기타(r--)
logs/2024/06/system.log: 소유자(rw-), 그룹(r--), 기타(---)
명령어를 작성하세요:
# 3-2 답안 작성란






4. 소유권 및 그룹 관리
4-1. 소유권 변경
다음과 같이 파일과 디렉터리의 소유권을 변경하세요:
company/departments/dev/ 디렉터리와 모든 하위 파일: alice 소유, developers 그룹
company/departments/hr/ 디렉터리와 모든 하위 파일: diana 소유, managers 그룹
shared/tools/ 디렉터리와 모든 하위 파일: root 소유, developers 그룹
명령어를 작성하세요:
# 4-1 답안 작성란





4-2. 그룹 전용 변경
다음 디렉터리들의 그룹만 변경하세요:
company/projects/: managers 그룹으로 변경
backup/daily/: developers 그룹으로 변경
명령어를 작성하세요:
# 4-2 답안 작성란






5. 실전 시나리오 해결
5-1. 보안 감사 및 수정
다음 보안 문제들을 찾아서 수정하세요:
777 권한으로 설정된 파일이나 디렉터리를 찾아 적절한 권한으로 변경
다른 사용자가 읽을 수 있는 민감한 파일들의 권한 수정
실행 권한이 없어야 할 데이터 파일에서 실행 권한 제거
명령어를 작성하세요:
# 5-1 답안 작성란 (보안 감사 명령어)




# 5-1 답안 작성란 (수정 명령어)






6. umask 및 기본 권한 관리
6-1. umask 설정 및 테스트
현재 시스템의 umask 값을 확인하고 다음과 같이 변경한 후 테스트하세요:
umask 값을 027로 설정
새 파일과 디렉터리를 생성하여 기본 권한 확인
원래 umask 값으로 복원
명령어를 작성하세요:
# 6-1 답안 작성란





6-2. 사용자별 umask 커스터마이징
각 사용자별로 다른 umask 값을 설정하세요:
alice: umask 022 (일반적인 개발자 설정)
diana: umask 077 (보안 강화 설정)
eve: umask 002 (그룹 협업 친화적 설정)
명령어를 작성하세요:
# 6-2 답안 작성란






8. 실행 권한 및 스크립트 관리
8-1. 스크립트 실행 환경 설정
다음 스크립트 파일들의 실행 권한을 적절히 설정하세요:
shared/tools/deploy.sh: developers 그룹만 실행 가능
shared/tools/backup.sh: alice와 diana만 실행 가능 (ACL 사용)
company/departments/dev/build.sh: 소유자만 실행 가능
명령어를 작성하세요:
# 8-1 답안 작성란





8-2. 시스템 스크립트 보안 설정
시스템 관리용 스크립트를 다음과 같이 설정하세요:
root 소유의 시스템 관리 스크립트 생성 (system_check.sh)
일반 사용자가 sudo 없이 실행할 수 있도록 SetUID 설정
실행 로그를 남기도록 권한 설정
명령어를 작성하세요:
# 8-2 답안 작성란






9. 디렉터리별 접근 제어
9-1. 계층적 접근 제어
다음과 같은 계층적 접근 권한을 설정하세요:
company/ : 모든 직원이 읽기 가능
company/departments/ : 각 부서원만 해당 부서 디렉터리 접근 가능
company/departments/finance/ : managers 그룹만 접근 가능
company/projects/ : 프로젝트 참여자만 해당 프로젝트 접근 가능
명령어를 작성하세요:
# 9-1 답안 작성란





9-2. 임시 작업 공간 설정
임시 작업을 위한 공간을 다음과 같이 설정하세요:
temp/ 디렉터리 생성 (모든 사용자가 파일 생성 가능)
Sticky Bit 설정으로 자신의 파일만 삭제 가능
1주일 후 자동 삭제되도록 권한 설정 (cron 작업용)
명령어를 작성하세요:
# 9-2 답안 작성란






10. 백업 및 아카이브 권한 관리
10-1. 백업 파일 보안
백업 관련 파일들의 보안을 다음과 같이 설정하세요:
backup/daily/ : developers 그룹이 백업 생성 가능, 읽기 전용
backup/weekly/ : managers만 접근 가능
backup/monthly/ : root만 접근 가능
모든 백업 파일은 생성 후 읽기 전용으로 자동 변경
명령어를 작성하세요:
# 10-1 답안 작성란







