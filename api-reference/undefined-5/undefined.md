# 채널 정보

{% hint style="info" %}
최근 업데이트 (8.17)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

{% swagger method="get" path="/chnnel/setting/:channelid/" baseUrl=" " summary="채널 정보 가져오기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter required="true" in="path" name="channelid" type="채널 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data" : {
    [
      {
        "id": 1,
        "nickname": "jayoon",
        "avatar": adsf,
        "role": "onwer" | "admin" | "user",
      },
      ...
    ]
  }
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
    "message": "채팅방 정보를 불러 올 수 없습니다!"
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}

Pong 게임 초대에 대한 건 게임 팀에 맞춰 설계하기
