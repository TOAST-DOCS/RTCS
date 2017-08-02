## Upcoming Products > RTCS > Getting Started
## 서비스 신청 방법
아직 콘솔 개발이 완료되지 않아 아래 내용을 채워 `support@cloud.toast.com`으로 메일을 보내주세요

### 서비스 신청 필요한 자료
* appkey
* SSL 사용 여부
* WebAuth URL
* Hook URL
* 전달 받을 hook event
  * 연결 완료
  * 연결 종료
  * 채널 가입
  * 채널 탈퇴

### 예제
```
* appkey : abcdefg
* SSL 사용 여부 : 불필요
* WebAuth URL : http://api.service.com/auth
* Hook URL : http://api.service.com/hook
* 전달 받을 hook event
  * 연결 완료 : 필요
  * 연결 종료 : 필요
  * 채널 가입 : 불필요
  * 채널 탈퇴 : 불필요
```  
