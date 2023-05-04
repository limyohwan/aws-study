# Elastic Load Balancing & Auto Scaling

### 시스템 아키텍처
- 확장성(Scalability)
    - 수직적 확장 : 자원을 추가하는 방식, 인스턴스의 스펙을 올림
    - 수평적 확장 : 노드를 추가하는 방식, 인스턴스의 개수를 늘림
- 고가용성(High Availability)
    - 지속적으로 정상 운영이 가능한 상태를 구축
    - 장애를 대비하여 시스템을 이중화하는 것
    - 여러 가용영역에 시스템을 분산 배치하는 방법
- 느슨한 결합(Loosely Coupled)
    - 한 시스템의 상태가 다른 쪽에 영향을 덜 미치는 결합
    - 로드 밸런서, 메시지 큐 등

### Elastic Load Balancing(ELB)
- 트래픽을 분산하는 서비스
- 인스턴스, 컨테이너, IP 등 여러 대상으로 자동으로 분산 가능

### ELB 종류
- Application Load Balancer
    - Layer 7
    - HTTP, HTTPS
    - HTTP Header Content를 사용해 라우팅 요청 처리
    - 웹 애플리케이션 서비스에 적합
- Network Load Balancer
    - Layer 4
    - TCP, UDP, TLS
    - Protocol, Prot Number를 사용해 라우팅 요청 처리
    - 수백만의 대용량 트래픽 처리에 적합
- Gateway Load Balancer
    - Layer 3 - Gateway Load Balancer Endpoint
    - Layer 4 - Gateway Load Balancer
    - GENEVE protocol을 사용하여 encapsulation 트래픽 전송
    - Transparency한 네티워크 게이트웨이를 제공하므로 방화벽, IPS, IDS 등의 원본 패킷의 데이터가 중요한 가상 어플라이언스에 적합
- Classic Load Balancer
    - Layer 4, Layer 7
    - HTTP, HTTPS, TCP, TLS
    - Protocol, Port Number를 사용해 라우팅 요청 처리
    - 이전 세대 EC2-Classic 네트워크에서 사용

### ELB 구성
- Client
- Listener
    - 연결 요청을 확인하는 프로세스
    - 클라이언트와 로드 밸런서 간의 연결을 위한 프로토콜 및 포트 번호로 구성
    - 로드 밸런서와 대상 간의 연결을 위한 프로토콜 및 포트번호로 구성
- Target Group
    - 대상(Target)의 모임
    - Target
        - EC2 인스턴스
        - EC2 Auto Scaling Group
        - IP address
        - Lambda

### Auto Scaling
- EC2 인스턴스를 자동으로 확장하고 축소하는 기능
- 사용자가 정의한 조정 정책에 따라 인스턴스 수가 증가 되거나 축소 됨

### Auto Scaling 구성
- 오토 스케일링 그룹 : EC2 인스턴스의 그룹
- 시작 템플릿(런치 템플릿) : EC2 서버를 시작하기위한 AMI, 인스턴스 유형 정보를 가진 템플릿
- 조정 옵션(조정 정책) : Auto Scaling 을 실행하기 위한 조건

### Auto Scaling 조정 정책
- 항상 현재 인스턴스 수준 유지 관리
- 수동 조정
- 일정을 기반으로 조정
- 온디맨드 기반 조정
- 예측 조정 사용(Predictive Scaling)

### Auto Scaling 동적 조정(Dynamic Scaling)
- 대상 추적 조정(Target Tracking Scaling)
- 단계 조정(Step Scaling)
- 단순 조정(Simple Scaling)