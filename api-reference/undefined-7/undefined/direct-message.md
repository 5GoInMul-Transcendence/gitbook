# \*삭제\*(채널 만들기에 합병)Direct message 보내기

{% hint style="info" %}
최근 업데이트 (0903)
{% endhint %}

{% swagger method="post" path="/channel/private" baseUrl=" " summary="채널 만들기" %}
{% swagger-description %}
&#x20;채팅방 생성 후 바로 입장 처리

기존에 존재하는 채팅방이면 기존 것을 띄우기
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="false" type="채널 이름" %}
DM은 "닉네임1, 닉네임2, ..."으로 한다.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="sessionid" type="세션  ID" required="true" %}

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

<summary><mark style="color:blue;">[07.26]</mark> 업데이트 내용</summary>

* POST /channel/private에서 sessionid가 필요하므로 추가함

</details>

<details>

<summary>0903 Update list</summary>

* 삭제

</details>
