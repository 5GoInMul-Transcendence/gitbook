# 상대방 프로필

{% hint style="info" %}
최근 업데이트 ([07.31](undefined-1.md#07.31))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>상대방 프로필</p></figcaption></figure>



> REST API

{% swagger method="get" path="/user/:nickname" baseUrl=" " summary="상대방 프로필 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter type="닉네임" in="path" name="nickname" required="true" %}
데이터 범위 : 영문자, 숫자

문자열 길이 : 2이상 12이하
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data":{
    "id":1,
    "nickname": 'donghyuk',
    "avatar": '793506111257096042754805',
    "gameRecord":"{
      "win":10
      "loss":10
      "ladderLevel":10
      "achievement":['10연승'] | []
    }"
    "isFriend": true|false,
    "isBlock" : true|false,
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data":{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "존재하지 않은 유저입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/user/:nickname/block" baseUrl=" " summary="상대방 차단" %}
{% swagger-description %}
채널 삭제에 대한 소켓 로직과 같음
{% endswagger-description %}

{% swagger-parameter type="닉네임" in="path" name="nickname" required="true" %}
데이터 범위 : 영문자, 숫자

문자열 길이 : 2이상 12이하
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data":{
    "id":1,
    "nickname": 'donghyuk',
    "avatar": '793506111257096042754805',
    "isFriend": true|false,
    "isBlock" : true|false,
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data":{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "존재하지 않은 유저입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">상대방 프로필 조회</mark> (/user/{nickname})

* 상대방 프로필 정보를 조회한다.
  * **id** : 사용자 식별 값
  * **nickname** : 닉네임
  * **avatar** : 이미지 식별 값
  * **gameRecord** : 상대방 게임 정보
  * **gameRecord.win** : 승수
  * **gameRecord.loss** : 패수
  * **gameRecord.ladderLevel** : 래더 레벨
  * **gameRecord.achievement** : 래더 업적들
  * **isFriend** : 친구 여부
  * **isBlock** : 차단 여부

</details>
