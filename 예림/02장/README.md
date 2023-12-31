# Chapter 2. Amazon Web Service 사용 시작
## 📌 계정을 만들고 AWS 이용 시작

- 루트 사용자는 모든 권한을 가진 사용자
    - AWS 계정 자체의 구성 변경, 계약 해지, 계약 변경 등 ‘무엇이든 할 수 있는’ 가장 큰 권한을 가진 사용자 → 보안 조심
- IAM 사용자 : 별도로 적절한 권한을 부여
    - 기본적으로 처음 로그인했을 때 IAM 계정을 생성한 뒤 IAM 계정만 사용하기를 추천
- 루트 사용자는 AWS 계정 전체에 관련된 설정 변경과 같이 반드시 루트 사용자로 해야하는 작업을 할 때 외에는 사용하지 않는 게 좋다.

## 📌 AWS 서비스를 사용하는 세 가지 방법

### 1. 웹 브라우저로 조작

가장 일반적인 방법은 `관리콘솔`을 이용하여 마우스와 같은 장치로 조작하는 것이다.

### 2. 명령줄 도구로 조작

명령줄 도구는 **AWS Command Line Interface(AWS CLI - 명령줄 도구)**를 설치해야 한다.

- AWS CLI는 브라우저에서 작업하는 것보다는 어려워 보이지만, 같은 명령을 실행했을 때 언제나 같은 결과를 얻을 수 있다.
- 즉, 재현성이 높다는 장점이 있다.

### 3. 프로그램 방식으로 조작

프로그래밍 방식으로 AWS를 이용하기 위해선 AWS SDK라는 개발 키트를 설치해야 한다.

- SDK는 Python, Java, Ruby 등 8가지 개발 언어를 지원한다.
- 그 외에도 React, Angular, IoT용 기기도 제공한다.

## 📌 AWS 서비스 이용료 시각화

### AWS Billing and Cost Management

청구 및 비용 관리를 위한 몇 가지 기능 제공 & 서비스 이용 및 비용 정보 시각화 

> 결제 대시보드 들어가면 나옴.
> 
- 청구정보나 이용현황보고서는 ‘`결제(Billing)’`에서 확인 가능
    - 청구서 : 청구 정보 CSV 파일로 다운로드 가능
    - Cost & usage reports : 계정의 청구정보와 이용량을 보고서로 작성 가능
- 비용상황은 ‘`Cost Management`’ 기능으로 확인하고 관리할 수 있다.
    - Cost explorer : 서비스 비용 및 자원을 그래프로 시각화해 분석 및 예측 가능
    - Budgets : 설정 예산별 상황 확인과 관리 가능 & 설정한 예산이 넘으면 경고 알림🚨을 실시

### 비용 관리 정책

비용 관리를 하는 데 있어 알아둘 것 2가지

- Cost explorer에서 올바르게 현황을 파악하고 방침을 수립할 것
- Budgets에서 예산을 설정하고 이용량을 감시할 것

Cost explorer에서는 서비스별 비용 상황을 파악할 수 있다 → 비용 최적화 실시 가능

Budgets에서 예산을 설정하면 월 이용 요금이 설정한 금액을 초과할 때 이를 감지하고 사용자에게 알림을 보냄.

## 📌 AWS 시스템이 구축되는 위치 선택

### 리전은 세계에 존재하는 지역

AWS에서는 전 세계 각 지역에 리전이라고 하는 지리적으로 떨어진 영역이 존재하고 각 리전은 AWS의 사설 네트워크로 연결돼 있다.

- 한국에는 서울 리전 ‘ap-northest-2’가 있다.
- 일본에는 도쿄와 오사카에 ‘ap-northeast-1’, ‘ap-northeast-3’이라는 리전이 존재
- 미국 연방정부, 주, 각 지방자치단체, 계약업체가 사용할 수 있는 특별한 리전도 있음.

세계 각지에 리전이 존재하면 다음과 같은 장점이 있다.

- 세계 각지의 사용자가 이용하는 글로벌 시스템 구축 가능
- 법적 요구 사항으로 특정 국가에 시스템을 구축해야 하는 경우 특정 리전을 사용하여 요건 충족 가능
- 큰 재난이 발생해 특정 리전에서 시스템 사용불가해도 다른 리전에서 시스템 가동 가능

### 가용성 영역은 리전 내의 독립적인 위치

가용 영역(이후 AZ)는 하나 이상의 데이터 센터로 구성되며 모두 독립적이다.

- AZ마다 전력원 & 네트워크 같은 설비도 독립적으로 작동 → 특정 AZ에서 발생한 장애는 다른 AZ에 영향을 미치지 않음.
- 각 AZ는 독립적이지만 AZ끼리는 고속의 네트워크로 연결돼 있고 암호화된 통신을 이용

AZ에는 AZ 이름과 AZ ID가 있음.

- AZ 이름 : ‘지역 이름+알파벳’
    - ap-northest-2a와 같은
- AZ ID : 일대일로 대응하지만, **AWS 계정마다 AZ 이름에 대응하는 AZ ID가 다름.**
    - ‘apne2-az1’
    - AWS 자원이 AZ에 분산되게 하기 위해서
    - 어딘가에 장애가 발생하면 AZ 이름이 아닌 AZ ID를 확인해야 함.

- AWS는 여러 AZ에 자원을 배치해 시스템 가용성을 높일 수 있으므로 사용자가 여러 AZ를 지정해 자원을 생성하는 경우가 많다.
    - S3는 자동으로 3개 이상의 AZ에 데이터가 복사됨.
