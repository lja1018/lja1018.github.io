# `Bash Tutorial`

## Unix Shell
* kernel을 둘러싸고있는 껍데기
* 사용자가 제어할 수 있는 명령형 해석기

## 커서이동
* 문장의 맨 처음 / 끝
  * Ctrl + a / Ctrl + e
* 단어 단위 이동
  * Ctrl + 방향키
* 화면 정리
  * Ctrl + l
* 스크롤 중단 및 재개
  * Ctrl + s / Ctrl + q

## 서버 접속 및 종료
* 접속
  * ssh hcon.nhnent.com
  * rlogin -l 아이디 호스트명
* 종료
  * logout / exit
* 조회
  * last

## 기본 명령
* pwd
  * 현재 디렉토리 확인
* id
  * 자신의 로그인 아이디
* uname
  * 현재 접속해있는 서버의 이름/OS 정보를 확인
  * uname
  * uname -a
* 비슷한 명령
  * hostname
* echo
  * 문자열을 출력하는 명령
  * echo "~~~~"
  * echo -n "hello world"; echo "java coffee"
    * new line 제거
* ls
  * 디렉토리와 파일의 목록 출력
  * 윈도우즈 cmd의 dir
  * ls -l
    * 리스트 포맷
  * ls -alF
  * ls /
  * ls /home1/irteam
  * t 옵션 : 시간 내림차순으로 출력
  
## Glob pattern
* Globbing & Wildcard
  * 임의의 길이를 가지는 문자열
    * \*
  * 임의의 한 글자
    * ?
  * 글자 집합
    * [abcw-z]
  * ls *
  * ls .*
  * ls [a-f]*.txt
  * ls *.tx?

## 파일 시스템
* File
  * OS에서 데이터를 디스크와 같은 저장소에 저장해 둘 때의 단위 형태
  * 넓은 의미에서는 일반 파일, 디렉토리와 각종 입출력 장치를 모두 파일로 간주
* Directory
  * 파일을 담아두는 공간(폴더)
  * 디렉토리 안에 디렉토리를 담을 수 있기 때문에 트리 구조로 형상화
* 디렉토리 이동
  * cd /var/log
* 사용자 홈 디렉토리
  * cd ~/.vim
* 특정 사용자의 홈 디렉토리
  * ls ~nemon

## History
* 조회
  * history
* 12번 명령 재실행
  * !12
* 커맨드 prefix로 재실행
  * !find
* 바로 직전 명령 재실행
  * !!
* 바로 직전 명령의 마지막 argument
  * !$
* 직전 명령 편집
  * echo "hello wolrd"
  * ^Hello^java

## 파일을 다루는 기본 명령
* touch
  * 빈 파일 만들기
  * touch 파일
  * touch file1.txt
* 디렉토리 관련 명령
  * mkdir 디렉토리
  * rmdir 디렉토리
    * 비어있는 디렉토리만 삭제
* cp
  * cp test1.txt test2.txt
  * cp -r mkdir1 mkdi2
* mv
  * mv test1.txt test2.txt
  * mv mydir1 mydir2
  * 대상 파일이 이미 존재하는 디렉토리라면? 에러
* rm
  * rm -f test2.txt
    * f : 강제 삭제 옵션
  * rm -rf mydir2
* file
  * 파일의 종류를 판단하는 명령
  * file 파일
  * file /bin/gzip
  * file /etc/rpm/macros.jpackage

## 변수
* 사용자 변수
  * 보통 소문자로 명명
  * x=1
  * x="hello world"
  * x=hello world
* 주의사항
  * = 주위에 공백 없음
* 값을 꺼내쓰기
  * echo x
  * echo $x
  * echo ${x}
    * 추천
  * echo "$x"
* Full Quotation
  * single quote as literal
  * x="java"; echo '$x is noun'
* Partial Quotation
  * double quote as variable substitution
  * x="java"; echo "$x is noun"

## Evaluation
* 명령 실행 결과를 문자열 변수로 대임
  * backquote(`) 또는 $()로 둘러싸기
  * date_str=\`date +"%Y%m%d"\`
    * 권장하지 않음
  * date_str=$(date +"%Y%m%d")
* 명령 문자열을 실행하기
  * eval 명령문자열
  * cmd="ls -alF"
  * eval $cmd
* Arithmetic
  * a=13
  * b=$((a % 3))
  * i=$((2 ** 60))
  * echo $RANDOM

## Type
* read-only
  * declare -r var1=1
  * var1=2
* integer
  * declare -i n=3
  * n="hello"
* array
* function
* 전부 권장 x
  
## 환경 변수
* 환경(environment)
  * 프로세스를 둘러싼 주변 정보
  * env
* exporting
  * sub-shell에서 상속받아 사용할 수 있도록 변수를 공개
  * 사용자 변수를 환경 변수로 전환
  * export나 declare -x로 지정
* var1=2
  * bash
  * echo $var1
  * exit
* export var1=2
  * bash
  * echo $var1
  * exit
* 주요 환경 변수
  * HOME
  * PATH
  * LANG
  * LC_ALL
  * TERM
    * 터미널
  * SHELL
    * 사용중인 로그인 쉘
  * HOSTNAME
  * LOGNAME / USER / USERNAME
  * ID / UID
  * EDITOR / VISUAL
    * 기본 편집기
  * PS1 / PS2
    * 프롬프트
* 개발자에게 유용한 환경 변수
  * SHLVL
    * 쉘 레벨
  * PPID
    * 부모 프로세스의 PID
  * SECONDS
    * 쉘이 시작한지 몇 초
  * FUNCNAME
    * 함수 이름
  * TMOUT
    * 타임아웃(자동 로그아웃)

## File Permission
* 파일의 타입 1글자
* owner / group / others 의 권한 3개씩 (9글자)
  * r : read
  * w : write
  * x : execute
* umask
  * 파일에 부여되는 permission의 초기값에서 제외할 권한 지정
  * umask 0027
  * touch test2.txt
* 소유자 변경하기
  * chown 소유자아이디 파일

## 제어문
* Boolean expression
  * &&, ||, !, -a, -o
  * (( 0 && 1 )) && echo true || echo false
  * (( 0 || 1 )) && echo true || echo false
* Comparison operator
  * interger
    * -eq -ne -ge -ge -lt -le
  * string
    * < <= > >= == = != -`z` -`n`
      * `z`ero length `n`ull?
* File Test
  * -e
    * exist?
  * -s
    * size not zero?
  * -f / -d / -p / -L
    * file, directory, pipe, symlink?
  * -r / -w / -x / -u / -g / -k
    * permission? (set`u`id, set`g`id, stic`k`y)
  * -nt / -ot
    * newer than, older than?
* if
  * if [ `조건` ]; then
    * 실행문
  * fi
  * x=3
  * if [ $x -eq 3 ]; then
    * echo "x is 3"
  * fi
* 주의사항
  * -eq 연산자는 정수 연산자
  * ==, = 연산자는 문자열 연산자
  * 변수가 정의되지 않았거나 공백을 포함할 수 있으므로 quotation 필요
    * x="he llo"
    * if [ "$x" == "he llo" ]; then echo $x; fi
* while
  * while [ `조건` ]; do
    * 실행문
  * done
  * i=3
  * while [ $i -lt 10 ]; do
    * echo $i; i=$((i + 1));
  * done
* 무한루프
  * while :; do
    * date
    * sleep 5
  * done
* for
  * for `변수명` in `리스트`; do
    * 실행문
  * done
  * for dir in *; do
    * [ -d "$dir" ] && (echo
    * "$dir"; cd "$dir"; ls -l |
    * wc -l)
  * done
* switch-case
  * case `변수` in
  * `케이스1`)
    * 실행문;;
  * *)
    * 실행문;;
  * esac
* break
* continue

## 입출력 리다이렉트
* 표준 입력(standard input) - 0번
  * 키보드 입력이 프로세스로 들어가는 통로
* 표준 출력(standard output) - 1번
  * 프로세스가 출력한 내용이 화면으로 나오는 통로
* 표준 에러(standard error) - 2번
  * 프로세스에서 발생한 에러가 화면으로 나오는 통로
* input redirect
  * sort < in.txt
* output redirect
  * ls /lkjfslfjds `>` out.txt
  * ls /lkjfslfjds > out.txt `2>` err.txt
* append
  * ls /lkjfslfjds > allresult.txt 2>&1
  * ls /lkjfslfjds 2>&1 | sort

## 필터
* 프로세스의 출력을 다른 프로세스의 입력으로 전달
  * 파이프(`|`) 기호를 이용
  * ls | head
  * cat test.txt | sort | uniq -c | sort -n
    * uniq : 중복파일 빼고
    * -c : 카운팅
* 특정 단계에서 발생하는 에러도 잡고 싶다면?
  * find /etx | grep

## 파일 내용 보기
* cat
* more
* less
  * grep : RE에 맞춰 해당하는 줄만 출력
* 파일의 앞쪽 일부만 보기
  * head -10 test1.txt
* 파일의 뒤쪽 일부만 보기
  * tail -5 test1.txt
  * tail -f /var/log/lastlog
    * -f : append 계속 탐지(파일의 변화)
* 찾기
    ```bash
    * grep `문자열` `파일`
    * grep "export" /etc/profile
    * grep -r "export" /etc
        * recursive 하게 탐색
    ```
* 잘라내서 쓰기
    ```bash
    cut -d `구분자` -f `필드번호` `파일`
    grep irteamro /etc/passwd | cut -d: -f1,3-4,7
    ```

## Alias
* 별명
    ```bash
    alias
    alias grep="egrep"
    alias diffs="diff -ignore-all-space"
    alias l="ssh hcon.nhnent.com"
    ```
## 함수
* 함수는 원래 리턴값이 있으나 bash에서는 subroutine과 구분이 없어 없기도 함
* function과 subroutine을 구분하지 않음
    ```bash
    func1() { echo "hello, $1"; }
    func1 "world"

    function func2 { return $(($1 + $2)); }
    func2 3 4
    echo $?
    ```
* 변수는 기본적으로 전역
* 함수 내부에서만 사용하려면 local로 지정해야 함
    ```bash
    function test1() {
        local int_val=3
        str_val="value of global variable"
    }
    test1
    echo $int_val
    echo $str_val
    ```

## Script File
* shebang
  * #!
    * 어떤 인터프리터 프로그램을 사용할 것인가를 지정
  * #!/bin/bash
  * #!/usr/bin/env python
    * 권장하는 방식
  * #!/bin/awk -f
    * 옵션을 붙여야 할 경우, env을 사용할 수 없음
* 파일 작성 (test.sh)
    ```bash
    #!/bin/bash
    echo "hello world"
    bash test.sh
    chmod a+x test.sh
    ./test.sh
    ```
* command-line arguments
  * $1, $2, ...
  * $#
* exit status
  * $?
* function의 매개변수와 리턴값도 동일

## Job Control
* Foreground job
  * 기본적으로 프로그램은 foreground에서 실행됨
  * 한 명령의 실행이 끝날 때까지 다음 명령은 기다려야 함
* Background job
  * &을 붙여서 실행하면 background에서 실행됨
  * 다음 명령을 바로 실행하거나 프롬프트가 뜸
    ```bash
    sleep 500 &
    jobs
    fg %1
    Ctrl-z
    bg
    wait #자식 프로세스를 기다림
    ```

## 사용자 설정
* Bourne shell
  * ~/.profile
* BASH
  * login shell
    * .bashrc
    * 로그인 했을 때 동작
    * source ~/.bashrc 로 이미 실행중인 shell에 적용
  * non-login shell
    * .bash_profile

## 추천 설정

## 자주 사용하는 명령
* 파일 경로 다루기
  * 디렉토리 이름 구하기
    * dirname
  * 파일 이름 구하기
    * basename
* 화면 청소하기
  * clear
* 실행 가능한 프로그램 확인
  * which
    * which lsof
    * PATH 환경변수에 포함되어야 탐색 가능
* 로케일 관련 명령
  * locale
    * locale
    * locale -a
  * iconv
    * 파일의 인코딩 변경
    * iconv -c -f CP949 -t UTF-8 `완성형파일 > UTF파일`
      * -c 옵션 필수
    * iconv -l
* 정렬과 카운팅
  * 정렬
    * sort
  * 인접한 행의 중복 제거
    * uniq `파일`
  * 행/열/문자 수 세기
    * wc `파일`
  * 자주 쓰는 조합
    * cut -d: -f7 /etc/passwd | sort -u | wc -l
    * grep -v "^#" /etc/sysctl.conf | cut -d'.' -f1 | sort | uniq -c | sort -n
      * -v : 뒷 패턴을 검색에서 제외
* 파일 탐색
  * find
    * find `디렉토리 목록` -name 이름패턴 -type 파일유형 ...
    * find /usr/lib64
    * find /usr/lib64 -name "lib*.a" -ls
    * find /usr/lib64 -type d -name "py*"
    * find /usr/lib64 \\( -name "python*" -o -name "pqsql*"\\) -ls
* 입력을 개별 처리하기
  * for 반복문은 공백이 포함된 입력을 처리하기 곤란함
  * xargs를 이용하여 행 단위로 처리하기
    * xargs `명령`
    * xargs -I % `명령`"%"
    * find /etc/init | xargs wc-l
    * find /etc/init | xargs -I % wc -l "%"
* 다른 사용자로 변경
  * su
    * 다른 사용자로 변경하기
    * su irteam
    * su -l irteamsu
  * sudo
    * rlogin -l irteamsu 호스트명
    * sudo apps/httpd/bin/apachectl start
* 접속 패스워드 변경하기
  * passwd
  * kpasswd
* 원격 제어
  * rsh -l `로그인ID 호스트명 "명령"`
  * rcp, scp
  * ftp, 
* 파일 묶기
  * 여러 파일을 하나로 묶거나 압축하기
    * tar cvfz mypack.tar.gz src/
      * z : 압축
  * zip 포맷
    * zip -r mypack.zip src/
* 프로세스 관련 명령
  * 프로세스 목록 조회
    * ps aux / pstree
  * 프로세스 종료
    * kill `프로세스ID` / pkill `프로세스명`
  * 프로세스 이름으로 프로세스ID 알아내기
    * pidof `프로세스명`
* 시스템 관련 명령
  * 시스템 자원 사용현황 조회
    * top
  * 디렉토리의 크기 조회
    * du -s
  * 디스크 전체 사용현황 조히ㅗ
    * df -k
* 네트웍 관련 명령
  * ifcofig -> ip addr
  * ping
  * nslookup -> getent hosts
    * getent hosts hangame.com
* 매뉴얼 페이지
  * man wc
  * man 2 open
  * man 3 opendir

## 우리 회사용 특수 명령
* r
  * search / searchall(sa)
  * login / shell
  * status
  * ip
  * copy / copyfrom / copyto
  * alias

## 명령 조합
## Reference