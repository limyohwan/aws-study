# 애플리케이션 통합
### Simple Queue Service(SQS)
- Queue는 대기한다는 의미
- SQS는 메시지를 대기하는 기능
- 애플리케이션 간에 느슨한 결합 제공(decoupling)
- SQS는 Poll 방식으로 메시지를 전송(Consumer가 메시지를 요청하여 받는 방식)
- Consumer가 메시지를 소비하면 SQS Queue에서는 메시지가 삭제됨

### SQS 표준 대기열 vs FIFO 대기열
|표준 대기열|FIFO 대기열|
|:---:|:---:|
|일반적인 대기열 방식|메시지가 들어온 순서대로 처리|
|순서와 상관없이 메시지 전달||
|가끔 2개 이상의 중복 메시지가 전달될 수 있음|중복메시지 전달이 없음|
|처리 순서와 상관없는 애플리케이션에 사용|처리 순서가 중요한 애플리케이션에 사용|
|순서가 없는 파일업로드, 순서가 없는 데이터베이스 항목 추가 등|쇼핑몰 주문 시 결제처리 후 배송 처리 등|

### Simple Notification Service(SNS)
- 메시지 전송 서비스
- 게시자(Publishers)에서 구독자(Subscriber, 생산자 및 소비자라고도 함)로 메시지를 전송
- 애플리케이션 간(A2A) 및 애플리케이션과 사용자 간(A2P) 통신
- SNS는 Push 방식으로 메시지를 전송(Subscriber에게 메시지를 보내는 방식)
- 전송순서
    1. SNS에서 주제(Topic) 생성
    2. 구독 생성(메시지를 받는 사람) 
    3. 메시지 생성
    4. 구독자에게 메시지 전달

### Kinesis
- 실시간 스트리밍 데이터를 손쉽게 수집, 처리 및 분석하는 서비스
- 비디오, 오디오, 애플리케이션 로그, 웹 사이트 클릭스트림 및 IoT 텔레메트리 데이터와 같은 실시간 데이터를 수집
- 데이터가 수집된 후에 처리를 시작할 수 있는 것이 아니라 데이터가 수신되는 대로 처리 및 분석
- Kinesis 서비스 유형
    - Kinesis Data Streams : 데이터 스트림을 수집, 저장 및 처리
    - Kinesis Data Firehose : 데이터 스트림을 AWS 데이터 스토어에 로드
    - Kinesis Data Analytics : SQL 또는 Apache Flink로 데이터 스트림 분석
    - Kinesis Video Streams : 비디오 스트림을 수집, 저장 및 처리

### API Gateway
- 개발자가 API를 생성, 게시, 유지관리, 모니터링 및 보안유지를 할 수 있게하는 서비스
- RESTful API 및 WebSocket API를 지원
- 애플리케이션이 API를 통해 백엔드 시스템 및 데이터에 액세스하여 통신