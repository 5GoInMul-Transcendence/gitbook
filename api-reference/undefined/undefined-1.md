# 로그인

{% hint style="info" %}
**최근 업데이트** ([08.08](undefined-1.md#08.08))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption><p>로그인 페이지</p></figcaption></figure>



> REST API

{% swagger method="post" path="/login" baseUrl=" " summary="로그인 (ID/PW)" expanded="false" fullWidth="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" required="true" type="아이디" %}
데이터 범위 : 영문자,숫자만 가능

문자열 길이 : 2이상 \~ 12이하
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" type="패스워드" %}
데이터 범위 : 아스키 코드만 가능

문자열 길이 : 8이상 \~ 15이하
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="로그인 실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "아이디/패스워드가 일치하지 않습니다."
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="로그인 성공 : 2FA 비활성화시, 메인 페이지 이동" %}
```json
HTTP/1.1 200 OK

Set-Cookie : session=abcdef1234567890
...

{ 
  "data" : '/main',
  "resStatus" :
  {
    "code"   : "0002"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="로그인 성공 : 2FA 활성화시, 인증 페이지 이동" %}
```json
HTTP/1.1 301 Moved Permanently

Set-Cookie : session=abcdef1234567890
...

{ 
  "data" : '/auth',
  "resStatus" :
  {
    "code"   : "0002"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/login/oauth/42" baseUrl=" " summary="OAuth 로그인" expanded="false" fullWidth="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="로그인 성공 : 2FA 비활성화시, 메인 페이지 이동" %}
```json
HTTP/1.1 200 OK

Set-Cookie : session=abcdef1234567890
...

{ 
  "data" : '/main',
  "resStatus" :
  {
    "code"   : "0002"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="로그인 성공 : 2FA 활성화시, 인증 페이지 이동" %}
```json
HTTP/1.1 200 OK

Set-Cookie : session=abcdef1234567890
...

{ 
  "data" : '/auth',
  "resStatus" :
  {
    "code"   : "0002"
    "message": ""
  }
}
```
{% endswagger-response %}
{% endswagger %}



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[08.08]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">ID/PW 로그인</mark> (/login) & <mark style="background-color:yellow;">OAuth 로그인</mark> (/login/oauth/42)

* ~~로그인 성공후, 리다이렉트를 반환한다. (2FA 활성화시, 인증페이지로)~~
* ~~로그인 성공후, 리다이렉트를 반환한다. (2FA 비활성화시, 메인페이지로)~~

&#x20;:right\_facing\_fist:  로그인 성공후, 리다이렉트 대신 <mark style="background-color:green;">200 OK</mark>를 반환한다.

</details>

<details>

<summary><mark style="color:blue;">[07.26]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">ID/PW 로그인</mark> (/login)

* 로그인 성공후, sessionid가 전달된다.
* 로그인 성공후, 리다이렉트를 반환한다. (2FA 활성화시, 인증페이지로)
* 로그인 성공후, 리다이렉트를 반환한다. (2FA 비활성화시, 메인페이지로)

#### <mark style="background-color:yellow;">OAuth 로그인</mark> (/login/oauth/42)

* 로그인 성공후, sessionid가 전달된다.
* 로그인 성공후, 리다이렉트를 반환한다. (2FA 활성화시, 인증페이지로)
* 로그인 성공후, 리다이렉트를 반환한다. (2FA 비활성화시, 메인페이지로)

</details>

