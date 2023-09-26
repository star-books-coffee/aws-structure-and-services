# Chapter 3. 컴퓨팅 서비스
## 대표적인 서버 유형

- **웹 서버**
    - 웹사이트를 구성하는데 필요한 데이터 저장 및 시스템 제어
    - **EC2, ECS 로 구현**하는 경우가 많음
- **데이터베이스 서버**
    - 데이터베이스 관리 시스템이 설치된 서버
    - EC2 에 DBMS 설치해서 DB 서버 구축해도 되지만, **RDS 나 DynamoDB** 이용할수도 있음
- **메일 서버**
    - SMTP 프로토콜, POP3 프로토콜을 이용해 메일 송신/전달/수신하는 서버
        - `SMTP` (Simple Mail Transfer Protocol) : 이메일 전송 시 사용
        - `POP3` (Post Office Protocol 3) : 이메일 수신 시 사용
    - 메일 전송 과정
        1. 메일전송자는 메일 클라이언트 프로그램에서 메일 작성 후, **SMTP 서버에 메일 전송 요청**
        2. SMTP 서버는 요청을 받아, **해당 메일 수신처를 DNS 서버에서 확인** (어디로 메일 보내야할 지 특정)
        3. 해당 메일 주소로 메일 전송
    - EC2 에 메일 서버 구축 가능, **Amazon SES** 이용 가능

## 웹 서버 작동 방식

- 웹 서버는 클라이언트를 `웹 브라우저` , 서버를 `웹 서버` 로 지정해 클라이언트-서버 통신을 함

## 서버 OS 란

- OS : 기기의 관리/제어를 수행하기 위한 인터페이스, 하드웨어 관리 기능, 기기에서 동작할 SW가 공통으로 이용할 기본 기능을 구현한 소프트웨어
- 리눅스
    - Red Hat Enterprise Linux (RHEL)
    - `CentOS` : **RHEL 의 복제 OS**로, RHEL 상용부분 제거한 리눅스 배포판
    - `Debian GNU/Linux` : Debian 프로젝트에서 개발한 리눅스 배포판
    - `Ubuntu Linux` : **Debian 기반**으로 만들어진 리눅스 배포판
- 윈도우 서버
    - 마이크로소프트에서 출시한 서버용 OS
    - GUI 로 조작하며, 데스크톱 윈도우와 사용법이 비슷

## 서버 가상화

- 일반적으로 <1대의 기기 - 1개의 OS> 지만, 가상화 SW를 사용하면 <1대의 기기 - n개의 OS> 가 가능하다
→ 서버의 가상화
- 물리서버 == 단독주택이어서 1 가족만 살 수 있음
가상서버 == 아파트여서 n 가족 살 수 있음
- `서버 가상화` : 하드웨어를 **나눠서 독립된 가상서버**를 만드는 것
    - 하드웨어 자원에 따라 얼마나 많은 서버를 만들지 결정됨 (건물크기에 따라 몇 가족 살 수 있는지 결정됨)
    - 서버는 CPU/메모리 같은 컴퓨팅 자원의 규모를 결정해야 한다 (가족별로 방크기가 얼마나 되는지 결정)

## AWS 에서의 가상화

- **Amazon EC2** 가 대표적인 예로, EC2 는 AWS 의 대규모 서버에서 가상화 수행
- 사용자는 OS 종류 / CPU / 메모리 크기를 자유롭게 선택해 **인스턴스** (가상 서버) 생성 가능
    
    ![Untitled](https://file.notion.so/f/f/3db2c1d3-d28f-483a-adc8-ee8abc696878/0f1da81f-d1ab-4783-8e6e-5636ded68de2/Untitled.jpeg?id=a8b1a1ab-e9d8-4d11-ba57-7d9c1763ae68&table=block&spaceId=3db2c1d3-d28f-483a-adc8-ee8abc696878&expirationTimestamp=1695823200000&signature=T5lQCIUHBwJGLH31lLrh8-AGNWGn9QxFj5MDSKq45Qo&downloadName=Untitled.jpeg)
