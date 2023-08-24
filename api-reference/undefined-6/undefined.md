---
description: 지
---

# 매치 페이지

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>매치 페이지</p></figcaption></figure>

> SOCKET API

### 매치 등록

```javascript
socket.emit('submitMatch', {
    gametype: classic | paddle | speed
}, (res) => {});
```



### 매치 취소

```jsx
socket.emit('cancleMatch', (res) => {});
```



### 매치 알림

```jsx
socket.on('waitMatch', ());
```



### 매치 성사

```javascript
socket.on('successMatch', {
	status: true | false ,
})
```



