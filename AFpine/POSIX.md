# POSIX basics

---

# [**[A guide to POSIX](https://www.baeldung.com/linux/posix)**]

---

## What is POSIX?

- POSIX는 Portable Operating System Interface의 약자
- 운영 체제 간의 호환성을 유지하기 위해 IEEE에서 지정한 표준 제품군
- POSIX 표준을 준수하는 software는 POSIX 표준을 준수하는 OS와 호환되어야 한다
    - ps 명령어를 사용하면 OpenBSD, Debian, macOS 등에서 거의 동일하게 작동한다

## POSIX Defined Standards

### The C API

- POSIX는 C언어로 표준을 정의한다
- 그러므로 프로그램은 source code level에서 다른 OS로 이식 가능

### General Concepts

- 프로그램 작성 규칙을 추가했다
    - 포인터 타입 initialization
    - concurrent executions
    - memory synchronization

### File Formats

- POSIX는 파일, 표준 입출력, 표준 오류에서 사용하는 형식 문자열에 대한 규칙을 정의한다
- 형식에는 [일반 문자, escape sequence characters, conversion specifications]이 있다

```c
printf("Hello, my name is %s.\n", name);
```

### Environment Variables

- 환경 변수는 로그인 성공 시 로그인 쉘이 처리하는 환경 파일에서 정의할 수 있는 변수
- 변수 이름은 [대문자와 밑줄]로만 이루어져야 한다
- 변수값은 [portable character set](https://en.wikipedia.org/wiki/Portable_character_set)으로 이루어진 문자열이어야 한다
- 환경 변수의 이름을 지정할 수 있다
    - 하지만 [standard utilities의 환경변수](https://www.linuxtopia.org/online_books/introduction_to_linux/linux_Reserved_variables.html)와는 겹치지 말아라
- reserved 환경 변수를 존중하자
    - COLUMN
    - HOME
    - LOGNAME
    - LINES
    - PATH
    - PWD
    - SHELL
    - TERM

### Locale

- 사용자 환경에서 사용되는 언어 및 문화적 규칙을 정의한다
- locale에 대한 환경 변수
    - LC_TYPE : 문자 분류
    - LC_COLLATE : 문자 순서
    - LC_MONETARY : 통화 형식
    - LC_NUMERIC : 숫자 형식
    - LC_TIME : 날짜 및 시간 형식
    - LC_MESSAGES : 정보 메세지 및 로그와 같은 프로그램 메세지

### Character Set

- 컴퓨터는 binary만 이해한다
- 그러므로 컴퓨터가 이해할 수 있는 문자 집합을 정의했다
- POSIX는 구현에 최소 하나 이상의 character set과 [portable character set](https://en.wikipedia.org/wiki/Portable_character_set)을 포함하는 것을 권장한다
- character set의 처음 8개 항목은 [control characters](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap06.html)이다

### Regular Expressions

- RE는 text를 찾기 위한 pattern을 정의하는 문자열이다
- standard C library는 RE가 구현되어 있고 awk, sed, grep같은 프로그램의 백엔드에서 작동한다

### Directory Structure

- 대부분의 주요 Linux 배포판들은 FHS를 준수한다
    - FHS : 구성 가능한 트리형 디렉토리 구조를 정의
- 계층의 첫 디렉토리는 root 디렉토리다
    - root : /
- root와 /dev 밑에 디렉토리를 만들면 안된다

### Utilities

- 대부분의 유틸리티가 동일하게 동작한다
- POSIX는 유틸리티 프로그램을 구현하는 방법에 대한 규칙을 정의한다
    - u_name : 유틸리티의 이름
    - [ ] 안의 항목은 optional
    - -a, -b : 프로그램 기능을 활성화/비활성화
    - -c : 사이에 공백 문자가 있는 인수를 예상한다
    - -d, -e : 두 옵션이 상호 배타적
    - -f : 옵션과 option-argument가 공백문자로 구분되면 안된다. argument가 없는 option은 다음 argument를 option argument로 취급하지 않는다
    - operand : 유틸리티가 처리하는 모든 것이 될 수 있다
    - … : 0개 이상의 operand를 입력할 수 있다
    - < > 안의 항목은 실제 값으로 대체해야 한다

```c
u_name [-a][-b][-c option_argument][-d|-e][-f[option_argument]][operand...] <parameter name>
```

## Operating Systems and POSIX Compliancy

### Linux

- POSIX와 완전히 호환되는 Linux 기반 OS를 만드는 것은 가능
- 하지만 대부분의 최신 프로그램은 부분적으로 준수하거나 그러지도 않는다
- 따라서 대부분의 Linux 배포판은 부분적으로 POSIX와 호환된다

### Darwin

- macOS, iOS 같은 Apple OS의 핵심 세트
- 부분적으로 POSIX와 호환된다

### Windows NT

- 전체 디자인이 UNIX 계열 OS와 완전히 다르므로 표준을 전혀 따르지 않는다
- WSL 호환 계층을 사용하여 POSIX 호환 환경을 설정할 수 있다
