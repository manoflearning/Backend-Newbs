# Terminal usage

---

# [**[Command line crash course](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Understanding_client-side_tools/Command_line)**]

---

## Basic built-in terminal commands

### Navigation on the command line

- 특정 directory로 이동하기 위한 명령
- 경로에 선행 슬래시(/)를 포함하면 절대 경로가 된다
    - 반대로 포함하지 않으면 상대 경로
    - ‘/’는 파일 시스템의 root를 나타낸다
    - ~ /home
    - . 현재위치
    - .. 현재의 부모의 위치

```html
cd Desktop
cd ..
cd /Desktop/project/src
cd ./Desktop
cd ~/abc
```

### Listing directory contents

- 특정 directory의 내용을 나열
- 절대 경로나 상대 경로를 설정하여 사용할 수 있다

```html
ls 
ls /Desktop/project/src
ls ~/abs -a
ls -al
```

### Creating, copying, moving, removing

- mkdir - 현재 directory에 새로운 directory 생성
    - mkdir my-awesome-website
- rmdir - 비어있는 directory를 삭제
    - 비어있지 않은 directory를 강제로 삭제하려면 -r 옵션 사용
    - rm (-r) my-awesome-website
- touch - 현재 directory에 비어있는 파일 하나 생성
    - touch abc.c
- mv - 파일을 첫 번째 위치에서 두 번째 위치로 이동시킨다
    - mv abc.c efg.cpp
    - 기술적으로는 파일이 이동한 것이지만, 파일의 이름을 변경하는데 사용된다
- cp - 첫 번째 위치의 파일의 복사본을 두 번째 위치에 생성
    - cp abc.c copied_abc.c
- rm - 파일 삭제
    - 영구적인 삭제이며, 휴지통 같은거 없다

## Connection commands together with pipes

- “|” (pipe) symbol을 사용하여 command들을 묶을 수 있다
- ls | wc -l
    - ls : 현재 directory 안의 파일의 이름들을 나열
    - wc -l :  input으로 들어온 어떤 것의 line 수를 센다
    - 즉 위의 예시는 현재 directory 안의 파일들의 갯수를 출력한다
- command들의 입출력 스트림을 제어하여 구현한다

# [**[50+ Linux Commands You Must Know](https://www.digitalocean.com/community/tutorials/linux-commands)**]
