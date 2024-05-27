## 실행 과정

1. 클라이언트에서 **docker container run [이미지명]** 입력한다.
2. 도커 호스트의 데몬이 실행 명령을 요청받고 도커 호스트에 있는 이미지를 컨테이너 형태로 실행한다.

## 이미지를 컨테이너로 실행하기

이미지는 미리 pull 받아놓음

```bash
docker container run ubuntu
docker container run python:3.11.6
```

## 도커 컨테이너 목록 확인

```bash
 docker container ls
```

아무런 컨테이너가 출력이 되지 않는다.

![도커컨테이너목록확인1](/images/도커컨테이너목록확인1.png)

python, ubuntu는 실행 중인 컨테이너가 아니기 때문에 목록에서 확인할 수 없는 것이다.

```bash
docker container ls -a
```

-a 옵션을 주면 실행 중인 컨테이너와 정지 상태인 컨테이너 모두 확인할 수 있다.

![도커컨테이너목록확인2](/images/도커컨테이너목록확인2.png)

## 컨테이너 내부 접속

```bash
docker container run -it [이미지명]
또는
docker container attach [컨테이너ID]
```

- -it
    - i : interactive의 줄임말로 표준 입력을 열어놓는다는 의미
    - t : tty의 줄임말로 가상 터미널을 의미
- ubuntu 컨테이너 내부에 접속한 화면

![컨테이너내부접속1](/images/컨테이너내부접속1.png)

### 새로운 터미널 열어서 컨테이너를 실행

터미널1

```bash
docker container run -it ubuntu bash
```

![컨테이너내부접속2](/images/컨테이너내부접속2.png)
터미널2

![컨테이너내부접속3](/images/컨테이너내부접속2.png)

터미널1에서 컨테이너를 실행하니 터미널2에서 실행 중인 컨테이너 목록에서 확인할 수 있었다.

## **컨테이너 종료하기**

```bash
docker container stop [컨테이너ID]
또는
exit
```

## 컨테이너 삭제하기

```bash
docker container rm [컨테이너ID]
```

def342a5058c 컨테이너가 삭제된 것을 확인할 수 있다.

![컨테이너삭제하기](/images/컨테이너삭제하기.png)

## 이미지 삭제하기

```bash
docker image rm [이미지 이름]
```

## 도커 이미지 변경하기

### 터미널 1

- 이미지 목록 확인

```bash
docker images
```

- 컨테이너 실행

```bash
docker container run -it ubuntu
```

- 컨테이너 IP를 확인하기 위해 net-tools 설치

```bash
apt update && apt install net-tools
```

- 컨테이너 IP 확인

```bash
ifconfig
```

### 터미널2

ubuntu 컨테이너에 net-tools를 설치한 컨테이너를 my-ubuntu라는 새로운 이름의 이미지로 저장하고 0.1이라는 태그를 붙이자.

- 실행 중인 컨테이너의 ID 확인

```bash
docker container ls
```

- 새로운 이미지 생성 (새로운 이미지명은 my-ubuntu:0.1)

```bash
docker container commit [컨테이너ID] [새로운 이미지명]
```

### 터미널 1로 이동

기존 컨테이너를 종료한 후 새로 만든 이미지를 컨테이너로 실행한다.

- 기존 컨테이너 종료

```bash
exit
```

- 기존 우분투 컨테이너 삭제

```bash
docker container rm [컨테이너ID]
```

- 새로 만든 이미지를 컨테이너로 실행

```bash
docker container run -it [이미지명]
```

![도커이미지변경하기](/images/도커이미지변경하기.png)

이전에 실행한 우분투에서는 net-tools을 설치해야 했지만 my-ubuntu 이미지를 이용해 생성한 컨테이너는 ifconfig 명령어를 사용할 수 있다.