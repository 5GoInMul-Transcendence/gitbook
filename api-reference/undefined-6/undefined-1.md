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
    gametype: 'classic' | 'paddle' | 'speed',
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
	gameKey: 'key'
  }
});
```

### 게임 준비

```
socket.emit('readyGame', ());
```

<details>

<summary>게임 준비</summary>

* p1이 게임을 시작할 수 있게 게임 준비 요청을 받는 소켓
* p1에게 startButton 을 띄우고 버튼을 누르게함
* p1,p2 에게 모두 standby 상태를 보내주기 위함&#x20;

</details>

### 게임 상태 정보 &#x20;

```javascript
socket.on('infoGame', (res) => {
  status: standby | play | end
});
```

<details>

<summary>게임 상태 정보  </summary>

* 게임 상태를 받는 소켓
* standby
  * 게임이 준비되었음을 알려주는 변수
  * 3초 카운트를 띄우고 게임이 시작할 수 있도록 socket.emit('startGame')보ㅁ
* end
  * 게임이 종료 되었음을 알려주는 변수

</details>

### 게임 시작

```javascript
socket.emit('startGame');
```

<details>

<summary>게임 시작</summary>

* 게임 카운트가 끝났다고 알려주는 소켓

</details>

### 게임 패들 업데이트

```javascript
socket.emit('updatePaddle', {
        paddle: keyDown | keyUp,
    }
})
```

<details>

<summary>게임 패들 업데이트</summary>

* 패들이 이동함을 전달하는 소켓

</details>

### 게임 오브젝트 업데이트

```javascript
socket.on('updateObject', (res) => {
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
})
```

<details>

<summary>게임 오브젝트 업데이트</summary>

* 게임 오브젝트에 대한 데이터를 보내주는 소켓

</details>

### 게임 스코어 업데이트

```javascript
socket.on('updateSocre', (res) => {
	p1 { 
		score: ,
	} ,
	p2 {
		score: ,
	} ,
	winner: p1 | p2,
})
```

<details>

<summary>게임 스코어 업데이트</summary>

* 게임 스코어가 변경되었음을 알려주는 소켓

</details>



<details>

<summary>[09.04] 업데이트</summary>

게임 응답 데이터 포맷이 변경되었습니다.&#x20;

```javascript
data {p1, p2} -> {p1, p2}
```

* 랩핑 비용과 네트워크 비용을 줄여 게임 성능을 높이기 위해 data랩핑을 제거하였습니다.

</details>
