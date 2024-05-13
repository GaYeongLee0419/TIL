### IAM이란?
- AWS 리소스에 대한 액세스를 안전하게 제어할 수 있는 웹 서비스
- IAM을 사용하면 사용자가 액세스할 수 있는 AWS 리소스를 제어하는 권한을 중앙에서 관리할 수 있음
- 리전에 상관없이 사용가능한 글로벌 서비스


### Policy Structure
![policy structure](/images/policy.png)
- Version : 정책 언어 버전
- Id : 정책 식별자(선택사항)
- Statement : 하나 이상의 개별 문장으로 구성
- Sid : 문장 식별자(선택사항)
- Effect : 문장이 액세스를 허용하거나 거부하는지 여부를 나타냄
- Principal : 이 정책이 적용되는 계정, 사용자, 역할을 나타냄
- Action : 이 정책이 허용하거나 거부하는 작업 목록
- Resource : 작업이 허용되는 리소스 목록
- Condition : 이 정책이 적용되는 조건(선택사항)
### MFA; Multi Factor Authentication
- password + security device
![mfa device](/images/mfa device.png)



### AWS에 액세스하기 위해 사용하는 세 가지 옵션
- AWS Management Console (Password + MFA)
- AWS CLI ; Command Line Interface (Access Key)
  - Command Line Shell에서 명령어를 사용하여 AWS 서비스와 공용 API로 직접 액세스가 가능
  자원을 관리하기 위해 스크립트를 개발할 수 있음
- AWS SDK ; Software Development Kit (Access Key)
  - 프로그래밍 언어에 따라 개별적인 SDK 존재
  - 코드로 작성하는 것이기 때문에 애플리케이션 내에 내장되어 있음 
### AWS  CLI를 이용한 AWS 서비스 이용하기
  1. 액세스 키 발급
  2. cmd창 들어가기
  3. aws configure 명령어를 이용해 구성하기
     - aws configure 
     - Access Key ID 입력
     - Secret Access Key 입력
     - default region name 입력
     - default output format 입력
     - aws iam list-users
     - 순서대로 명령어를 입력하면 IAM에서 생성된 유저 정보들을 확인할 수 있음
  4. admin 그룹 관리자에서 사용자를 삭제했을 경우 -> Access Denied 
### AWS CloudShell
- AWS 클라우드 웹사이트에서 무료로 사용 가능한 터미널과 같은 개념
- CLI는 어떤 리전이든 가능
- CloudShell은 현재 이용 중인 리전만 나옴

### IAM Role
- IAM Security Tools
- IAM Credentials Report (account-level) IAM 자격 증명 보고서
- IAM Access Advisor (user-level) IAM 접근 관리
### IAM Guidelines & Best Practices
- 루트 계정은 AWS 계정을 설정할 때를 제외하고 사용하지 마라
- 1명 당 1개의 계정
- 사용자를 그룹에 넣어 해당 그룹에 권한을 부여하라
- 비밀 번호 정책을 생성하라
- MFA를 사용하라
- CLI & SDK를 사용할 때 액세스 키를 만들어라
- 계정 권한 검사는 IAM 자격 증명 보고서와 IAM 액세스 분석기를 사용하라