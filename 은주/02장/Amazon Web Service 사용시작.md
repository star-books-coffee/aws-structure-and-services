## Chapter 2. Amazon Web Service 사용시작
### 루트 사용자 vs. IAM 사용자

- 루트 사용자
    - 모든 권한을 가진 사용자
    - IAM 에서 부여할 수 있는 모든 궈리 외에, AWS 계정 자체의 구성 변경, 계약 해지 및 변경 등 `무엇이든 할 수 있는` 사용자
- IAM 사용자
    - **루트사용자로부터 적절한 권한을 부여받아** 서비스를 사용하는 사람
- 루트 사용자 계정은 AWS 계정 전체의 설정 변경과 같이 **반드시 루트 사용자로 해야 하는 작업 외에는 사용하지 않는게 좋다**

ex) 팀에서 하나의 계정을 공유해야 할 경우, 루트 계정의 id/pw 를 공유하는 것이 아니라 아래와 같이 루트 사용자가 IAM 사용자들에게 권한을 준다
<br>
![](https://file.notion.so/f/f/3db2c1d3-d28f-483a-adc8-ee8abc696878/29b421b0-a8e0-4671-ab6d-f39ef03d6ccb/Untitled.png?id=20ab57e9-a93f-4956-bfec-51bbcf9cc211&table=block&spaceId=3db2c1d3-d28f-483a-adc8-ee8abc696878&expirationTimestamp=1695477600000&signature=ziVIIYAa1XtU_XdliRhMhAHpohsKU0o1YJyuUoG_t10&downloadName=Untitled.png)

### AWS 서비스를 사용하는 방법

1. 웹 브라우저에서 `관리콘솔`로 조작
2. AWS CLI 를 설치하여 조작
    
    ```bash
    aws ec2 create-security-group —group-name sample-sg —description “sample sg”
    ```
    
    - AWS CLI 는 웹 브라우저보다 난이도가 있어보이지만, **같은 명령 실행 시 언제나 같은 결과를 얻을 수 있는** `재현성`이 높다는 장점이 있다
    - 콘솔 사용 시, UI 변경이나 잘못된 순서로 조작하는 경우에 의한 실수를 방지할 수 있다
    - AWS CLI 명령어를 사용하면, **자주 사용하는 명령어 저장해두고 바로 사용할 수 있어** 조작 실수를 줄일 수 있음
3. 개발 언어에 `AWS SDK` 를 설치하여 조작
    - SDK 는 AWS 자원 조작은 물론, 응용 프로그램의 일불 AWS 자원을 조합하는 기능도 가능하다
    
    ```jsx
    const AWS = require('aws-sdk');
    const dotenv = require('dotenv');
    dotenv.config();
    
    // aws region 및 자격증명 설정
    AWS.config.update({
       accessKeyId: process.env.S3_ACCESS_KEY_ID,
       secretAccessKey: process.env.S3_SECRET_ACCESS_KEY,
       region: 'ap-northeast-2',
    });
    ```
    
### AWS 서비스 이용료 시각화

- `종량 과금제` : 이용한만큼 매월 이용료가 청구된다.
- `Cost Explorer` : aws 서비스별 비용을 파악하는데 도움이 된다
- `Budgets` : 예산 설정하여, 월 이용 요금이 설정 금액을 초과했을 경우 알림을 보냄

### AWS 시스템이 구축되는 위치 : 리전

- `리전` 은 전 세계 각지에 지리적으로 떨어진 영역이며, AWS의 **사설 네트워크로 연결되어 있음**
- 세계 각지에 리전이 존재함으로써 얻게 되는 장점
    - 글로벌 시스템 구축 가능 → 통신 지연 줄임
    - 법적 요구사항으로, 특정 국가에 시스템을 구축해야 하는 경우 요건 충족 가능
    - 특정 리전에 재난이 발생해도, 다른 리전에서 시스템 가동 가능
- 즉, **리전별로 분리해 자원을 관리**할 수 있음

### AZ 는 리전 내의 독립적인 위치

- 리전 == 복수 개의 `가용 영역 (AZ)`
- AZ == 하나 이상의 `데이터센터`
- 모든 AZ는 **독립적**이며, 다른 AZ에 장애가 발생해도 영향을 받지 않으며, AZ 끼리는 **고속 네트워크로 연결**돼 있고 **암호화된 통신**을 이용함
- AZ 이름 : 지역 이름 + 알파벳   ex) ap-northeast-2a
- AZ ID          ex) apne-az1
    - AZ 이름과 AZ ID 는 일대일 대응하지만, **AWS 계정마다 AZ 이름에 대응하는 AZ ID는 다르다**
    - **AZ ID 가 동일하면, 같은 위치의 AZ 이므로 장애 발생시 ID 를 확인하면 된다.**
- 기본적으로 여러 AZ 에서 실행하도록 AWS 자원을 생성하는 경우가 많음
