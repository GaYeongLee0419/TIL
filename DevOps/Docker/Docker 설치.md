## 사전 준비 사항

### 1. 통신 환경 설정

도커를 설치하기 위해 필요한 도커 리포지토리와 통신할 수 있는 환경을 설정한다.

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
```

- apt-get 패키지 인덱스를 업데이트한다.
- apt가 HTTP에서 리포지토리를 사용할 수 있게 하는 데 필요한 패키지를 설치한다.
    - ca-certificates : 인증서 관련 패키지
    - curl : 파일을 다운로드하기 위한 패키지
    - gnupg : 디지털 서명을 사용하기 위한 패키지
    - lsb-realease : 리눅스 배포판 식별을 위해 필요한 패키지


### 2. GPG키 추가

GPG ; GNU Privacy Guard

도커 이미지 인증을 확인할 때 사용하는 키이다.

```bash
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

### 3. 리포지토리 설정

Docker 패키지를 설치하기 위해 Docker의 공식 저장소 URL을 시스템의 패키지 소스 목록에 추가한다.

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Docker 설치

### 1. apt 패키지 업데이트

패키지의 최신 버전을 다운로드 받기 위해 업데이트한다.

```bash
sudo apt-get update
```

### 2. Docker 설치

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

- docker-ce
    - **설명**: Docker의 커뮤니티 에디션으로, 컨테이너화된 애플리케이션을 개발하고 배포할 수 있게 해준다. 이는 Docker의 핵심 패키지로, Docker 데몬과 CLI를 포함한다.
    - **기능**: 컨테이너 이미지 생성, 관리, 배포 및 실행 기능을 제공합니다. Docker 데몬은 컨테이너의 생성 및 관리를 담당하며, CLI는 사용자가 Docker와 상호 작용할 수 있게 해준다.
- docker-cli
    - **설명**: Docker 커뮤니티 에디션의 명령줄 인터페이스 도구이다.
    - **기능**: 사용자가 Docker 데몬과 상호 작용할 수 있게 해주는 명령어 도구를 제공한다. 이는 컨테이너와 이미지를 빌드, 실행, 관리할 수 있는 다양한 명령어를 포함한다. `docker run`, `docker build`, `docker images`, `docker ps` 등의 명령어를 사용할 수 있게 해준다.
- comtainerd.io
    - **설명**: Docker가 컨테이너를 실행하는 데 사용하는 컨테이너 런타임이다. 이는 독립적으로도 사용될 수 있으며, Kubernetes와 같은 오케스트레이션 도구에서 널리 사용된다.
    - **기능**: 컨테이너의 수명 주기를 관리하는 데 필요한 기본적인 기능을 제공한다. 이미지 전송, 컨테이너 실행, 저장소 및 네트워크 관리 기능을 포함한다.
- docker-buildx-plugin
    - **설명**: Docker의 `buildx` 확장 기능으로, Docker 이미지 빌드를 더 강력하게 해준다. 기본 빌드 도구보다 더 많은 기능을 제공한다.
    - **기능**: 멀티 플랫폼 빌드, 캐시 관리, 원격 빌드 기능을 포함한다. 이를 통해 다양한 아키텍처용 이미지를 한 번에 빌드할 수 있다.
- docker-compose-plugin
    - **설명**: Docker Compose는 다중 컨테이너 Docker 애플리케이션을 정의하고 실행하기 위한 도구이다. 이 플러그인은 Docker CLI와 통합되어 Compose 파일을 사용할 수 있게 해준다.
    - **기능**: YAML 파일을 사용하여 애플리케이션의 서비스, 네트워크, 볼륨을 정의할 수 있다. 이를 통해 여러 컨테이너로 구성된 애플리케이션을 쉽게 관리하고 배포할 수 있다. `docker-compose up`, `docker-compose down` 등의 명령어를 사용한다.

### 3. 설치 확인

```bash
docker
```

![도커설치확인](/images/도커설치확인.png)

```bash
systemctl status docker
```

systemctl status : 서비스의 상태 확인

도커가 작동되고 있는지 확인한다.
![도커작동확인](/images/도커작동확인.png)

### 4. 도커 명령어를 사용자 모드에서 사용할 수 있게 설정

```bash
sudo usermod -aG docker $USER
```

docker 그룹에 현재 사용자($USER = gayeong)을 추가한다.

사용자 모드에서 사용할 수 있는지 확인하기 위해 로그아웃 후 다시 로그인 하여 도커 버전을 확인한다.

```bash
docker version
```

![도커버전확인](/images/도커버전확인.png)

sudo 명령어 없이도 실행되므로 사용자 모드에서도 사용 가능한 것을 확인할 수 있다.

## 테스트

```bash
docker run hello-world
```

![테스트](/images/테스트.png)