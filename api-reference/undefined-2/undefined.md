# 마이 프로필

{% hint style="info" %}
최근 업데이트 ([07.31](undefined.md#07.31))&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>메인 페이지</p></figcaption></figure>



> REST API

{% swagger method="get" path="/me" baseUrl=" " summary="마이 프로필 조회" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data":{
    "id":1,
    "nickname": 'donghyuk',
    "avatar": '793506111257096042754805',
    "gameRecord":"{
      "win":10
      "loss":10
      "ladderLevel":10
      "achievement":['10연승'] | null
    }"
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



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">마이 프로필 조회</mark> (/me)

* 간단한 유저 정보를 조회한다.
* **이메일**과 **핸드폰 번호**는 포함되지 않는다.

</details>
