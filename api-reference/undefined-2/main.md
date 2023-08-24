# 소켓 연결 (main)

{% hint style="info" %}
최근 업데이트 ([07.31](main.md#07.31))
{% endhint %}



> SOCKET API

### :arrow\_right: 연결 요청

```javascript
const socket = io('http://localhost:10001/main', {
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



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">연결 요청</mark>

*   **Parameters**

    ```
    transports: ['websocket']
    ```

    * 기본 롱폴링 방식에서 웹소켓 방식으로 수정한다.



    ```
    auth: {sessionid: '123456789abcdef'}
    ```

    * 사용자 식별을 위해 '**sessionid**' 전달한다.

#### <mark style="background-color:yellow;">연결 에러</mark> (connect\_error)

* '**sessionid**' 인증 실패시, 에러를 반환한다.

#### <mark style="background-color:yellow;">연결 성공</mark>  <mark style="background-color:yellow;">(</mark>connect)

* 소켓 연결 성공시, 반환한다.

</details>

