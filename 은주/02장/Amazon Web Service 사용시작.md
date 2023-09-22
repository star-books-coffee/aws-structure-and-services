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
