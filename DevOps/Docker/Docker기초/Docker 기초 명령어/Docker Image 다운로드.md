## Docker Image 다운로드

태그 이름 이용

```bash
docker image pull [이미지 이름:태그 이름]
```

DIGEST값 이용

```bash
docker image pull [이미지 이름@DIGEST]
```

## Docker Image 목록 확인

```bash
docker images
```

![이미지목록](/images/이미지목록1.png)
출처 : 한 권으로 배우는 도커 & 컨테이너

```bash
docker image ls
```

![이미지목록2](/images/이미지목록2.png)
출처 : 한 권으로 배우는 도커 & 컨테이너

- REPOSITORY : 이미지 이름
- TAG : 이미지 태그
- IMAGE ID : 다운로드 후 로컬에서 할당 받은 ID 값 (≠ DIGEST값)
- CREATED : 이미지가 만들어진 시간
- SIZE : 이미지 크기