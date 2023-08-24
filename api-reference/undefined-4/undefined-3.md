# 채널 채팅방

{% hint style="info" %}
최근 업데이트 (8.24)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>채팅 페이지</p></figcaption></figure>

{% swagger method="get" path="/channel/:channelid/check" baseUrl=" " summary="채널 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="channelid" type="채널 ID" required="true" %}
숫자
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-typescript"><code class="lang-typescript"><strong>HTTP/1.1 200 OK
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
  "resStatus":
  {
    "code"   : "0001"
    "message": "채널이 존재하지 않습니다."
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/:channelid/password" baseUrl=" " summary="채널 비밀번호 인증" %}
{% swagger-description %}
서버에서는 채팅방에 유저를 넣어준다.
{% endswagger-description %}

{% swagger-parameter in="body" name="password" type="패스워드" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter required="true" in="path" name="channelid" type="채널 ID" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

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
    "env": "public" | "protected" | "private" | "dm",
    "recentMessage": [{
          id: 1,
          nickname: 'jiyokim',
          content: '최근 메시지',
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

{% swagger method="delete" path="/channel/:channleid" baseUrl=" " summary="채널 나가기" %}
{% swagger-description %}
채널에 아무도 없으면 채널 삭제
{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" required="true" %}

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

<summary><mark style="color:blue;">[08.24]</mark> 업데이트</summary>

## 채널 확인

* env 프로퍼티 명을 mode로 변경
* "채널이 존재하지 않습니다." 메시지 추가

## 채널 비밀번호 인증

* 어떤 유저가 유효한 비밀번호로 인증 되었는지 확인하기 위해 세션 ID가 필요하다.
* 설명 추가

## 채널 입장

* 실패 시 메시지를 구체적으로 변경
* 설명 추가

</details>
