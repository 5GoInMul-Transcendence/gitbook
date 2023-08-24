# 인증코드 확인



{% hint style="info" %}
**최근 업데이트** ([07.31](undefined.md#07.31))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>인증 페이지</p></figcaption></figure>



> REST API

{% swagger expanded="false" method="post" path="/auth" baseUrl=" " summary="인증코드 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="code" type="인증코드" required="true" %}
 숫자 (0000~9999)
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="인증 성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="인증 실패" %}
```javascript
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "인증코드가 일치하지 않습니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">인증코드 확인</mark> (/auth)

* 인증코드는 4자리 숫자이다. (0000 \~ 9999)

</details>
