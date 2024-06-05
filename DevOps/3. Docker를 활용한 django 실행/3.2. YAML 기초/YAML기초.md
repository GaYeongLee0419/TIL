# YAML의 개념

- 마크업 언어가 아니다.
- 도커 컴포즈와 쿠버네티스를 사용할 때 YAML 파일을 활용한다.
- 파일 확장자 : .yaml, .yml

# pyyaml 설치

pyyaml : 파이썬에서 YAML 파일을 다룰 수 있게 도와주는 라이브러리

파이썬 가상 환경을 실행하고 pyyaml 라이브러리를 설치한다.

```bash
gayeong@myserver01:~$ pyenv activate py3_11_6
(py3_11_6) gayeong@myserver01:~$ pip install pyyaml
```

설치가 잘 되었는지 확인한다.

```bash
(py3_11_6) gayeong@myserver01:~$ python
Python 3.11.6 (main, May 29 2024, 05:57:42) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import yaml
>>> quit()
(py3_11_6) gayeong@myserver01:~$ source deactivate
pyenv-virtualenv: deactivate 3.11.6/envs/py3_11_6
```

# YAML 문법

실습 디렉터리를 생성하고 이동한다.

```bash
gayeong@myserver01:~/work$ mkdir ch05
gayeong@myserver01:~/work$ cd ch05
gayeong@myserver01:~/work/ch05$ mkdir ex01
gayeong@myserver01:~/work/ch05$ cd ex01
gayeong@myserver01:~/work/ch05/ex01$
```

## YAML 파일 생성

- {key: value} 구조를 사용한다.

```bash
gayeong@myserver01:~/work/ch05/ex01$ vim yaml_practice.yml

apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    -name: nginx
     image: nginx:latest
    -name: ubuntu
     image: ubuntu:latest
```

- 가상 환경을 실행하고 pyyaml 라이브러리를 불러온다.
- yaml 라이브러리의 load 함수를 이용해 데이터를 로드하고 data를 확인한다.

```bash
gayeong@myserver01:~/work/ch05/ex01$ pyenv activate py3_11_6
(py3_11_6) gayeong@myserver01:~/work/ch05/ex01$ python
iPython 3.11.6 (main, May 29 2024, 05:57:42) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>import yaml
>>> raw = open("/home/gayeong/work/ch05/ex01/yaml_practice.yml", "r+")
>>> data = yaml.load(raw, Loader=yaml.SafeLoader)
>>> data
{'apiVersion': 'v1', 'kind': 'Pod', 'metadata': {'name': 'nginx'}, 'spec': {'containers': [{'name': 'nginx', 'image': 'nginx:latest'}, {'name': 'ubuntu', 'image': 'ubuntu:latest'}]}}
```