# 기타

## 개발자 도구
### CodeCommit
- Git을 이용해 코드 버전을 관리하는 서비스
- Git은 소스 코드 관리 시스템

### CodeDeploy
- 소프트웨어(코드) 배포를 자동화하는 서비스

### CodeBuild
- 소프트웨어(코드)를 빌드 하는 서비스
- 소스 코드를 컴파일하는 단계부터 테스트 실행 후 소프트웨어 패키지를 개발하여 배포하는 단계까지 마칠 수 있는 완전 관리형의 지속적 통합 서비스

### CodePipeline
- 소프트웨어(코드) 릴리스 파이프라인을 자동화 하는 서비스
- 빌드 -> 테스트 -> 배포 단계를 자동화하는 서비스

### CodeArtifact
- 소프트웨어 패키지를 안전하게 저장, 게시 및 공유할 수 있도록 지원하는 완전 관리형의 아티팩트 리포지토리 서비스

### CodeStar
- 소프트웨어 개발 활동을 한곳에서 쉽게 관리 하는 서비스
- 애플리케이션 코드의 코딩, 빌드, 테스트 및 배포를 위한 전체 개발 및 지속적 전달 도구 체인을 간편하게 구성

### Cloud9
- 클라우드 기반 IDE 서비스(Integrated Development Environment)
- 코드를 작성, 실행, 편집하는 도구

### X-Ray
- 프로덕션 분산 애플리케이션(MSA)의 분석 및 디버깅 서비스

### Device Farm
- 데스크톱 브라우저 및 실제 모바일 디바이스에서 테스트를 진행하여 웹 및 모바일 앱 품질을 향상시키는 애플리케이션 테스트 서비스

### Fault Injection Simulator
- 오류 주입 실험을 수행하기 위한 완전 관리형 서비스
- 테스트 또는 프로덕션 환경에서 CPU나 메모리 소모가 갑자기 증가하는 등의 중단 이벤트를 만들어 애플리케이션에 스트레스를 유발

## 머신러닝
### Comprehend
- 텍스트 안에서 특정 항목을 찾아내는 서비스
- 분석 보고서에서 회사 이름 찾기, 부정적인 후기 또는 고객 서비스 상담사와의 긍정적인 고객 상담

### Rekognition
- 이미지, 비디오 분석(이미지에서 얼굴 탐지, 사물 인식) 

### Polly
- 텍스트를 음성으로 변환하는 서비스 

### Lex
- 음성 인식 서비스, 챗봇 구현 가능 

### Textract
- 스캔 문서에서 문자, 테이블, 양식 추출 서비스

### Translate
- 번역 서비스

### Transcribe
- 음성을 텍스트로 변환

### SageMaker
- 머신러닝 모델을 구축, 훈련 및 배포하는 서비스 

### Forecast
- 머신러닝을 기반으로 하며, 비즈니스 지표 분석을 위해 구축된 시계열 예측 서비스

### Kendera
- 지능형 검색 서비스
- 간단한 키워드 외에도 자연어 질문을 사용하여 원하는 답을 얻을 수 있으며 텍스트 조각, FAQ, PDF 문서 등에 관계없이 문서 내에서 정확한 답변을 반환

### Personalize
- Amazon.com에서 실시간 맞춤화 추천에 사용하는 것과 동일한 기계 학습(ML) 기술로 애플리케이션을 구축 가능한 서비스
- 특정 제품 추천, 맞춤화 된 제품 순위 재지정, 맞춤화 된 직접 마케팅 등을 포함하여 다양한 맞춤화 환경을 제공할 수 있는 애플리케이션을 손쉽게 구축 가능

### Amazon Connect
- 클라우드 기반 고객 센터 서비스
- 전화 통화, 자동 음성 음답, 챗봇 등의 기술 통합 가능

## 인프라 자동화
### CloudFormation
- AWS 인프라 세트를 수동으로 프로비저닝하면 많은 노력이 소요됨
- AMI 생성, EC2 생성, 보안 그룹 적용, Auto Scaling, ALB등의 세트를 수백 대 여러 리전에 배포할 시
- 수동 작업 말고 코드를 작성하여 자동화
- 코드를 통해 인프라를 프로비저닝, 관리 하는 서비스가 CloudFormation(Infrastructure as Code)
- 코드를 통해 자동화하여 AWS 인프라를 생성, 업데이트, 삭제 가능
- AWS 인프라를 프로비저닝하는 비용과 시간을 절약 할 수 있음
- 구성요소
    - Template : 인스턴스 유형, AMI ID, VPC, IP 주소 등의 인프라를 구성하기 위한 설정 값이 있는 JSON 또는 YAML 형식의 텍스트 파일로 이루어진 템플릿
    - Stack : Template을 사용하여 생성된 리소스
    - Change Set : Stack 리소스 변경 사항에 대한 세트

## AWS 기술지원
### AWS Support 플랜
- AWS에서는 기본, 개발자, 비즈니스, Enterprise On-Ramp, 엔터프라이즈 5가지 플랜을 제공 
- 기본 지원(Basic Support) 플랜은 모든 AWS 고객에게 제공 되며 아래를 포함
    - 고객 서비스 및 커뮤니티 : 고객 서비스, 설명서, 백서 및 AWS re:Post에 대한 연중무휴 24시간 상시 액세스를 제공
    - AWS Trusted Advisor : 핵심 Trusted Advisor 확인 및 지침에 액세스
        - 보안 그룹 - 제한 없는 특정 포트(무료)
        - AWS IAM 사용(무료)
        - Amazon S3 버킷 권한(무료)
        - 루트 계정의 Multi-Factor Authentication(MFA)(무료)
        - Amazon RDS 퍼블릭 스냅샷(무료)
        - 서비스 한도(무료)
    - AWS Personal Health Dashboard : AWS 서비스의 상태를 보여주는 개인화된 보기이며 리소스가 영향을 받을 때 알림을 표시
- https://aws.amazon.com/ko/premiumsupport/plans/

## AWS 비용관리
### AWS Budgets
- 예산을 지정하여 비용과 사용량을 추적하는 서비스
- 비용 또는 사용량이 사용자가 지정한 임계값을 초과할 때 이메일 등으로 알림을 받거나 RDS/EC2 등의 서비스를 중지하는 작업을 연결할 수 있음
- 비용 할당 태그를 이용해 AWS 특정 리소스에 태그 값을 지정하여 태그에 대한 리소스 보고서만 생성 가능(특정 애플리케이션을 실행하는 서비스 비용과 사용량에 대한 보고서 작성)

### AWS Cost Explorer(비용 탐색기)
- AWS 서비스에 대한 비용 및 사용량을 분석하는 서비스
- 서비스, 계정, 일, 월 등의 사용량 및 비용을 확인하여 보고서를 생성 및 다운로드 할 수 있음
- Cost Explorer는 그래프, 숫자를 통한 시각화 된 인터페이스를 제공

### AWS 비용 및 사용 보고서
- AWS 비용 및 사용에 대한 가장 상세한 보고서를 제공하는 서비스

### AWS Pricing Calculator
- AWS 서비스 사용에 대한 예상 비용을 계산하는 서비스
- https://calculator.aws

## AWS Well-Architected Framework
### AWS Well-Architected
- 애플리케이션에 사용할 보안, 성능, 복원력 및 효율성이 뛰어난 인프라를 구축하는 클라우드 아키텍트를 돕기 위한 프레임워크
- 여섯 가지 원칙을 기반
    - 운영 우수성 원칙(Operational Excellence)
    - 보안 원칙(Security)
    - 안정성/신뢰성 원칙(Reliability)
    - 성능 효율성 원칙(Performance Efficiency)
    - 비용 최적화 원칙(Cost Optimization)
    - 지속 가능성 원칙(Sustainability)