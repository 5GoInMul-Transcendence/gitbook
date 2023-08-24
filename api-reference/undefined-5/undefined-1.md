# 채널 설정

{% hint style="info" %}
최근 업데이트 (8.17)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>채널 설정창</p></figcaption></figure>

{% swagger method="put" path="/channel/setting/:channelid" baseUrl=" " summary="채널 설정 수정" %}
{% swagger-description %}
소켓으로 채널 리스트 env 업데이트
{% endswagger-description %}

{% swagger-parameter in="body" name="env" required="true" type="방 설정" %}
protected | public
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="비밀번호" required="false" %}

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

