## Upcoming Products > RTCS > Developer's Guide
RTCS를 사용하기 위해 필요한 기본 지식과 API에 대해 설명한다.

## 채널
메세지를 수신하기 위한 기본 단위이다. 같은 채널에 가입되어있는 클라이언트들과 메세지를 공유한다. 클라이언트 별로 다른 메세지를 전달해야한다면 전용 채널을 생성하면 된다. 기본적으로 메세지를 받으려면 RTCS와 연결이 완료된 후 채널에 가입을 진행해야한다. 채널의 종류는 아래와 같다.

### 채널 명규칙
채널 명은 RTCS내부에서 사용하는 prefix 채널과 사용자가 임의로 만들어서 사용하는 공개 채널이 있다. 채널명을 작성할 때는 아래의 조건에 맞아야한다.
* `영문`, `숫자`, `_` 와  `-` 만 허용한다.
* `200 byte`의 길이만 허용한다.
* `private_`, `presence_`, `member_` 로 시작하는 공개 채널은 생성할 수 없다.

채널의 종류는 아래와 같다.

### 공개 채널
인증과정이 없어 누구나 가입이 가능한다. `private_`, `presence_`, `member_` 로 시작하는 채널명은 만들 수 없다.

### 비공개 채널
가입을 위해서는 연결 URL을 요청할때 선 가입을 시켜주거나, 추후 가입시에 인증이 필요하다. 채널명은 `private_`로 시작한다.

### 멤버 채널
가입을 위해서는 연결 URL을 요청할때 선 가입을 시켜주거나, 추후 가입시에 인증이 필요하다. 채널명은 `member_`로 시작한다. 가입자를 아래와 같은 내용으로 조회가 가능하다
```
{세션아이디:사용자정보}
```

### 출석 채널
가입을 위해서는 연결 URL을 요청할때 선 가입을 시켜주거나, 추후 가입시에 인증이 필요하다. 채널명은 `presence_`로 시작한다. 채널에 가입과 탈퇴하는 회원의 정보를 채널 가입들에게 broadcast를 해준다. 가입자 정보를 아래와 같은 내용으로 조회가 가능한다.
```
{세션아이디:사용자정보}
```

## 인증

## Webhook
클라이언트에서 밣생하는 이벤트를 서비스 서버로 전달할때 사용한다. Http의 post로 요청이 전달되고 body는 Json형태 이다. Hook은 기본 시간 동안(`1000ms`) 전송 시도 후 성공/실패에 상관없이 완료되며, 실패 하더라도 재전송 되지 않는다.

### 클라이언트 접속
클라이언트가 접속 했을 때 Hook이 발생한다. 지정한 Hook URL로 아래와 같은 데이터가 전송된다. `user`키에 데이터는 접속 URL을 요청했을 때 전달해준 user 데이터이다.
* type : `connect`
* app : 토스트 클라우드의 `AppID`
* session : RTCS에서 사용하는 클라이언트 단위의 ID
* hook data
```
{
    "time" : "milliseconds",
    "type" : "connect",
    "app" : "app_id",
    "user" : "user_id",
    "session" : "session_id",
    "detail" : {
       "origin":"http://service"
     }
}
```

### 클라이언트 종료
클라이언트가 종료 했을 때 Hook이 발생한다. 지정한 Hook URL로 아래와 같은 데이터가 전송된다. `user`키에 데이터는 접속 URL을 요청했을 때 전달해준 user 데이터이다.
```
{
    "time" : "milliseconds",
    "type" : "connect",
    "app" : "app_id",
    "user" : "user_id",
    "session" : "session_id",
    "detail" : {
       "origin":"http://service"
     }
}
```
### 채널 가입
클라이언트에서 채널을 가입했을 때 Hook이 발생된다. 지정한 Hook URL로 아래와 같은 데이터가 전송된다. `user`키에 데이터는 접속 URL을 요청했을 때 전달해준 user 데이터이다.
```
{
    "time":"1352770998419",
    "type":"subscribe",
    "app":"app_id",
    "user":"user_id",
    "session":"session_id",
    "detail":{
       "channel":"channel_name"
     }
}
```
### 채널 탈퇴
클라이언트에서 채널을 탈퇴했을 때 Hook이 발생된다. 지정한 Hook URL로 아래와 같은 데이터가 전송된다. `user`키에 데이터는 접속 URL을 요청했을 때 전달해준 user 데이터이다.
```
{
    "time":"1352770998419",
    "type":"unsubscribe",
    "app":"app_id",
    "user":"user_id",
    "session":"session_id",
    "detail":{
       "channel":"channel_name"
     }
}
```
## Service API  
RTCS에서 제공하는 Restfull API에 대한 설명이다. API종류는 접속 권한 요청, 채널 메시지 전달 요청, 채널 존재 여부 확인 등의 기능을 제공한다. 기본 API URL은 아래와 같다.

|기본 도메인|
|---|
|https://api-gw.cloud.toast.com/tc-pusher/|

### 접속 권한 요청

### 채널 메시지 전달 요청

### 채널 존재 여부 확인

### 채널에 가입된 세션 정보 조회

### 채널에 가입된 세션 개수 조회
