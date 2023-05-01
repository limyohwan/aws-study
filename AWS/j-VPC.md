# 네트워크 - VPC

### VPC(Virtual Private Cloud)
- AWS의 가상 네트워크
- AWS 서비스의 네트워크 연결을 제어하는 기능
- VPC 구성요소
    - 서브넷 : VPC의 IP 주소 범위
    - 라우팅 테이블 : 네트워크 트래픽을 전달할 위치를 결정하는 데 사용
    - 인터넷 게이트웨이: VPC의 리소스와 인터넷 간의 통신을 연결하는 게이트웨이
    - Network ACL : 서브넷과 연결되어 서브넷의 내부와 외부의 트래픽을 제어하는 방화벽
- AWS 계정을 생성하면 기본 VPC 네트워크가 생성됨
- 기본 VPC는 인터넷과 연결되어 있고 EC2 인스턴스를 생성하면 기본 VPC에 연결
- VPC는 Private 네트워크이므로 Private IP 대역을 사용
- AWS Private Services : VPC에 네트워크 환경을 지원하는 서비스(EC2 등)
- AWS Public Services: VPC 외부에 위치하며 인터넷으로부터 액세스 가능한 서비스(S3, DynamoDB, WorkSpaces 등)

### Network Address Translation(NAT) 개요
- Public IP를 가진 인스턴스는 IGW(Internet Gateway)를 통해 인터넷으로 트래픽을 전송
- Private IP를 가진 인스턴스는 Private IP 주소를 Public IP 주소로 변환하는 NAT를 사용

### NAT Gateway
- NAT 게이트웨이는 네트워크 주소 변환 서비스
- 프라이빗 서브넷의 인스턴스가 VPC 외부의 인터넷 서비스에 연결
- 외부 인터넷 서비스에서는 프라이빗 서브넷의 인스턴스와의 연결을 시작할 수 없음

### Security Group
- 인스턴스에 대한 인바운드 및 아웃바운드 트래픽을 제어하는 가상 방화벽
- 서브넷 수준이 아니라 인스턴스 수준에서 작동(EC2 인스턴스의 ENI와 연결 됨)
- 보안 그룹은 허용 규칙만 지정 가능하고 거부 규칙은 지정할 수 없음
- 보안 그룹은 생성된 VPC 내에서만 사용 가능

### Network Access Control List(NACL)
- 서브넷 내부와 외부의 트래픽을 제어하는 방화벽
- 서브넷 레벨의 연결 방화벽
- 하나의 NACL은 여러 서브넷과 연결 가능
- 하나의 서브넷은 하나의 NACL만 연결 가능
- 허용, 거부 규칙 모두 지정 가능
- NACL 규칙 번호
    - 가장 낮은 번호가 지정된 규칙부터 시작해서 트래픽이 내부 또는 외부로 전달되도록 허용되는지 결정
    - 번호가 가장 낮은 규칙부터 평가됨
    - 규칙에 사용할 수 있는 가장 높은 번호 = 32766

### VPC Peering
- VPC 끼리는 기본적으로 네트워크 통신이 되지 않음
- VPC 피어링은 두 VPC 끼리 트래픽을 라우팅 할 수 있도록 하기 위한 두 VPC 사이의 네트워킹 연결
- VPC 피어링 트래픽은 퍼블릭 인터넷을 통과하지 않고 프라이빗 IP 주소를 사용하여 서로 통신
- VPC 피어링은 같은 리전 내에, 다른 리전 간, 다른 AWS 계정 간 가능
- 지원되지 않는 VPC Peering 구성
    - CIDR 중첩(CIDR Overlapping) : 일치하거나 중첩되는 IPv4 CIDR 블록이 있는 VPC 간에는 VCP 피어링 연결을 만들 수 없음 = 쉽게말하면 같은 IP 끼리 연결 불가
    - 전이적 피어링(Transitive Peering) : 3개의 VPC가 모두 연결되려면 서로 연결되어 있어야 하며 라우팅 할 수 없음, VPC Peering은 1:1 연결만 가능

### VPC Endpoints
- AWS S3와 DynamoDB 등 AWS 서비스에 대한 프라이빗 연결

### VPN 개요
- 인터넷을 이용해 가상 사설망(Virtual Private Network)을 구성 하는 것
- VPN 트래픽은 VPN 프로토콜로 보호 됨
- IPSec : Site-to-Site VPN 암호화 프로토콜, Main Office와 Branch Office를 연결할 때 사용
- TLS : Client VPN, Client와 Main Office를 연결할 때 사용

### AWS Site-to-Site VPN
- IPSec 암호화 프로토콜을 사용하여 AWS VPC와 온프레미스 간에 프라이빗 네트워크를 구성
- 인터넷 연결을 사용

### Direct Connect
- AWS와 온프레미스 간에 DX(Direct Connect) Location(전용선)을 통해 프라이빗 네트워크 연결 생성
- 물리적인 구성을 해야 하기에 설치 시간이 오래 걸림
- VPN 보다 가격이 비싸며 인터넷을 통하지 않기에 인터넷 전송 비용이 들지 않음
- 트래픽이 인터넷 연결을 사용하는 Site-to-Site VPN 보다 안정적

### Transit Gateway
- Transit Gateway를 통해 각 VPC 또는 VPN 간의 모든 트래픽을 라우팅
- 복잡한 피어링 관계를 제거하여 네트워크를 간소화

### VPC Flow Log
- VPC의 네트워크 인터페이스에서 전송되고 수신되는 IP 트래픽에 대한 정보를 수집할 수 있는 기능
- 데이터는 AWS CloudWatch Logs 또는 AWS S3에 저장 가능
- VPC, Subnet, EC2 인스턴스 레벨에 Flow Log 활성화 가능
- Flow Log 레코드는 허용(Accept), 거부(Reject), 모든 트래픽(All Traffic)을 캡처
- 2 123456789010 eni-1235b8ca123456789 172.31.16.139 172.31.16.21 20641 22 6 20 4249 1418530010 1418530070 ACCEPT OK