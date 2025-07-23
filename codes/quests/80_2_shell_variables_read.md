인자와 read를 함께 사용하여 변수 조합 출력

~$ 80_2_shell_variables_read.sh agument_first
 read input : read_first

input values : agument_first read_first



nano 80_2_shell_variables_read.sh 내부 스크립트
```shell
readfirst="$1"

read -p "read input : " rinput

echo "input values : $1 $rinput"
```

결과값
```shell
[im@localhost Downloads]$ source 80_2_shell_variables_read.sh
read input : read_first
input values :  read_first
```
