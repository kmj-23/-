# 일정관리 앱 API 명세서
|기능|Method|URL|Request|Response|Status Code|
|:---:|:---:|:---:|:---:|:---:|:---|
|일정 생성하기|POST|/api/schedules|요청body|등록정보|- 성공: 201 Created|
|일정 전체 조회하기|GET|/api/schedules||다건응답 정보|- 성공: - Status Code 200 OK<br>- 전체 일정x: 200 OK & []|
|일정 단건 조회하기|GET|/api/schedules/{id}||단건응답 정보|- 성공: 200 OK<br>- 전체 일정x: 404 NotFound|
|일정 수정<br>(덮어쓰기)|PUT|/api/schedules/{id}|<br>요청body|수정 정보|- 성공: 200 OK<br>- 해당하는 일정x: 404 NotFound<br>- 입력할 값을 누락: 400 BadRequest|
|일정 삭제하기|DELETE|/api/schedules/{id}|||- 성공: Status Code 200 OK<br>- 삭제하려는 일정x: 404 NotFound|


### ■ 일정 생성
#### □ 요청
|이름|타입|설명|필수여부|
|:---:|:---:|:---:|:---:|
|title|String|일정명|필수|
|content|String|일정 내용|필수|
|password|String|비밀번호|필수|

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
    "id": "1"
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
    "id": "1",
    "title": "강의 듣기",
    }
    {
    "id": "2",
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
    "id": "1",
    "title": "강의 듣기",
    "contents": "다음 주 월요일 마감"
    }
    </code>
</pre>

### 일정 수정(덮어쓰기)
#### □ 요청
|이름|타입|설명|필수여부|
|:---:|:---:|:---:|:---:|
|title|String|일정명|필수|
|content|String|일정 내용|필수|

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
    "id": "1",
    "title": "졸업논문 마감일",
    "contents": "토익으로 대체가능"
    }
    </code>
</pre>

### 일정 삭제하기
#### □ 요청
|이름|타입|설명|필수여부|
|:---:|:---:|:---:|:---:|
|password|String|비밀번호|필수|

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



# 일정관리 앱 ERD
![image](https://github.com/user-attachments/assets/824ea867-c393-434b-81ca-cd749785d4b3)



# 일정관리앱 SQL
### 1.스케줄 및 유저 테이블 생성 query(Create)
<pre>
  <code>
  //schedule 테이블 생성
  CREATE TABLE schedule (
  id int NOT NULL PRIMARY KEY,
  title varchar(45) NOT NULL,
  content varchar(45) NOT NULL,
  password varchar(45) NOT NULL,
  creat_date timestamp(6) NOT NULL,
  update_date timestamp(6) NOT NULL);

 //user 테이블 생성
  CREATE TABLE user(
  userID int NOT NULL PRIMARY KEY,
  email varchar NOT NULL,
  password varchar(45) NOT NULL,
  name varchar(45) NOT NULL);
  </code>
</pre>

### 2. 일정 및 유저 생성 query(Insert)
<pre>
  <code>
//schedule 생성
INSERT INTO schedule
(id, title, content, password, creat_date, update_date)
VALUES
(id: '1', '강의 듣기', '다음주 월요일 마감', '1234', '241013', '241015');

//user 생성
INSERT INTO user
(userID, email, password, name)
VALUES
('abc', 'abc@naver.com' , '1234', '김민주');
  </code>
</pre>

### 3. 전체 일정 조회 query(Select)
<pre>
  <code>
SELECT *
FROM schedule;
    </code>
</pre>

### 4. 선택 일정 조회 query(Select) (일정명 조회)
<pre>
  <code>
SELECT title 
FROM schedule;
  </code>
</pre>   

### 5. 선택 일정 수정 및 유저 정보 수정 query(Update)
<pre>
  <code>
//schedule 정보 수정
UPDATE schedule
SET 
title='바뀐 제목',
contents='바뀐 내용'
WHERE id = 1;
    
//user 정보 수정
UPDATE user
SET
email = '바뀐 e-mail 주소',
password= '바뀐 비밀번호'
name= '바뀐 이름'
WHERE userId = 'userId';
  </code>
</pre>

### 6. 선택 일정 삭제 query(Delete)
<pre>
  <code>
DELETE FROM schedule
WHERE id=1
   </code>
</pre>




