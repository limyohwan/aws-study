# Elastice Block Store(EBS)
- EC2에 연결하여 사용하는 블록 스토리지
- EC2 인스턴스 시작시 AMI가 설치 되는 EBS 루트 볼륨이 생성됨
- EC2 종료 후 EBS가 같이 삭제 되지 않으면 사용 비용이 청구 됨
- 여러 개의 EBS 볼륨을 생성하여 EC2에 추가 연결 가능
- EBS와 EC2는 동일한 가용영역에 있어야 연결 가능
- 스냅샷 기능을 통해 EBS 볼륨 백업 가능
- 수명 주기 관리자(Data Life Cycle Manager) 정책을 통해 스냅샷 생성 일정을 자동화 가능
- AWS Key Management Service(KMS)를 이용해 EBS 볼륨 암호화 가능

### Amazon Machine Image(AMI)
- OS, 애플리케이션, 서버 프로그램 설정 등이 미리 구성된 이미지
- EC2 인스턴스를 시작하는데 AMI 사용하여 EC2 시작 시 OS 설치나 서버 소프트웨어 설정 등을 별도로 할 필요 없음
- AWS 제공 AMI, AWS 마켓플레이스 AMI, AWS 커스텀 AMI
- 운영중인 EC2 인스턴스를 커스텀 AMI로 만들어서 동일한 환경으로 구성된 EC2를 빠르게 시작 가능
