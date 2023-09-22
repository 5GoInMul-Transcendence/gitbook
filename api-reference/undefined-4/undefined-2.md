# 채널 채팅방

{% hint style="info" %}
최근 업데이트 (0912)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>채팅 페이지</p></figcaption></figure>

{% swagger method="get" path="/channel/:channelid/check" baseUrl=" " summary="채널 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="channelid" type="채널 ID" required="true" %}
숫자
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : 
  {
    "mode": "public" | "protected",
    "isBan": true | false
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus":
  {
    "code"   : "0001"
    "message": "채널이 존재하지 않습니다."
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/:channelid/password" baseUrl=" " summary="채널 비밀번호 인증 및 입장" %}
{% swagger-description %}
pubilc일 때와 다르게 protected는 서버에서 채팅방에 유저를 이 때 넣어준다.

이는 서버에 비밀번호를 통해 들어오는 유저가 password 인증을 했을 때 인증된 유저를 따로 저장하지 않기 위해서다. 비밀번호 인증만 하고, 방에 들어오지 않는다 가정한다면 이 때 인증 받은 유저는 메모리 상에 계속 쌓일 것이고, 방에 들어가지 않았기 때문에 지울 방법이 없기 때문이다.

첫 입장 시 서버에서 입장만 시켜주지, 실제로는 GET /channel/:channelid API 를 다시 호출해줘야 한다.
{% endswagger-description %}

{% swagger-parameter in="body" name="password" type="패스워드" required="true" %}
string 4자리(0000~9999)
{% endswagger-parameter %}

{% swagger-parameter required="true" in="path" name="channelid" type="채널 ID" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data" : {
    "id": 123,
    "name": "채널 이름"
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "비밀번호가 일치하지 않습니다!"
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path=" /channel/:channelid" baseUrl=" " summary="채널 입장" %}
{% swagger-description %}
실패 시 차단은 채팅방에서 ban을 의미한다.
{% endswagger-description %}

{% swagger-parameter in="path" name="channelid" type="채널 아이디" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 아이디" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {
    "id": 1,
    "name": '채널 이름',
    "role": "onwer" | "admin" | "user",
    "mode": "public" | "protected" | "private" | "dm",
    "recentMessage": [{
          "id": 1 (message id),
          "content": '최근 메시지',
          "nickname": 'jiyokim',
          "avatar": "/avatar/$(userId)"
    }, ...], 
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "차단(ban)되었습니다."
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/:channelid/chat" baseUrl=" " summary="메시지 보내기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter required="true" in="path" name="channelid" type="채널 ID" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="message" type="메시지" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "1001"
    "message": "채팅 방에 입장한 상태가 아닙니다."
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="delete" path="/channel/:channelid" baseUrl=" " summary="채널 나가기" %}
{% swagger-description %}
채널에 아무도 없으면, 서버에서 삭제해야 한다. All, My 채널 리스트의 웹 소켓으로 없어졌다는 신호를 보내면 프론트는 알아서 없앨 수 있나?
{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="channelid" type="채널 아이디" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "채팅방에 갇혔습니다!!"
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

메시지 받기 (채널리스트, 채널방 메시지)

```json
socket.on('updateMyChannel', (res)=> {  
  { 
    "data" : {
        "id": 1,
        "name": '채널이름',
        "recentMessage": {
          "id": message id,
          "content": '최근 메시지',
          "nickname": 'jiyokim',
          "avatar": "/avatar/$(userId)"
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

<summary><mark style="color:blue;">[08.24]</mark> 업데이트</summary>

## 채널 확인

* env 프로퍼티 명을 mode로 변경
* "채널이 존재하지 않습니다." 메시지 추가

## 채널 비밀번호 인증

* 어떤 유저가 유효한 비밀번호로 인증 되었는지 확인하기 위해 세션 ID가 필요하다.
* 설명 추가

## 채널 입장

* 실패 시 메시지를 구체적으로 변경
* env 프로퍼티 명을 mode로 변경&#x20;
* 설명 추가

## 채널 나가기

* parameter에 channelid 누락 수정
* API resource 오타 수정, channleid => channelid

</details>

<details>

<summary>0903 Update list</summary>

password 가 0, 00, 000, 0000 일 때를 구분하지 못하기 때문에 문자열로 변경한다.

</details>

<details>

<summary>0912 Update list</summary>

* POST /channel/:channelid/password를 protected mode인 채널에 첫 입장 시 호출하면 비밀 번호가 올바를 때 서버 상에서 채널에 입장 시켜준다. 그러나 프론트 상에서는 채널 입장 API 를 다시 호출해줘야 메시지 및 채널 정보를 얻을 수 있다.
* 때문에 비밀번호 인증 때 채널 생성과 같이 채널의 id와 name 만을 보내주도록 변경 되었다.

</details>
