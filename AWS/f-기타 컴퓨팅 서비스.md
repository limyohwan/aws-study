# 컴퓨팅 - 기타

### AWS Lambda
- Serverless
    - 서버를 사용자가 관리할 필요가 없음
    - 실제로 서버는 존재하며 서버 인프라 운영은 AWS등의 클라우드 회사에서 담당
    - AWS에서 용량조정, 프로비저닝, 패치 등의 인프라를 관리
    - 사용자는 필요한 애플리케이션을 구축해서 사용하기만 하며 됨
    - Lambda, Fargate, S3, DynamoDB, Aurora Serverless, SNS, SQS, Gateway 등
- 코드를 실행하여 동작하는 서버리스 컴퓨팅
- AWS에서 운영에 필요한 모든 인프라를 관리
- 요청할 때에만 시스템을 사용하는 온디맨드 방식의 이벤트 중심의 실행
- 사용한 만큼만 비용 지불
- 사용량이 늘어나면 자동으로 용량이 확장되므로 용량 계획이 필요 없고 확장성이 뛰어남
- 다양한 프로그래밍 언어 지원(nodejs, pytho, java 등)
- 독립적으로 사용하지 않고 다른 서비스와 결합하여 사용(API Gateway, Kinesis, DynamoDB, SNS, SQS, S3, CloundFront)

### AWS Batch
- AWS에서 배치 컴퓨칭 작업을 효율적으로 손쉽게 실행할 수 있게 해주는 서비스
- 배치 컴퓨팅은 수동 개입 없이 하나 이상의 컴퓨터에서 일련의 프로그램을 실행하는 것
- 제출된 작업에 따라 리소스를 효율적으로 프로비저닝함으로써 용량 제한을 해소하고 컴퓨팅 비용을 줄이며 결과를 신속하게 제공
- 자동으로 컴퓨팅 리소스를 프로비저닝하고 워크로드의 양 및 규모에 따라 워크로드 분배를 최적화
- 작업 실행을 위한 배치 컴퓨팅 소프츠웨어나 서버 클러스터를 설치하여 관리할 필요가 없음
- 배치 작업은 Docker 컨테이너 이미지로 정의 되어 Elastic Container Services(ECS)에서 실행됨

### ECS & Fargate
- Container
    - 애플리케이션 구성 라이브러리를 패키지로 묶어서 컨테이너 엔진 위에서 실행하는 것
    - OS환경이 바뀌어도 구동 가능하며 각각의 컨테이너가 독립적임
    - 마이크로서비스를 배포하는데 주로 이용
- Elastic Container Servie(ECS)
    - 도커 컨테이너를 배포 관리하는 오케스트레이션 서비스
- Amazon Elastic Kubernetes Service(EKS)
    - AWS에서 쿠버네티스를 실행하는 서비
- AWS Fargate
    - 서버리스 컨테이너 서비스
    - 서버 프로비저닝, 패치 적용, 클러스터 용량 관리 또는 인프라 관리를 AWS에서 자동으로 수행
    - Elastic Container Servie 및  Elastic Kubernetes Service와 연동되는 서비스
    - ECS, EKS 모두 Fargate를 통해 프로비저닝된 컨테이너를 사용하여 자동으로 컨테이너 크기를 조정하고 로드밸런싱 가능
- Amazon Elastice Container Registry(Amazon ECR)
    - 도커 등의 컨테이너 이미지를 공유, 배포 등의 관리 서비스

### Elastic Beanstalk
- 웹 애플리케이션 및 서비스를 배포하고 운영하는 서비스
- 사용자가 직접 인프라 리소스를 구성할 필요 없고 애플리케이션 코드에만 집중하면 됨
- 코드를 업로드하기만 하면 Elastic Beanstalk가 용량 프로비저닝, 로드 밸런싱, Auto Scaling부터 시작하여 애플리케이션 상태 모니터링 등의 배포를 AWS에서 자동으로 처리
- Java, .NET, PHP, Node.js, Python, Ruby, Go 및 Docker 웹 애플리케이션을 지원

### Lightsail
- 웹 애플리케이션 또는 웹 사이트를 클릭 몇번으로 설정하고 실행할 수 있는 사용이 쉬운 클라우드 리소스
- 인스턴스, 컨테이너, 데이터베이스 및 스토리지와 같은 서비스를 쉽게 배포할 수 있음
- 클라우드 경험이 없는 사용자를 위한 서비스
- EC2, ELB, EBS 등의 서비스 사용에 대한 대안
- 서비스를 저렴하고 예측 가능한 월간 요금으로 사용 가능

### Amazon WorkSpaces & Amazon AppStream 2.0
- Amazon WorkSpaces
    - 클라우드 기반 Microsoft Windows 또는 Amazon Linux 데스크톱 가상화 서비스
    - 기존 데스크톱을 대체할 수 있는 클라우드 기반 가상 데스크톱
- Amazon AppStream 2.0
    - 애플리케이션 및 데스크톱 스트리밍 서비스