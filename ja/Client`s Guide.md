## Upcoming Products > RTCS > Client`s Guide
socket.io의 기본 이벤트 메세지와 RTCS 전용 메세지에 대한 내용을 설명한다.

## Socket.io 기본 이벤트
socket.io메세지 설명은 JS를 기준으로 한다 나머지 클라이언트 라이브러리도 사용법은 대동 소이하다. 메시지는 문자열과 JSON 타입 지원하며 문자셋은 UTF-8로 고정되어 있다.

### 접속
서버로 부터 접속 URL을 받아 아래와 같이 세팅한다.
```
socket = io.connect("{url}")
```

### 접속 이벤트
```
socket.on("connect", function() {
      // 접속시 처리할 작업
});
```

### 종료 이벤트
```
socket.on("disconnect", function(reason) {
      // 종료시 처리할 작업
});
```

### 에러 이벤트
```
socket.on("error", function(reason) {
      // 종료시 처리할 작업
});
```

### 사용자 정의 이벤트
```
socket.on("event_name", function(data) {
      // data 처리
 });
```

## RTCS전용 메세지
### 채널 가입/탈퇴
채널에 대한 가입/탈퇴는 `rtcs:channel` 이벤트를 사용한다.

### 채널 가입 요청
```
var message = {
      command : "subscribe",
      name : "channel_name"
};
socket.emit("rtcs:channel", message);
```



### 채널 탈퇴 요청
```
var message = {
      command : "unsubscribe",
      name : "channel_name"
};
socket.emit("rtcs:channel", message);
```

### 채널 가입/탈퇴에 대한 결과
```
socket.on("rtcs:channel", function(data) {
        // data 내용에 따른 처리
});
```

### 결과 데이터
* rtcs:channel 이벤트에 대한 데이터는 JSON 형태로 반환된다.
```
가입 성공 - {"type":"subscribe_success", "name":"channel_name", "message":"success_message"}
가입 실패 - {"type":"subscribe_error", "name":"channel_name", "message":"error_message"}
탈퇴 성공 - {"type":"unsubscribe_success", "name":"channel_name", "message":"success_message"}
탈퇴 실패 - {"type":"unsubscribe_error", "name":"channel_name", "message":"error_message"}
```
* 특히 채널명이 "presence_" 로 시작하면 채널 가입/탈퇴에 대한 이벤트가 같은 채널에 속한 사용자들간에 공유된다.
```
가입 - {"type":"member_join", "name":"channel_name", "message":"", "info":{"session":"session_id", "user":"user_data"}}
탈퇴 - {"type":"member_leave", "name":"channel_name", "message":"", "info":{"session":"session_id", "user":"user_data"}}
```
