# 보안, 자격 증명 및 규정 준수

### AWS 공동 책임 모델
|고객 책임 '클라우드에서의 보안’|AWS 책임 '클라우드의 보안’|
|:---:|:---:|
|고객이 구성을 하고 사용하는 부분|고객이 변경, 구성이 불가능한 AWS에서 관리하는 부분|
|고객 데이터, 애플리케이션, 접근권한, ID관리, 암호화 등|AWS 클라우드 인프라(하드웨어 시설), AWS관리 소프트웨어|
|게스트 OS, 애플리케이션 패치|인프라 관련 결함 수정과 패치|
|자체 게스트 운영체제, 데이터베이스 및 애플리케이션 구성|인프라 디바이스 구성을 유지 관리|
|자사 직원 교육|AWS 직원 교육|
|클라우드 인프라 위의 보안|클라우드 인프라 자체의 보안|

### Shield
- AWS 웹 애플리케이션을 DDoS(Distributed Denial of Service) 공격으로부터 보호
- Shield Standard
    - 모든 AWS 사용자에게 적용되어 있음(무료)
    - SYN/UDP Flood등 기본적인 DDoS공격 보호
- Shield Advanced
    - 스탠다드 서비스보다 많은 보호 제공(유료)
    - EC2, ELB, CloudFront, Route53등에서 정교한 DDoS 보호제공

### WAF(Web Application Firewall)
- 웹 애플리케이션을 보호하는 방화벽
- HTTP에서 동작
- Application Load Balancer, API Gateway, CloudFront에 적용 가능
- WAF의 Web ACL(Access Control List)를 통해 정의할 수 있는 기능
    - 악성 IP 주소 차단
    - 특정 국가의 엑세스 제어(차단)
    - SQL Injection, Cross-Site-Scripting(XSS) 방어
    - 속도기반규칙(Rate-based rules)으로 DDoS공격방어

### KMS(Key Management Service)
- 암호화(Encryption)
    - 데이터를 도난이나 해킹으로부터 보호하기 위한 방법
    - 3가지 암호화 방법
        - 전송중 암호화 : 네트워크로 전송하는 트래픽을 암호화
        - 서버측 암호화 : 서버에 저장된 데이터를 암호화
        - 클라이언트측 암호화 : 데이터를 보내기전에 암호화
- 암호화 키를 생성 및 관리하는 서비스
- 키(Key)는 암호화를 하고 암호를 해독하는 역할
- AWS에서 암호화에 관련된 서비스는 대부분 KMS와 관련되어 있음
- EBS, S3, RDS등의 AWS 서비스 데이터 암호화에 KMS 사용
- 키를 자동 교체하는 기능 지원
- 감사를 위해 AWS CloudTrail과도 통합되어 모든 키 사용에 관한 로그를 제공
- 3가지 유형의 키 제공
    - 고객 관리형 키(Customer managed keys)
        - 사용자가 생성, 소유 및 관리하는 AWS 계정의 KMS 키
        - 키 정책, IAM 정책 및 권한 부여, 암호화 구성요소 등의 제어 권한을 사용자가 가짐
    - AWS 관리형 키(AWS managed keys)
        - AWS 서비스가 고객의 계정에서 고객 대신 생성, 관리 및 사용하는 KMS 키
        - 키 정책, 키 삭제 등의 제어 권한이 없거나 제한이 있음 
    - AWS의 키(AWS owned keys)
        - AWS 서비스가 여러 AWS 계정에서 사용하기 위해 소유하고 관리하는 KMS 키 모음

### CloudHSM
- CloudHSM은 AWS에서 제공하는 하드웨어 암호화 장비를 통한 하드웨어 방식의 암호화
- KMS는 AWS에서 관리하는 소프트웨어 방식의 암호화방식이며 KMS와는 다르게 암호화 키관리는 사용자(클라이언트)가 해야함
- 고객 제공 키(SSE-C, Customer Provided Keys)에 적합한 방식

### ACM(AWS Certificate Manager)
- SSL/TLS 인증서를 중앙에서 관리하는 서비스
- AWS 리소스에 사용할 공인 및 사설 SSL/TLS(Secure Socket Layer, 전송 계층 보안) 인증서를 관리 및 배포 할 수 있음
- SSL/TLS 인증서는 ACM에서 자동으로 갱신 됨

### Secrets Manager
- 보안 정보(자격증명)를 중앙 집중식으로 저장, 검색, 액세스 제어, 교체, 감사 및 모니터링하는 서비스
- 보안 정보는 데이터베이스 자격 증명, 온프레미스 리소스 자격 증명, SaaS 애플리케이션 자격 증명, 타사 API 키 및 Secure Shell(SSH) 키 등이 될 수 있음
- 보안 정보(자격증명,Secret)를 유지하는 방법
    - 사용자가 소유하고 AWS Key Management Service(KMS)에 저장한 암호화 키를 사용해 저장 보안 정보를 암호화
    - 사용자는 AWS Identity and Access Management(IAM) 정책을 사용하여 보안 정보에 대한 액세스를 제어
    - 사용자가 보안 정보를 검색하면 Secrets Manager가 해당 보안 정보를 복호화하여 TLS를 통해 안전하게 로컬 환경으로 전송
- 보안 정보(자격 증명)을 자동으로 교체 및 관리 가능
    - Amazon RDS, Amazon Redshift 및 Amazon DocumentDB와 기본적으로 통합되며 사용자 대신 이러한 데이터베이스 자격 증명을 자동으로 교체
    - Lambda의 코드와 통합하여 30일, 60일 등의 자격증명 자동교체 날짜를 지정하여 실행 가능

### AWS Artifact
- AWS의 규정 준수 문서와 AWS 계약에 대한 문서를 제공하는 사이트
- 실제 서비스가 아니라 문서를 보고 다운 받을 수 있는 사이트
- 보고서 : SOC(Service Organization Control) 보고서와 PCI(Payment Card Industry) 보고서, 그리고 여러 지역의 인정 기구와 규정 준수 기관에서 AWS 보안 제어의 구현 및 운영 효율성을 입증하는 인증서가 포함
- 계약 : BAA(Business Associate Addendum)와 NDA(Nondisclosure Agreement)이 포함

### AWS GuardDuty
- AWS 계정 및 워크로드에서 악의적 활동을 모니터링하고 상세한 보안 결과를 제공하는 위협 탐지 서비스
- 공격자 정찰, 인스턴스 침해, 계정 침해 및 버킷 침해와 같은 위협을 파악하도록 지원하여 AWS 계정, 워크로드 및 데이터에 대한 광범위한 보호를 제공
- 보안 탐지 결과를 GuardDuty 콘솔과 Amazon CloudWatch Events로 전달하여 알림을 토대로 조치를 취할 수 있고 기존 이벤트 관리 또는 워크로드 시스템에 통합 가능

### AWS Macie
- 데이터 보안 및 데이터 프라이버시 서비스로서, 기계 학습 및 패턴 일치를 활용하여 AWS에서 민감한 데이터를 검색하고 보호
- 이름, 주소 및 신용카드 번호와 같은 개인 식별 정보(PII)를 포함하여 대규모의 점점 증가하는 민감한 데이터 유형 목록을 자동으로 감지
- S3 버킷에 기계 학습 및 패턴 매칭 기법을 적용하여 개인 식별 정보(PII)와 같은 민감한 데이터를 식별하고 사용자에게 알릴 수 있음

### AWS Inspector
- EC2 및 컨테이너 워크로드에서 소프트웨어 취약성과 의도하지 않은 네트워크 노출을 지속적으로 스캔하는 자동화된 취약성 관리 서비스

### Security Hub
- AWS에서 보안 상태에 대한 통합 보기를 제공
- AWS 환경에서 보안 검사를 자동화하고, 보안 분석 결과를 관리하며, 우선순위가 가장 높은 보안 문제를 식별

### AWS Detective
- 잠재적 보안 문제나 의심스러운 활동의 근본 원인을 쉽고 빠르게 분석, 조사 및 식별하는 서비스
- AWS GuardDuty, AWS Macie 및 AWS Security Hub는 잠재적 보안 문제나 탐지 결과를 식별하여 문제가 발생했음을 알리거나 수정할 위치를 가리킬 때 매우 유용
- 근본 원인을 격리하고 조치를 취하기 위해 더 자세한 정보를 탐색하고 더 많은 정보를 분석해야 하는 보안 탐지 결과가 있을 수 있음
- 근본 원인을 확인하는 작업은 개별 데이터 원본에서 로그를 수집 및 결합하여 데이터를 구성한 후 보안 분석가가 데이터를 해석하고 시간이 오래 걸리는 조사를 수행하는 작업이 포함된 복잡한 프로세스
- AWS Detective를 사용하면 보안 팀이 쉽게 조사하고 탐지 결과의 근본 원인을 빠르게 파악할 수 있으므로 이 프로세스를 단순화
- AWS Detective는 Virtual Private Cloud(VPC) 플로우 로그, AWS CloudTrail 및 Amazon GuardDuty와 같은 여러 데이터 원본에서 이벤트를 분석하고, 시간에 따른 리소스, 사용자 및 이들 간의 상호작용에 대한 통합된 대화형 보기를 자동으로 생성
- 이 통합된 보기를 통해 한 곳에서 모든 세부 정보와 컨텍스트를 시각화하여 탐지 결과에 대한 근본적인 이유를 식별하고, 관련 기록 활동을 자세히 탐구하며, 근본 원인을 빠르게 확인
- 전반적인 API 호출 볼륨은 특정기간에 성공한 호출과 실패한 호출을 표시하고, 설정된 기준선과 이를 비교하여 비정상적인 활동의 패턴을 식별하고, 보안 탐지 결과를 검증

### AWS Abuse
- 악의적이거나 불법적인 용도로 AWS 리소스가 사용되고 있다고 의심될 경우 AWS에 알릴 수 있음
- AWS 신뢰 및 안전팀은 AWS 리소스가 다음과 같은 유형의 침해 행위와 관련하여 사용되는 경우 고객을 지원
    - 스팸 : AWS 소유 IP 주소에서 원치 않는 이메일을 수신하거나 AWS 리소스가 웹 사이트 또는 포럼에 스팸을 보내는 데 사용됨
    - 포트 스캐닝 : 하나 이상의 AWS 소유 IP 주소에서 서버의 여러 포트로 패킷을 전송하고 있음이 로그에 표시되며 이는 보안되지 않은 포트를 찾으려는 시도라고 생각함
    - DoS (서비스 거부) 공격 : 하나 이상의 AWS 소유 IP 주소가 리소스의 포트를 패킷으로 플러딩하는 데 사용됨이 로그에 표시되며 서버 또는 서버에서 실행되는 소프트웨어를 압도하거나 충돌하려는 시도라고 생각함
    - 침입 시도 : 하나 이상의 AWS 소유 IP 주소가 리소스에 로그인하려고 사용되고 있음이 로그에 표시됨
    - 금지된 콘텐츠 호스팅 : AWS 리소스가 불법 콘텐츠 또는 저작권이 있는 콘텐츠와 같은 금지된 콘텐츠를 저작권 보유자의 동의 없이 배포하는 데 사용된다는 증거가 있음
    - 맬웨어 배포 : 설치된 컴퓨터 또는 시스템을 손상시키거나 해를 입히기 위해 의도적으로 생성된 소프트웨어를 배포하는 데 AWS 리소스가 사용된다는 증거가 있음
- AWS 리소스가 침해 목적으로 사용되었다고 의심되는 경우 Amazon AWS 침해 보고 양식을 사용하거나, abuse@amazonaws.com으로 연락하면 됨

### AWS Cognito
- 애플리케이션에 대한 로그인 및 인증을 제공하는 기능
- 웹과 모바일 앱에 빠르고 사용자 가입, 로그인 및 액세스 제어 기능
- 애플, 구글, 페이스북 등의 계정과 통합 가능

### AWS SSO(Single Sign On)
- SSO는 중앙에서 관리하는 하나의 계정으로 여러 애플리케이션에 로그인하는 기능
- AWS Organization, Active Directory, SAML 2.0과 통합 가능
- SAML은 인증을 지원하기 위한 표준 데이터 포맷