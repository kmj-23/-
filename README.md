# 일정관리 앱 API 명세서
|기능|Method|URL|Request|Response|
|:---:|:---:|:---:|:---:|:---:|
|일정 생성하기|POST|/schedules|{<br>"name": string,<br> "contents": string<br>} |//성공시 Status Code 201 CREATED| 
|일정 전체 조회하기|GET|/schedules||//성공시 Status Code 200 OK<br>[<br>{<br>"id": Long<br>"name": string,<br> "contents": string<br>}<br>{<br>"id": Long<br>"name": string,<br> "contents": string<br>}<br>..<br>]<br>//해당 id소유자의 전체 일정이 없으면 200 OK와 []|
|일정 단건 조회하기|GET|/schedules/{id}||//성공시 Status Code 200 OK<br>{<br>"id": Long<br>"name": string,<br> "contents": string<br>}<br>//해당 id소유자의 일정이 없는 경우 404 NotFound
|일정 수정(덮어쓰기)|PUT|/schedules/{id}|{<br>"name": string,<br> "contents": string<br>}|//성공시 Status Code 200 OK<br>//해당하는 일정이 없으면 404 NotFound<br>//필수로 입력해줘야 하는 값을 누락한 경우 400 BadRequest|
|일정명 수정|PATCH|/schedules/{id}|{<br>"name": string<br>}|//성공시 Status Code 200 OK<br>//해당하는 일정이 존재하지 않는 경우 404 NotFound<br>//수정하고자 하는 일정명을 누락한 경우 400 BadRequest|
|일정 삭제하기|DELETE|/schedules/{id}||//성공시 Status Code 200 OK<br>//삭제하고자 하는 일정이 존재하지 않는 경우 404 NotFound|


### ■ 일정 생성
#### □ 요청
|이름|타입|설명|
|:---:|:---:|:---:|
|name|String|일정명|
|content|String|일정 내용|

{<br>"id": Long<br>"name": string,<br> "contents": string<br>}

#### □ 응답
|이름|타입|설명|
|:---:|:---:|:---:|
|id|Long|사용자 식별 번호|
|name|String|일정명|
|content|String|일정 내용|

### 일정 전체 조회하기

### 일정 단건 조회하기

### 일정 수정(덮어쓰기)

### 일정명 수정

### 일정 삭제하기

# 일정관리 앱 ERD



# 일정관리앱 SQL
