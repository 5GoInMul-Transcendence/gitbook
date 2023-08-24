# 친구 리스트

{% hint style="info" %}
최근 업데이트 ([07.31](undefined-1.md#07.31))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>메인 페이지</p></figcaption></figure>



> REST API

{% swagger method="post" path="/friend" baseUrl=" " summary="친구 추가" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="nickname" required="true" type="닉네임" %}
데이터 범위 : 영문자, 숫자

문자열 길이 : 2이상 12이하
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{
    "id":1,
    "nickname":'donghyuk',
    "avatar":'793506111257096042754805',
    "status":'online'|'offline'|'ingame'
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
```
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "이미 추가된 유저입니다."
  }
}
```

```
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "존재하지 않는 닉네임입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/friend/list" baseUrl=" " summary="친구 리스트 조회" expanded="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
<pre class="language-json"><code class="lang-json"><strong>HTTP/1.1 200 OK
</strong>
{ 
  "data":[{
    "id":1,
    "nickname":'donghyuk',
    "avatar":'793506111257096042754805',
    "status":'online'|'offline'|'ingame'
   }, ...],
  "resStatus":
  {
     "code"   : "0000"
     "message": ""
  }
}
</code></pre>
{% endswagger-response %}
{% endswagger %}



> SOCKET API

### :back: 친구 상태 업데이트 (friend\_update)

```json
socket.on('friend_update', (res)=> {
	"data":{
          "id":1,
          "nickname":'donghyuk2' | undefined
          "avatar":'793506111257096042754805' | undefined
          "status":'online'|'offline'|'ingame' | undefined
        },
        "resStatus":
        {
          "code"   :'0000'
          "message":''
        }
      }	
});
```



> API 업데이트 노트

<details>

<summary>[08.21] 업데이트 내용</summary>

#### <mark style="background-color:yellow;">친구 리스트 조회</mark> (/friend/list)

* URI가 '**/friendlist**'에서 '**/friend/list**'로 변경되었습니다.

</details>

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">친구 추가</mark> (/friend)

* 친구 추가 성공시, 친구 정보를 반환한다.
  * **id** : 유저 식별 값
  * **avatar :** 이미지 식별 값
  * **nickname :** 닉네임
  * **status :** 친구 연결 상태를 나타내며, 'online | offline | ingame' 값을 가진다.

#### <mark style="background-color:yellow;">친구 리스트 조회</mark> (/friendlist)

* 친구 리스트 조회 성공시, 친구 리스트를 배열로 반환된다.

#### <mark style="background-color:yellow;">친구 상태 업데이트</mark>  <mark style="background-color:yellow;">(</mark>friend\_update)

* 친구의 업데이트된 내용을 반환한다. (닉네임, 아바타, 상태 변경시)
* 친구 닉네임이 변경될 경우, **data**는 **id,** **nickname** 값만 담겨온다. (나머지는 undefined)

</details>
