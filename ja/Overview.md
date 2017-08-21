## Upcoming Products > RTCS > Overview
RTCS는 쉽고 빠르게 Web, 모바일 앱, 데스크탑 어플리케이션과 같은 다양한 디바이스를 실시간으로 연결시켜주고 메세지를 주고 받을 수 있게 해주는 서비스이다. RTCS를 이용해서 실시간 협업툴, 멀티플레이어 게임, 채팅, 리얼타임 대시보드와 같은 기능을 다양한 디바이스에서 쉽게 구현 가능하다.

## 주요기능
### 실시간 메세지 전송
서버에서 Rest API를 이용하여 클라이언트에 메세지를 push할 수 있다. 클라이언트에서 서비스 서버로 메세지 전달을 요청하면 서버가 RTCS서버에게 전달을 하고 가입된 채널 맴버들에게 메세지를 전달한다.

### 클라이언트 접근 인증
클라이언트가 RTCS에 접근을 하려고 할때 별도의 인증을 받는다. 사용자가 접근을 요청하면 서비스 서버가 RTCS서버에 접근 URL을 요청을 하고 해당 URL을 이용하여 클라이언트가 RTCS서버에 접근 허가를 받는다. 필요하다면 서비스 서버와의 추가 인증 절차를 통하여 접근허가를 추가 할 수있다.

### 클라이언트 이벤트 Hook 기능
클라이언트의 상태에 따라 서비스 서버로 Hook을 전달 한다 전달되는 이벤트의 종류는 아래와 같다
* 접근 인증요청
* 연결 완료
* 연결 종료
* 채널 가입
* 채널 탈퇴

### 채널단위 관리
RTCS가 메세지를 broadcast하는 단위는 채널이다. 메세지 전달 요청을 하면 같은 채널에 있는 디바이스에 메세지를 전달한다. 용도별로 다른 메세지를 전달 해야한다면 용도별 채널을 생성해야한다. 또 디바이스별/사용자별 메세지 전달이 필요하다면 전용 채널을 생성 해야한다.

### 메세지/사용자 지표 제공
RTCS를 통해 접속한 사용자, 메세지의 양 등의 통계자료를 지표로 제공한다. 또 현재 접속중인 사용자의 수도 실시간으로 제공한다.

## 클라이언트 지원
> Socket.io 0.9, 1.x기반의 플랫폼 서비스이다.

클라이언트는 Javascript는 socket.io 0.9 기반, 나머지 native client들은 아래 socket.io 1.x버젼용 client library를 사용하면된다.

### client libraries
- Javascript
  - socket.io 0.9
  - [https://cdnjs.com/libraries/socket.io/0.9.17](https://cdnjs.com/libraries/socket.io/0.9.17)
- Java
	- socket.io 1.x
  - maven
  ```
  <dependencies>
    <dependency>
      <groupId>io.socket</groupId>
      <artifactId>socket.io-client</artifactId>
      <version>1.0.0</version>
    </dependency>
  </dependencies>
  ```
  - Gradle
  ```
  compile ('io.socket:socket.io-client:1.0.0') {
    // excluding org.json which is provided by Android
    exclude group: 'org.json', module: 'json'
  }
  ```
- Swift
  - socket.io 1.x
  - [https://github.com/socketio/socket.io-client-swift/releases/tag/v9.0.1](https://github.com/socketio/socket.io-client-swift/releases/tag/v9.0.1)

- Cpp
  - socket.io 1.x
  - [https://github.com/socketio/socket.io-client-cpp/releases/tag/1.6.1](https://github.com/socketio/socket.io-client-cpp/releases/tag/1.6.1)

- Unity3D
  - socket.io 1.x
  - [https://github.com/nhnent/socket.io-client-unity3d](https://github.com/nhnent/socket.io-client-unity3d)
