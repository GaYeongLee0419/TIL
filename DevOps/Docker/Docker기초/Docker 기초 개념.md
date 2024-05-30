## Docker 작동 방식

앞에서 도커를 설치하고 hello world를 실행해 결과를 얻었다. 도커는 어떻게 작동하는 것일까?

### Docker 구조

![도커구조](/images/도커구조.png)

출처 : 한 권으로 배우는 도커 & 쿠버네티스

1. 도커 클라이언트에서 명령어를 입력한다.
2. 도커 호스트의 도커 데몬이 명령을 받는다.
3. 도커 호스트에 이미지가 존재하지 않으면 도커 레지스트리에서 다운로드한다.
- Docker Client
    - 도커에 명령을 내릴 수 있는 CLI 도구
    - 컨테이너, 이미지, 볼륨 등을 관리한다.
- Docker Host
    - 도커를 설치한 서버 혹은 가상머신
- Docker Registry
    - 도커 이미지를 저장하거나 배포하는 시스템
    - 도커 레지스트리는 Public과 Private으로 나눈다. 대표적인 public registry로 Docker Hub가 있다.
    - 도커를 사용하는 사람이라면 누구나 Docker Hub에서 이미지를 다운로드하거나 업로드할 수 있다.

### Docker Image

- 컨테이너 형태로 소프트웨어를 배포하기 위해 필요한 모든 요소를 실행할 수 있는 포맷으로 컴파일 및 빌드한 패키지
- 도커 이미지는 여러 개의 레이어로 구성되어 있으며 도커 허브와 같은 중앙 저장소에 저장되어 관리된다.

<aside>
💡 도커 이미지를 통해 동일한 환경을 가진 여러 개의 컨테이너를 손쉽게 생성할 수 있다.

</aside>

### Docker Container

- 도커 이미지를 실행할 수 있는 인스턴스
- 도커 컨테이너는 도커 이미지로부터 생성된다.
- 컨테이너는 자체적으로 파일 시스템을 가지고 있어 독립적으로 실행된다.

<aside>
💡 컨테이너는 운영체제를 포함하기 때문에 무거울 것이다? **NO
WHY?**
도커 엔진과 운영체제를 공유하기 때문이다.
→ 컨테이너 내부는 프로그램을 실행시키기 위한 최소한으로 필요한 바이너리, 라이브러리와 같은 구성 요소로 이루어져 있다.

</aside>

### hello world 실행 과정

1. **docker run hello-world**

   hello-world라는 컨테이너를 실행시킨다.

2. **Unable to rind image ‘hello-world:lates’ locally**

   나는 이전에 이미지를 다운받은 적이 없기 때문에 당연히 로컬에서 ‘hello-world:lates’라는 이미지를 찾을 수 없다.

3. **latest: Pulling from library/hello-world**

   도커 허브에 있는 library/hello-world에서 이미지를 pull 받아온다.

4. **Digest : ~**

   식별값으로 Digest라는 해시 함수를 거쳐 해시값을 갖는다.