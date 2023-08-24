# 게임

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>게임 페이지</p></figcaption></figure>



> REST API

{% swagger method="get" path="/game" baseUrl=" " summary="게임 정보 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionId" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```javascript
HTTP/1.1 200 OK

{ 
  "data":{
    p1: {
     id: 1,
     nickname:
     avatar:
    },
    p2: {
     id: 2
     nickname:
     avatar:
    },
    gamekey: ,
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}



> SOCKET API

### 소켓 연결

```jsx
const socket = io('http://localhost:10003/game', {
  transports: ['websocket'],
  auth: {
	gamekey: 'key'
  }
});
```

### 게임 준비

```
socket.emit('readyGame', ());
```



### 게임 상태 정보 &#x20;

```javascript
socket.on('infoGame', (res) => {
  status: standby | play | end
});
```



### 게임 시작

```javascript
socket.emit('startGame');
```



### 게임 패들 업데이트

```javascript
socket.emit('updatePaddle', (res) => {
	data:{
		x: ,
		y:
	}
})
```

###

### 게임 오브젝트 업데이트

```javascript
socket.on('updateObject', (res) => {
	"data":{
		p1: {
			x: ,
			y: ,
		},
		p2: {
			x: ,
			y: ,
		},
		b: {
			x: ,
			y:
		}
	},
})
```



### 게임 스코어 업데이트

```javascript
socket.on('updateSocre', (res) => {
	"data":{
		p1 { 
			score: ,
		} ,
		p2 {
			score: ,
		} ,
		winner: p1 | p2,
	},
})
```

