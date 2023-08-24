# 채널 리스트

{% hint style="info" %}
최근 업데이트 (8.24)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>채팅 페이지</p></figcaption></figure>



> REST API

{% swagger method="get" path="/channels" baseUrl=" " summary="All 채널 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="성공" %}
```javascript
HTTP/1.1 200 OK

{ 
  "data" : [
    {
      id: 1,
      name: '채널이름',
    } ...,
  ],
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/me/channels" baseUrl=" " summary="My 채널 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```javascript
HTTP/1.1 200 OK

{ 
  "data" : [
    {
        id: 1,
        name: '채널이름',
        recentMessage: {
          nickname: 'jiyokim',
          message: '최근 메시지'
        }
    } ...,
  ],
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

### :back: All 채널 추가

```javascript
socket.on('addAllChannel', (res)=> {  
  { 
    "data" : {
          id: 1,
          name: '채널이름',
    },
    "resStatus" :
    {
      "code"   : "0000"
      "message": ""
    }
  }
});
```

### :back: All 채널 삭제

```javascript
socket.on('deleteAllChannel', (res)=> {  
  { 
    "data": 1,
    "resStatus":
    {
      "code"   : "0000"
      "message": ""
    }
  }
});
```

### :back: My 채널 추가

```javascript
socket.on('addAllChannel', (res)=> {  
  { 
    "data" : {
          id: 1,
          name: '채널이름',
    },
    "resStatus" :
    {
      "code"   : "0000"
      "message": ""
    }
  }
});
```

### :back: My 채널 삭제

```javascript
socket.on('deleteAllChannel', (res)=> {  
  { 
    "data": 1,
    "resStatus":
    {
      "code"   : "0000"
      "message": ""
    }
  }
});
```

### :back: My 채널 업데이트

```javascript
socket.on('updateMyChannel', (res)=> {  
  { 
    "data" : {
        id: 1,
        name: '채널이름',
        recentMessage: {
          id: 1,
          nickname: 'jiyokim',
          content: '최근 메시지'
        },
      },
    ],
    "resStatus" :
    {
      "code"   : "0000"
      "message": ""
    }
  }
});
```

<details>

<summary><mark style="color:blue;">[08.24]</mark> 업데이트 내용</summary>

## My channel 조회

* 세션 ID 가 필요하므로 파라미터에 추가함

</details>
