# 데이터베이스
### 데이터베이스 개요
- 관계형 데이터베이스(RDS)
    - 데이터들이 서로 연결되어 관계들로 구성된 데이터베이스
    - 데이터를 테이블 형태('스키마'라고 부른다)로 관리 하여 관계를 통해서 연결된 여러 테이블에 분산
    - SQL 언어를 사용하여 데이터를 검색 및 조작
    - 데이터를 중복없이 다루기에 데이터 무결성이 보장
    - 관계를 맺고 있는 데이터가 자주 변경 되는 애플리케이션에서 주로 사용
    - AWS RDS, AWS Aurora
- NoSQL 데이터베이스
    - NoSQL = non-SQL = non relational databases
    - 관계 구조를 갖지 않는 데이터베이스 관리 시스템
    - 관계 구조가 없기에 대규모의 데이터를 유연하게 처리할 수 있음
    - Key-Value Database, Document Database, Column Family Database, Graph Database 등
    - AWS DynamoDB
- 인 메모리 데이터 베이스
    - 디스크가 아닌 주 메모리에 데이터를 보유하고 있는 데이터베이스
    - 디스크 검색보다 자료접근이 훨씬 빠름
    - 데이터 양의 빠른 증가로 데이터베이스 응답속도가 떨어지는 문제를 해결할 수 있음
    - AWS Elasticache

### RDS on EC2
- EC2에서 운영되는 RDS
- 사용자가 직접 RDS 데이터베이스를 설치, 백업, 소프트웨어 패치 관리
- 사용자가 운영체제, 데이터베이스 설치 및 구성에 대한 모든 권한을 유지
- 사용자가 직접 운영을 할 필요가 없는 AWS 관리형 RDS 데이터베이스인 RDS, Aurora 사용가능

### AWS RDS
- AWS 관리형 관계형 데이터베이스(Relational Database Service)
- 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업을 AWS에서 관리
- Aurora, PostgreSQL, MySQL, MariaDB, Oracle, SQL Server 등을 제공
- SQL 쿼리를 이용하는 데이터베이스에 사용
- DB 다운타임 없이 스토리지 용량 자동으로 확장 가능(Storage Auto Scaling)
- DB 인스턴스 백업 및 복구를 위한 두가지 방법인 자동백업 및 데이터베이스 스냅샷(DB스냅샷)을 제공
- SSL/TLS를 사용하여 애플리케이션과 DB 인스턴스 간의 전송 중 암호화 가능
- AWS Key Management Service(KMS)를 통해 관리하는 키를 사용하여 모든 데이터베이스 엔진에 대한 암호화 가능

### RDS 읽기 전용 복제본(Read Replica)
- 읽기만 가능한 DB 인스턴스의 복제복을 여러개 만드는 기능
- 읽기를 별도로 분리하여 성능 향상
- 원본 DB의 읽기/쓰기 트래픽을 분산시켜 성능 향상
- SQL 쿼리를 많이 하는 리포팅 툴의 경우 읽기 복제본으로 연결하여 쿼리 성능 향상

### RDS 다중 AZ(Multi-AZ)
- 데이터베이스를 여러 가용영역에 배치
- 내구성과 가용성을 향상시킴
- 한 곳의 DB에 장애가 발생하면 다른 복제 DB로 자동 연결하도록 장애 조치 수행

### Aurora
- RDS 호환형 관계형 데이터베이스
- RDS에서 제공하는 대부분의 기능 제공
- AWS에서 만든 서비스로 다른 RDS보다 저렴한 비용에 성능이 더 뛰어남(확실하지 않음)
- 다른 RDS보다 속도는 3-5배 빠름
- 데이터베이스 설정, 패치 적용 및 백업과 같은 관리 태스크 자동화
- 개별 DB 인스턴스 기반이 아닌 여러 인스턴스를 하나로 운영하는 클러스터 DB 기반으로 구성됨
- DB 인스턴스 운영 및 데이터 베이스 용량을 수동으로 관리 하지 않는 서버리스 RDS 서비스인 Aurora Severless 사용가능

### ElasticCache
- 인메모리 데이터 스토어
- 1ms 미만의 빠른 응답시간을 제공
- 빠른 응답이 필요한 애플리케이션에 사용
- 기존의 RDS와 연결하여 DB 응답 성능을 개선하기 위해 사용(자주 사용하는 DB 데이터를 캐시)
- 세션 스토어, 게임 리더보드, 스트리밍 및 분석과 같이 내구성이 필요하지 않는 기본 데이터스토어로 사용
- 오픈소스 인메모리 데이터베이스 솔루션인 Redis 또는 Memcached 두가지 유형을 지원
- Memcached는 멀티쓰레드 지원, Redis는 싱글쓰레드만 지원
- 일반적으로 Redis가 더 많은 기능을 지원(스냅샷 백업, 복제기능, 고가용성 제공 등)

### DynamoDB
- NoSQL 데이터베이스 서비스
- 키-값(Key-Value), 문서 데이터 모델 지원
- 서버리스 서비스
- 용량에 맞게 자동으로 확장 및 축소(Auto Scaling)하므로 관리 및 운영 오버헤드 최소화
- 10ms 미만의 빠른 응답을 제공
- 초당 수백만개 이상의 요청 처리 가능
- 지연시간이 짧거나 빠른 응답이 필요한 애플리케이션에 사용
- 쇼핑몰 장바구니, 게임 플레이어 기록 저장 등에 사용

### Neptune
- 완전 관리형 그래프 데이터베이스 서비스
- 그래프 데이터베이스는 관계를 저장하고 탐색하도록 구축된 데이터베이스 유형
- 그래프 데이터베이스는 노드를 사용하여 데이터 엔터티를 저장하고 엣지로는 엔터티 간의 관계를 저장
- 쇼핑 추천 엔진, 소셜 네트워크 친구 등에 사용

### Database Migration Service(DMS)
- 데이터베이스를 마이그레이션 하는 서비스(DB -> DB)
- 온프레미스에서 AWS 또는 AWS 내에서 마이그레이션 가능
- 원본 DB를 사용하는 중에도 지속적으로 마이그레이션 가능
- 같은 종류 및 서로 다른 종류 DB도 마이그레이션 가능
- 다른 종류의 DB는 Schema Conversion Tool(SCT)를 이용해 데이터 스키마를 마이그레이션 대상 DB에 적합하게 변환해야 함(같은 종류의 DB는 데이터 변환X)

### 데이터 분석 서비스
- AWS Athena
    - 표준 SQL을 사용해 S3에 저장된 데이터를 분석할 수 있는 쿼리 서비스
    - Athena로 데이터를 로드할 필요 없이 S3에 저장된 데이터를 직접 사용
    - S3에 csv 데이터 파일을 저장하여 Athena를 사용해 SQL 쿼리를 하는 비용 효율적인 솔루션 구축
- AWS EMR(Elastic MapReduce)
    - MapReduce는 분산 병렬처리 컴퓨팅 모델의 이름
    - 빅데이터 플랫폼인 Hadoop 클러스터를 손쉽게 생성해 주는 서비스
    - 데이터 처리를 위한 EMR 클러스터(수십 ~ 수백대의 EC2 인스턴스)를 자동으로 구성하고 확장 및 축소하는 기능을 함
    - 머신러닝, 빅데이터 처리 등에 사용
- AWS Redshift
    - 데이터 웨어하우스 서비스
    - 데이터 웨어하우스는 정보에 입각한 의사결정을 내릴 수 있도록 분석 가능한 정보의 중앙 리포지토리
    - 데이터는 Database, S3 및 기타 소스로부터 보통 정기적으로 데이터 웨어하우스로 저장
    - 비즈니스 애널리스트, 데이터 엔지니어, 데이터 사이언티스트 및 의사 결정권자는 비즈니스 인텔리전스(BI) 도구, SQL 클라이언트 및 기타 분석 응용 프로그램을 통해 데이터에 액세스
- AWS Glue
    - 데이터 분석을 위한 ETL(Extract, Transform and Load) 서비스
    - 다양한 소스에서 데이터 검색 및 추출, 데이터 강화, 정리, 정규화 및 결합, 데이터베이스, 데이터 웨어하우스 및 데이터 호수에 데이터 로드 및 구성 등의 여러 작업을 포함
- AWS QuickSight
    - 클라우드 기반의 비즈니스 인텔리전스(BI) 도구
    - 대시보드, 그래프 등의 데이터 분석을 시각화를 통해 의사결정을 도와주는 서비스