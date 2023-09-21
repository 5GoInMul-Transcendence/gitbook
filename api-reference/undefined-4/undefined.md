# 채널 리스트

{% hint style="info" %}
최근 업데이트 (0903)
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

{% swagger method="get" path="/channels/mine" baseUrl=" " summary="My 채널 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data" : [
    {
        "id": channel id(number),
        "name": '채널이름',
        "recentMessage": {
          "id": message id(number), If message is empty, it is -1(number),
          "nickname": 'jiyokim' | '',
          "content": '최근 메시지' | '',
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
    "data": {
      "id": 1,
    },
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
socket.on('addMyChannel', (res)=> {  
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
socket.on('deleteMyChannel', (res)=> {  
  { 
    "data": {
      id: 1,
    },
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

<details>

<summary>0903 Update list</summary>

* 채널 가져오기 리소스 명을 /me/channels 에서 /channels/mine 으로 변경했다.
* 이후에 유지보수 하기가 어려워질 것이다. /me 로 하면 채널이 있던 디렉토리가 아니라 아예 다른 디렉토리에서 개발하게 되어서 과도한 import 가 되고, 한 번에 채팅 관련 프로그램을 개발할 수 없다는 단점이 있다.

<!---->

* 게임 파트는 모든 기능을 하나의 애플리케이션에 담는 고전적인 monolithic 방법이 아닌 micro service 로 게임만 다른 애플리케이션으로 나누었는데 다음에 채팅도 성능 이슈 때문에 나눠야 할 때면 하나의 디렉토리에 있는 게 관리하기 편할 것이다.

<!---->

* /channels/mine, /channels/me, /channels/my 등을 고민했으나 RESTful 한 API 리소스 명은 명사로 해야 한다는 점 등을 고려하여 mine 으로 할 예정이다.
* 채널을 처음 생성했을 때는 recentMessage 는 없을 것이므로 recentMessage 의 프로퍼티인 nickname 과 message 는 null 을 가진다.

</details>
