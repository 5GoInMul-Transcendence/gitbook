# 게임 히스토리

{% swagger method="get" path="/history/:nickname" baseUrl=" " summary="게임 히스토리 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="nickname" type="닉네임" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data": [
    {
      "gameId": number;
      "createdDate": string;
      "player1": {
        "nickname": string;
        "avatar": string;
        "score": number;
      };
      "player2": {
        "nickname": string;
        "score": number;
        "avatar": string;
      };
    }
  ],
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}

