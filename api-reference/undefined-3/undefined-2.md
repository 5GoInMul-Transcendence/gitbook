# 내 프로필 수정

{% hint style="info" %}
최근 업데이트 ([07.31](undefined-2.md#07.31))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p>내 프로필 수정</p></figcaption></figure>



> REST API

{% swagger method="get" path=" /me/details" baseUrl=" " summary="내 프로필 상세 조회" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" type="" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
```json
HTTP/1.1 200 OK

{ 
  "data":{
    "id":1,
    "nickname": 'donghyuk',
    "avatar": '793506111257096042754805',
    "mail": 'donghyuk@naver.com' | null,
    "phone": '01012345678' | null,
    "twoFactor": 'mail' | 'phone' | 'disabled'
  },
  "resStatus" :
  {
    "code"   : "0000"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/me/nickname" baseUrl=" " summary="닉네임 수정" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="nickname" required="true" type="닉네임" %}
데이터 범위 : 영문자,숫자만 가능

문자열 길이 : 2이상 \~ 12이하
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="cookie" type="세션 ID" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
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

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "이미 사용중인 닉네임입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/me/twofactor" baseUrl=" " summary="twofactor 수정" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="twofactor" required="true" type="2FA" %}
disabled | mail | phone  
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
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

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "잘못된 요청입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/me/image" baseUrl=" " summary="이미지 수정 (향후 수정)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" %}

{% endswagger-parameter %}
{% endswagger %}

{% swagger method="post" path="/auth/mail" baseUrl=" " summary="이메일 인증코드 전송" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="mail" required="true" type="메일" %}

{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
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

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "유효하지 않는 이메일입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path=" /auth/phone" baseUrl=" " summary="핸드폰 인증코드 전송" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="cookie" name="sessionid" required="true" type="세션 ID" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="phone" required="true" type="핸드폰 번호" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="성공" %}
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

{% swagger-response status="200: OK" description="실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "유효하지 않는 핸드폰입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/auth" baseUrl=" " summary="인증코드 확인" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="code" type="인증코드" required="true" %}
 숫자 (0000~9999)
{% endswagger-parameter %}

{% swagger-parameter in="cookie" name="sessionid" type="세션 ID" required="true" %}

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
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "잘못된 인증코드입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[07.31]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">내 프로필 상세 조회</mark> (/me/details)

* '**mail**'과 '**phone**'의 값이 null일 수 있다.
* **'twoFactor'**는 본인이 선택한 2단계 인증(2FA)을 반환한다.

#### <mark style="background-color:yellow;">닉네임 수정</mark> (/me/nickname)

* '**nickname**'은 영문자, 숫자만 가능하며 총 길이는 2이상 12이하이다.

#### <mark style="background-color:yellow;">twofactor 수정</mark> (/me/twofactor)

* **'URI'**에 복합단어가 들어가는 경우 2단어 이하는 모두 소문자로 표기한다. (twofactor)
* **'twoFactor'**는 'mail | phone | disabled' 값 중 하나를 가진다.

#### <mark style="background-color:yellow;">이메일 인증코드 전송</mark>  <mark style="background-color:yellow;">(</mark>/auth/mail)

* 2단계 인증(2FA)을 등록하기 위해 이메일로 인증코드를 전송한다.

#### <mark style="background-color:yellow;">핸드폰 인증코드 전송</mark> (/auth/phone)

* 2단계 인증(2FA)을 등록하기 위해 핸드폰으로  인증코드를 전송한다.

#### <mark style="background-color:yellow;">인증코드 확인</mark> (/auth)

* 인증코드는 4자리 숫자이다. (0000 \~ 9999)

</details>
