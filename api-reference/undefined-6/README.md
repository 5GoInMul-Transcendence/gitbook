# 게임 페이지

### 요청 방식

```javascript
socket.emit(event, ...args, (res) => {} );
```

* event : 요청한 이벤트&#x20;
* args   : 요청에 필요한 데이터
* res     : 요청 후 서버의 응답 데이터를 처리할 콜백함수

응답 데이터 (res)

```javascript
res: {
  "data": {},
  "resStatus" :
  {
    "code"   : "0000" | "0001" (성공 | 실패)
    "message": ""
  }
}
```



