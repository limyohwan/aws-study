### 5번
- AWS Artifact = 보안 및 규정 준수 문서
- AWS Config = 모든 리소스에 대한 구성 관리 세부 정보 다운로드
- AWS training and certification 사이트 = AWS 서비스를 위한 교육 자료
- Aamzon inspector = AWS 클라우드에 배포된 애플리케이션 보안평가

### 8번
- 인터넷 게이트웨이 = 인터넷의 인바운드 트래픽이 VPC에 액세스 하도록 허용하는 서비스
- NAT 게이트웨이 = 프라이빗 서브넷의 리소스가 인터넷과 통신하기 위한 게이트웨이, 아웃바운드 트래픽만 허용
- AWS WAF = 방화벽
- VPC 피어링 = VPC끼리의 연결 서비스

### 9번
- AWS X-Ray = 프로덕션 분산 애플리케이션의 분석 및 디버깅 서비스
- AWS Shield = DDos 방어 서비스
- AWS Trusted Advisor = 사용자의 AWS 환경을 조사하여 비용 절감, 시스템 성능 향상, 보안 결함 제거를 위한 권장 사항 제시
- AWS CloudTrail = AWS 내에서 수행되는 모든 계정 활동 기록, AWS 계정의 위험 감사를 지원

### 13번
- AWS Well-Architected Framework
    - 여러 AWS 계정을 단일 계정으로 통합 = 비용 최적화 원칙 - 단일 계정 통합으로 청구 비용 할인
    - AWS 클라우드 설계에 대한 설계 탄력성 = 안정성 / 신뢰성 원칙 - 수요에 따라 리소스 증가 및 감소가 가능하므로 용량 추정 불필요

### 16번
- AWS EC2 비용 최적화
    - Auto Scaling 그룹 구현, 필요에 따라 인스턴스 추가 및 제거
    - 예약 인스턴스 구매 - 장기 약정으로 할인된 요금으로 인스턴스 사용

### 19번
- Amazon Simple Queue Service(Amazon SQS) = 애플리케이션의 분리 및 확장 가능, 서로 간에 느슨한 결합 제공
- AWS Outposts = 온프레미스에서 AWS 서비스를 실행하게 해주는 서비스
- Amazon S3 = 스토리지 서비스
- Amazon Simple Email Service(Amazon SES) = 이메일 서비스

### 20번
- Amazon Inspector = EC2 및 컨테이너 워크로드에서 소프트웨어 취약성과 네트워크 노출을 스캔하는 취약성 관리 서비스
- AWS Config = AWS 리소스 구성 변경사항을 로그 기록
- AWS Trusted Advisor = 미사용 리소스와 유휴 리소스를 식별하여 비용 최적화, 비용최적화 검사로 사용되지 않거나 사용률이 낮은 리소스를 확인
- AWS Organizations = 여러 AWS 계정을 중앙에서 관리하는 서비스

### 21번
- AWS Well-Architected Framework
    - 수요 변화에 따라 효율성을 유지하기 위해 리소스를 적시에 프로비저닝하고 필요에 따라 확장하도록 명시함 - 성능 효율성

### 22번
- AWS WAF = 웹 애플리케이션 방화벽, SQL 주입 및 교차 사이트 스크립팅 방어 가능
- Amazon VPC = AWS 네트워크
- Amazon GuardDuty = AWS 계정 및 워크로드에서 악의적 활동을 모니터링하고 상세한 보안 결과를 제공하는 위협 탐지 서비스
- Amazon CloudWatch = AWS 클라우드 리소스와 AWS에서 실행되는 애플리케이션을 위한 모니터링 서비스

### 25번
- AWS가 제공하는 보안 관련 서비스
    - MFA 기능 제공
    - AWS Trusted Advisor 보안 검사
    - 데이터 암호화

### 26번
- AWS Artifact = AWS ISO 인증, 여러 지역의 인증 기구와 규정 준수 기관의 인증서를 제공
- AWS 서비스 약관 = Amazon EC2 이용약관
- AWS Cost Explorer = 기업의 AWS 지출 내역

### 28번
- AWS CodeBuild = 소프트웨어(코드)를 빌드하는 서비스
- AWS Code Pipeline = 소프트웨어(코드) 릴리스 파이프라인을 자동화하는 서비스
- AWS CloudFormation = 코드를 통해 AWS 인프라를 자동으로 프로비저닝, 관리하는 서비스
- Amazon CloudWatch = AWS 클라우드 리소스와 AWS에서 실행되는 애플리케이션을 위한 모니터링 서비스

### 29번
- 요구사항에 충족하는 EC2 인스턴스 유형
    - 인터넷 트래픽 단기적으로 급증
    - 트래픽이 증가하는 동안 애플리케이션 중단 불가
    - 비용을 최소화하고 유연성을 극대화 해야함
- 온디맨드 인스턴스 = 중단되지 않는 단기적인 용도로 적합

### 30번
- AWS 클라우드에서 워크 로드를 실행할 떄의 시장 이점
    - 새로운 워크로드를 배포하는 데 필요한 직원 시간 단축 - AWS에서 많은 부분을 담당하기에 사용자의 시간을 단축
    - 애플리케이션 개발 팀의 생산성 향상 - AWS에서 인프라 부분을 담당하기에 개발팀은 개발에만 집중 가능

### 37번
- 배치 워크로드는 Amazon EC2 인스턴스에서 완료하는데 5시간이 걸리며 처리 할 데이터 양은 매월 두배로 늘어나며 처리 시간에 비례함
- 위의 수요를 해결하는데 가장 적합한 클라우드 아키텍처는?
    - 여러 EC2 인스턴스에 애플리케이션을 배포하고 워크로드를 병렬로 실행
    - 여러 인스턴스에서 병렬처리를 통해 처리 시간을 줄일 수 있음

### 39번
- 모든 지원 수준에서 사용하는 AWS 결제 지원 리소스
    - AWS 고객 서비스

### 40번
- AWS CloudTrail = AWS내에서 수행되는 모든 계정 활동 기록, Amazon EC2 인스턴스를 중지한 특정 사용자를 식별
- Amazon Inspector = EC2 및 컨테이너 워크로드에서 소프트웨어 취약성과 네트워크 노출을 스캔하는 취약성 관리 서비스
- Amazon CloudWatch = AWS 클라우드 리소스와 AWS에서 실행되는 애플리케이션을 위한 모니터링 서비스
- VPC 흐름 로그(Flow Log) = VPC의 네트워크 인터페이스에서 전송되고 수신되는 IP 트래픽에 대한 정보를 수집