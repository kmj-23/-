# 일정관리 앱 API 명세서
|기능|Method|URL|Request|Response|Status Code|
|:---:|:---:|:---:|:---:|:---:|:---|
|일정 생성하기|POST|/api/schedules|요청body|등록정보|- 성공: 201 Created|
|일정 전체 조회하기|GET|/api/schedules||다건응답 정보|- 성공: - Status Code 200 OK<br>- 전체 일정x: 200 OK & []|
|일정 단건 조회하기|GET|/api/schedules/{id}|요청param|단건응답 정보|- 성공: 200 OK<br>- 전체 일정x: 404 NotFound|
|일정 수정<br>(덮어쓰기)|PUT|/api/schedules/{id}|요청param/<br>요청body|수정 정보|- 성공: 200 OK<br>- 해당하는 일정x: 404 NotFound<br>- 입력할 값을 누락: 400 BadRequest|
|일정명 수정|PATCH|/api/schedules/{id}|요청param/<br>요청body|수정정보|- 성공: Status Code 200 OK<br>- 해당 일정 존재x: 404 NotFound<br>- 수정하고자 하는 일정명 누락: 400 BadRequest|
|일정 삭제하기|DELETE|/api/schedules/{id}|요청param||- 성공: Status Code 200 OK<br>- 삭제하려는 일정x: 404 NotFound|


### ■ 일정 생성
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|title|String|일정명|
|content|String|일정 내용|
|password|String|비밀번호|

<pre>
  <code>
    {
    "title": "강의 듣기", 
    "contents": "다음 주 월요일까지",
    "password": "1234"
    }
  </code>
</pre>


#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|string|아이디|
|title|String|일정명|
|content|String|일정 내용|
|password|String|비밀번호|

<pre>
  <code>
    {
    "id": "1111"
    "title": "강의 듣기", 
    "contents": "다음 주 월요일까지",
    "password": "1234"
    }
  </code>
</pre>

### 일정 전체 조회하기 
#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|string|아이디|
|title|String|일정명|

<pre>
  <code>
    [
    {
    "id": "1111",
    "title": "강의 듣기",
    }
    {
    "id": "2222",
    "title": "치과 진료",
        ..
    }
    ]
  </code>
</pre>

### 일정 단건 조회하기
#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|string|아이디|
|title|String|일정명|
|content|String|일정 내용|

<pre>
  <code>
    {
    "id": "1111",
    "title": "강의 듣기",
    "contents": "다음 주 월요일 마감"
    }
    </code>
</pre>

### 일정 수정(덮어쓰기)
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|title|String|일정명|
|content|String|일정 내용|

<pre>
  <code>
    {
    "title": "졸업논문 마감일", 
    "contents": "토익으로 대체가능"
    }
  </code>
</pre>

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|string|아이디|
|title|String|일정명|
|content|String|일정 내용|

<pre>
  <code>
    {
    "id": "1111",
    "title": "졸업논문 마감일",
    "contents": "토익으로 대체가능"
    }
    </code>
</pre>

### 일정명 수정
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|title|String|일정명|

<pre>
  <code>
    {
    "name": "영어 시험"
    }
    </code>
</pre>

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|string|아이디|
|title|String|일정명|
|content|String|일정 내용|

<pre>
  <code>
    {
    "id": "1111",
    "title": "영어 시험",
    "contents": "토익으로 대체가능"
    }
    </code>
</pre>

### 일정 삭제하기
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|password|String|비밀번호|

<pre>
  <code>
    {
    "password": "1234"
    }
    </code>
</pre>

#### □ 응답
<pre>
  <code>
   
  </code>
</pre>

|기능|Method|URL|Request|Response|Status Code|
|:---:|:---:|:---:|:---:|:---:|:---|
|유저 등록|POST|/api/users|요청body|등록정보|성공:201 Created|
|유저 정보 조회|GET|/api/users/{id}|요청body|단건응답 정보|- 성공: 200 OK<br>- 전체 일정x: 404 NotFound|
|유저 정보 수정|PUT|/api/users{id}|요청body|수정정보|- 성공: Status Code 200 OK<br>- 해당 일정 존재x: 404 NotFound<br>- 수정하고자 하는 일정명 누락: 400 BadRequest|

### 유저등록
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|
|password|String|비밀 번호|

<pre>
  <code>
    {
    "name": "김민주", 
    "email": "abcd123@naver.com",
    "password": "1234"
    }
  </code>
</pre>

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|
|password|String|비밀 번호|

<pre>
  <code>
    {
    "name": "김민주", 
    "email": "abcd123@naver.com",
    "password": "1234"
    }
  </code>
</pre>

### 유저 정보 조회
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|


<pre>
  <code>
    {
    "name": "김민주", 
    "email": "abcd123@naver.com"
    }
  </code>
</pre>

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|
|password|String|비밀 번호|

<pre>
  <code>
    {
    "name": "김민주", 
    "email": "abcd123@naver.com",
    "password": "1234"
    }
  </code>
</pre>

### 유저 정보 수정
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|
|password|String|비밀 번호|

<pre>
  <code>
    {
    "name": "김민수", 
    "email": "abcd123@naver.com",
    "password": "1234"
    }
  </code>
</pre>

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|유저 이름|
|email|String|유저 이메일|
|password|String|비밀 번호|

<pre>
  <code>
    {
    "name": "김민수", 
    "email": "abcd123@naver.com",
    "password": "1234"
    }
  </code>
</pre>


# 일정관리 앱 ERD



# 일정관리앱 SQL
