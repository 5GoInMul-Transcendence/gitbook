# 소켓 연결 (chat)

{% hint style="info" %}
최근 업데이트 (8.14)
{% endhint %}



> SOCKET API

### :arrow\_right: 연결 요청

```javascript
const socket = io('http://localhost:10002/chat', {
  transports: ['websocket'],
  extraHeaders:{
    cookie: 'sessionid=0123456789abcdef'
  }
});
```

### :back: 연결 에러 (connect\_error)

```javascript
socket.on('connect_error', (err)=> {
	console.log(err.message); // 인증 실패
});
```

### :back: 연결 성공 (connect)

```
socket.on('connect', ()=> {
 // 연결 성공 
});
```
