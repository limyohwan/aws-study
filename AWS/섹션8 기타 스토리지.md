# 스토리지 - 기타
### Storage Gateway
- 온프레미스 데이터 센터의 데이터와 AWS 클라우드의 스토리지를 연결하는 서비스
- 하이브리드 클라우드 스토리지로도 부름 (온프레미스 + 클라우드)
- 온프레미스의 데이터를 AWS클라우드로 실시간으로 전송 및 저장 가능
- 온프레미스에 로컬캐시 기능을 통해 자주 사용하는 데이터 보관 가능
- 파일 백업, 클라우드 파일 저장소, 재해 복구 저장소의 용도로 사용
- 온프레미스 스토리지 공간과 관련 비용 절감 효과
- 4가지 유형(S3 파일게이트웨이, FSx 파일게이트웨이, 볼륨게이트웨이, 테이프게이트웨이)

### FSx fro Lustre
- 리눅스 환경을 위한 고성능 병렬 스토리지 시스템
- 병렬 스토리지 시스템 = 분산파일 시스템 (Distributed File System)
- 머신 러닝, 빅데이터 등의 고성능 컴퓨팅에 사용 (High Performance Computing)
- Amazon S3 버킷과 통합 구성하여 같이 사용 가능
- 온프레미스 서버에서 액세스 가능

### FSx for Windows File Server
- FSx for Windows File Server는 윈도우 서버에 구축되는 파일 공유 서비스(EFS는 리눅스 환경)
- SMB 프로토콜을 이용(윈도우, 리눅스에서 액세스 가능)
- 사용자 액세스 제어를 위해 Active Directory(AD) 서비스와 통합 가능
- 온프레미스 서버에서 액세스 가능

### Snow Family
- 데이터를 네트워크가 아닌 물리적인 장치에 저장하여 전송할 수 있는 디바이스
- 온프레미스에 있는 데이터를 AWS로 마이그레이션 해야 할 때 사용
- 제한된 시간안에 마이그레이션, 1회성 마이그레이션 등 제약조건들이 있을 때 사용
- 데이터 전송절차 : 스노우볼 디바이스 요청 -> 주문자에게 디바이스 배송 -> 서버에 연결하여 데이터 복사 -> AWS 데이터센터로 디바이스 배송 -> AWS 데이터센터에서 S3 버킷으로 데이터 복사 -> 스노우볼 데이터 제거
- AWS Snowcone < AWS Snowball < AWS Snowmobile

### AWS DataSync
- 온프레미스와 AWS간 또는 AWS 스토리지 서비스간 데이터 전송 및 복제를 자동화 하는 서비스(데이터 마이그레이션)
- SMB나 NFS를 사용하는 온프레미스 서버의 파일을 AWS의 S3, EFS, FSx for Windows로 전송
- 온프레미스 데이터를 S3, EFS, FSx for Windows File Server로 마이그레이션하거나 S3 Glacier로 아카이빙을 위해 사용
- AWS 서비스 내의 스토리지 내의 데이터 이동을 위해 사용
- 전송 중 및 전송 종료 시 데이터 무결성 확인 및 암호화 가능
- 전송은 시간별, 일별, 주별 등 예약된 일정에 따라 자동으로 이루어짐
- AWS DataSync vs. AWS Snowball Edge
    - AWS DataSync : 온라인으로 데이터 전송하는데 사용
    - Snowball Edge : 오프라인 데이터 전송, 전송대역폭이 제한, 연결이 안정적이지 못한 경우 사용
- AWS DataSync vs. AWS Storage Gateway
    - AWS DataSync : 초기 데이터를 Amazon S3로 마이그레이션
    - AWS Storage Gateway : 초기 마이그레이션 이후 AWS Storage Gateway의 파일 게이트웨이 구성을 사용하여 마이그레이션된 데이터 및 온프레미스 파일 기반 애플리케이션의 지속적인 액세스를 유지

### AWS Backup
- 중앙 집중식 백업 관리 서비스
- 백업 대상 : FSx, EFS, DynamoDB, EC2, EBS, RDS, Aurora, Storage Gateway, VMWare 가상머신
- 백업 일정 관리, 보존관리, 백업 모니터링, 수명주기관리, 액세스 정책, 암호화 등 지원
- 교차리전 백업, 교차계정 백업 지원
- 리소스 태그 기반으로 백업 정책 구성 가능