## 📌 수집한 데이터를 활용하는 서비스 6가지

### 데이터 분석이란

- AWS 스토리지 서비스와 데이터베이스 서비스는 대량의 데이터를 고가용성으로 저장할 수 있다. 또는 대량의 데이터를 고속으로 처리하기 위한 서비스도 제공한다
- **이러한 서비스로 수집한 데이터를 분석하고 유용한 정보를 얻는 것**이 `데이터 분석 서비스`의 역할이다
- 데이터 분석의 종료
    - 빅데이터 분석 : 페타바이트 단위의 데이터 분석
    - 실시간 분석 : 물류 정보와 같이 즉시성이 필요한 정보에 적합
    - 시각화 : 데이터를 분석해 인간이 이해하기 쉬운 형태로 만드는 것도 데이터 분석의 하나

### 데이터 저장

- `데이터 레이크` : 분석에 사용할 데이터를 담아두는 장소 (저렴하게 대용량 데이터를 저장할 수 있는 서비스가 적합 ex. S3)
    
    !https://upload.wikimedia.org/wikipedia/commons/a/ab/Gentau_Pic_du_Midi_Ossau.jpg
    
- 원시 데이터를 그대로 분석하는 경우도 있지만 일반적으로 분석 방법에 적합한 형식으로 가공해 데이터베이스에 저장해 사용
- `데이터 웨어하우스`: 가공이 끝난 데이터를 저장해두는 장소 (주로 Redshift 이용)
    
    !https://www.newcastlesys.com/hs-fs/hubfs/2022/0406/220406-how-to-keep-your-warehouse-organized.jpeg?width=1000&name=220406-how-to-keep-your-warehouse-organized.jpeg
    
    - 가공한 데이터도 분석한 후 장기 보관을 위해 데이터 레이크에 다시 저장

### Amazon Athena

- `Amazon Athena` : 표준 SQL을 사용해 S3에 저장된 데이터를 간편하게 분석할 수 있는 대화식 쿼리 서비스
- 서버리스 서비스 → 인프라 관리가 필요 없이 실행한 쿼리에 대해서만 비용 발생
- 사용방법 : S3에 저장된 파일의 데이터 구조를 스키마로 정의하고 Athena에 저장하면 됨

### Amazon Glue

- 데이터를 분석할 때는 분석이 쉬운 형태로 변환하거나 데이터 웨어하우스로 마이그레이션한 뒤 이용하는 경우가 많음
- `AWS Glue` : 이러한 ETL(Extract, Transform, Load) 처리를 간단히 자동화하는 서비스

### Amazon OpenSearch Service

- `Amazon OpenSearch Service` : AWS 클라우드에서 OpenSearch 클러스터를 쉽게 사용할 수 있게 하는 서비스
- OpenSearch : Elasticsearch를 기반으로 만들어진 데이터 분석용 엔진으로 전체 텍스트 검색에 특히 강한 성능을 보임
- OpenSearch Dashboard를 통해 데이터의 검색, 집계, 그래프 표시 등 가능

### Amzaon EMR

- 빅데이터 분석은 한 대의 컴퓨터로 처리 불가 → `분산 처리 프레임워크` 등장 (ex. Apach Spark, Apach Hadoop)
- `Amzaon EMR` : 분산 처리 프레임워크를 AWS에서 실행하기 위한 서비스

### Amazon QuickSight

- Amazon QuickSight : 등록된 데이터를 분석하고 그래프화하는 등 데이터를 시각화하는 서비스

### Amazon Kinesis

- Amazon Kinesis : 실시간으로 데이터를 처리하기 위한 4가지 서비스를 제공
    - Kinesis Data Streams : 프로그램을 바로 처리할 수 없는 경우에도 데이터를 최대 1년 간 저장하고 대량의 원본 데이터를 프로그램에 전달
    - Kinesis Data Firehose : 대량의 데이터를 저장소에 실시간으로 순서대로 저장
    - Kinesis Data Analytics : 차례대로 저장되는 데이터를 실시간으로 분석, SQL이나 자바를 이용
    - Kinesis Video Streams : 대량의 동영상 데이터를 처리 프로그램에 전달
