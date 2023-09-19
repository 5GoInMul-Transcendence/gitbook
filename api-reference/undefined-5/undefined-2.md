# 채널 유저 설정

{% hint style="info" %}
최근 업데이트 (8.17)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>채널 유저 설정 모달</p></figcaption></figure>

{% swagger method="get" path="/channel/setting/:channelid/:userid" baseUrl=" " summary="채널 유저 설정 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {
    "admin": true | false,
    "mute": true | false,
    "ban": true | false
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
    "message": "채널 유저 설정 조회를 할 수 없습니다!"
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/channel/setting/:channelid/user" baseUrl=" " summary="채널 유저 설정 수정" %}
{% swagger-description %}
 
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="유저 아이디" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="status" type="변경될 상태" required="true" %}
"admin" | "mute" | "ban" | "kink"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="sessionid" type="세션 ID" required="true" %}

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
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : '',
  "resStatus" :
  {
    "code"   : "0001"
    "message": "설정 변경을 할 수 없습니다!"
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}
