# 채널 만들기

{% hint style="info" %}
최근 업데이트 (0910)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>채널 생성창</p></figcaption></figure>

{% swagger method="post" path="/channel/public" baseUrl="server" summary="public 채널 만들기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 id" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="채널 이름" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
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
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/protected" baseUrl="server" summary="protected 채널 만들기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세선 id" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="채널 이름" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="비밀번호" required="true" %}
4자리
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
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
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/private" baseUrl="server" summary="private 채널 만들기" %}
{% swagger-description %}
자신의 이름이 채널 이름이 된다.
{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 id" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
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
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/channel/dm" baseUrl="server" summary="DM 채널 만들기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 id" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="invitedUserid" type="유저 id" required="true" %}
초대 받는 유저의 id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
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
</code></pre>
{% endswagger-response %}
{% endswagger %}

<details>

<summary><mark style="color:blue;">[08.24]</mark> 업데이트 내용</summary>

## 채널 만들기

* sessionid가 필요하므로 추가
* env 프로퍼티 명을 mode로 변경&#x20;

</details>

<details>

<summary>[09.03] 업데이트</summary>

* password 가 0, 00, 000, 0000 일 때를 구분하지 못하기 때문에 문자열로 변경한다
* mode에 'dm' 추가
* 비밀번호가 존재하지 않을 시 null 명시적으로 넣어주기

</details>

<details>

<summary>[0909] Update list</summary>

* Add property of invitedUserId in POST /channel body

</details>

<details>

<summary>[0910] Update list</summary>

* channel mode 인 public, protected, private, dm 각각의 상황이 매우 다양하다. 때문에 하나의 API 에서 처리하기에 어렵다. 그래서 기존 하나의 생성에서 모드마다 생성 API 를 만들어 나누었다.
* private 채널 생성 시도 시 기존에 이미 만들어져 있으면 해당 채널 id 와 name 을 보냄
* DM 채널 생성 시도 시 자신과 초대 받을 유저가 입장한 DM 채널이 존재할 시 해당 채널 id 와 name 을 보냄

</details>

## 삭제 예정 API

***

{% swagger method="post" path="/channel" baseUrl=" " summary="(삭제 예정)채널 만들기" expanded="false" %}
{% swagger-description %}
 채팅방 생성 후 바로 입장 처리
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="true" type="채널 이름" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="mode" required="true" type="방 설정" %}
'public' | 'protected' | 'private' | 'dm'
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="비밀번호" required="true" %}
문자열 4자리(0000~9999), 없으면 null 명시하기
{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="invitedUserId" type="유저 아이디" required="true" %}
초대 받을 유저의 id, 숫자, 없으면 null
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>HTTP/1.1 200 OK
</strong>
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
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : '',
  "resStatus" :
  {
    "code"   : "0001"
    "message": "방을 생성할 수 없습니다."
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/channel/private/check" baseUrl="server" summary="(삭제 예정)private 채널 생성 유무 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 id" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="create channel" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : "create",
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="enter channel" %}
```json
HTTP/1.1 200 OK

{ 
  "data" : "enter",
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/channel/dm/check" baseUrl="server" summary="(삭제 예정)DM 채널 생성 유무 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 id" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="invitedUserId" type="유저 id" required="true" %}
초대 받는 유저의 id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="create channel" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : "create",
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}

{% swagger-response status="200: OK" description="enter channel" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : "enter",
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}
