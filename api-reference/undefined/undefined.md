# 회원가입

{% hint style="info" %}
**최근 업데이트** ([08.08](undefined.md#08.08))
{% endhint %}

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>회원가입 페이지</p></figcaption></figure>



> REST API

{% swagger method="get" path="signup/check/id/{id}" baseUrl=" " summary="아이디 중복 확인" expanded="false" fullWidth="false" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="id" required="true" type="아이디" %}
데이터 범위 : 영문자,숫자만 가능

문자열 길이 : 2이상 \~ 12이하
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
    "message": "이미 중복된 닉네임입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="signup" baseUrl=" " summary="회원가입" expanded="false" fullWidth="false" %}
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

{% swagger-response status="200: OK" description="회원가입 성공 : 로그인 페이지 이동" %}
```json
HTTP/1.1 200 OK

{ 
  "data" : '/login',
  "resStatus" :
  {
    "code"   : "0002"
    "message": ""
  }
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="회원가입 실패" %}
```json
HTTP/1.1 200 OK

{ 
  "data" :{},
  "resStatus" :
  {
    "code"   : "0001"
    "message": "이미 등록된 아이디입니다."
  }
}
```
{% endswagger-response %}
{% endswagger %}



> API 업데이트 노트

<details>

<summary><mark style="color:blue;">[08.08]</mark> 업데이트 내용</summary>

#### <mark style="background-color:yellow;">회원가입</mark> (POST /signup)

* ~~회원가입 성공시, 리다이렉트를 반환한다. (로그인 페이지로)~~

&#x20;:right\_facing\_fist: 회원가입 성공시, 리다이렉트 대신 <mark style="background-color:green;">200 OK</mark>를 반환한다.

</details>

<details>

<summary><mark style="color:blue;">[07.26]</mark> 업데이트 내용</summary>

#### &#x20;<mark style="background-color:yellow;">아이디 중복 확인</mark> (GET /signup/check/id/{id})

* '**id'**는 영문자, 숫자만 가능하며 총 길이는 2이상 \~ 12이하이다.

#### <mark style="background-color:yellow;">회원가입</mark> (POST /signup)

* '**id'**는 영문자, 숫자만 가능하며 총 길이는 2이상 \~ 12이하이다.
* '**password**'는 아스키 코드만 가능하며 총 길이는 8이상 \~ 15이하이다.
* '**nickname**'은 서버에서 랜덤으로 설정된다.
* 회원가입 성공시, 리다이렉트를 반환한다. (로그인 페이지로)

</details>
