# 채널 만들기

{% hint style="info" %}
최근 업데이트 (8.24)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>채널 생성창</p></figcaption></figure>



{% swagger method="post" path="/channel" baseUrl=" " summary="채널 만들기" %}
{% swagger-description %}
 채팅방 생성 후 바로 입장 처리
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="true" type="채널 이름" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="mode" required="true" type="방 설정" %}
'public' 'protected' | 'private'
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="비밀번호" required="false" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션 ID" required="true" %}

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

<details>

<summary><mark style="color:blue;">[08.24]</mark> 업데이트 내용</summary>

## 채널 만들기

* sessionid가 필요하므로 추가
* env 프로퍼티 명을 mode로 변경&#x20;

</details>
