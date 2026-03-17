# API 명세

## Keywards

### API(Applicaion Programming Interface)

두 소프트웨어 구성 요소가 서로 통신할 수 있게 해주는 메커니즘이다.  
내부 구현을 몰라도, 약속된 방식(Interface)만 알면 기능을 사용할 수 있다.  
"특정 요청을 보내면, 특정 응답을 주겠다"는 소프트웨어간의 엄격한 약속이다.

API는 소프트웨어 개발에서 호환성을 위해 지켜야 하는 추상적인 원칙이다.  
라이브러리는 이러한 API들을 기반으로 개발자에게 기능을 제공할 수 있도록 실제 구현된 구현체다.

API가 실제 기능 구현체인 라이브러리와 함께 제공되는 경우도 있으며, 이 경우를 SDK(Software Development Kit)라고 한다.

1. 캡슐화와 정보 은닉 (Information Hiding)

"내부 구현을 몰라도 된다"는 점은 API의 가장 큰 장점입니다. 이는 내부 코드가 수정되더라도 API 규격(Interface)만 유지된다면 이를 사용하는 외부 소프트웨어는 아무런 영향을 받지 않음을 의미합니다.

2. 계약에 의한 설계 (Design by Contract)

"특정 요청에 대한 특정 응답"은 단순한 약속을 넘어선 규격입니다. 이를 어길 경우 시스템은 동작하지 않으며, 이는 API 문서(Documentation)가 소프트웨어 개발에서 설계도 역할을 하는 이유입니다.

3. 중재자(Mediator) 역할

API는 마치 레스토랑의 점원과 같습니다. 손님(Client)이 메뉴판(Interface)을 보고 주문(Request)을 하면, 점원은 주방(System)의 조리 과정(Implementation)을 노출하지 않고 결과물(Response)만 전달합니다.

#### 제어의 역전

1. API(라이브러리): 내가 주도하는 개발

일반적인 API나 라이브러리는 **'도구 상자'**와 같습니다.  
제어권: 개발자인 **'나'**에게 있습니다.  
작동 방식: 내가 필요할 때 API를 호출하고, 그 결과값을 받아서 다음 로직을 어떻게 진행할지 직접 결정합니다.  
자유도: 전체 프로그램의 흐름(Main 흐름)을 내가 원하는 대로 설계할 수 있습니다.

2. 프레임워크: 규칙에 따라야 하는 개발

프레임워크는 **'이미 지어져 있는 집의 뼈대'**와 같습니다.  
제어권: **'프레임워크'**에 있습니다. (Hollywood Principle: "나를 부르지 마라, 내가 너를 부를 것이다.")  
작동 방식: 프레임워크가 전체적인 흐름을 이미 다 짜놓았습니다. 개발자는 프레임워크가 지정한 특정 위치(빈 공간)에 필요한 비즈니스 로직만 끼워 넣습니다.  
제약 사항: 프레임워크가 정한 **라이프사이클(Lifecycle)**이나 규칙을 벗어나면 프로그램은 돌아가지 않습니다. 예를 들어, 웹 프레임워크에서 "HTTP 요청 -> 컨트롤러 -> 서비스"로 이어지는 흐름을 무시하고 마음대로 흐름을 바꾸려 하면 프레임워크는 동작하지 않습니다.

### URI(Uniform Resource Identifier) & URL(Uniform Resource Locator)

URL은 일종의 URI이다.  
URL은 URI + 위치이다.  
URL은 위치이므로 어떻게 위치를 찾고 도달할 수 있는지까지 포함되어야 한다.(프로토콜도 포함)  
URL이 자원의 식별자이기도 해서 URL을 URI로 섞어 사용하기도 한다.

https:// -> scheme  
gemini.google.com -> URI  
/app/ff17bbf526364a?hl=ko -> URN(Uniform Resource Name)  
`https://gemini.google.com/app/ff17bbf53214364a?hl=ko` -> URL

### HTTP 요청 Method

**주어진 리소스에 수행하길 원하는 행동을 나타냅니다.**  
클라이언트, 서버간 요청과 응답 데이터 전송 방식  
서버가 수행해야 할 동작을 지정하는 요청을 보내는 방법

Safe: Read-only -> GET, HEAD, OPTIONS

Cacheable

**멱등성(Idempotent)**

- 동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 서버의 상태도 동일하게 남을 때, 해당 HTTP 메서드가 멱등성을 가졌다고 말합니다.
- 서버에 미치는 영향(Side Effect)이 동일

#### GET

- The GET method requests a **representation** of the specified resource. Requests using GET should only retrieve data and should not contain a request content.
- GET 메서드는 지정된 자원의 표현을 요청합니다. GET을 사용하는 요청은 데이터만 가져와야 하며 요청 내용을 포함해서는 안 됩니다.

#### POST

- The POST method **submits an entity** to the specified resource, often causing a change in state or side effects on the server.
  '엔티티 제출(Submitting an Entity)'의 의미 분석

- 공식 문서에서 POST를 이렇게 정의하는 이유는 POST가 단순히 "데이터를 보낸다"는 행위를 넘어, **"특정 목적지에 데이터를 맡겨서 서버가 알아서 처리하게 한다"**는 포괄적인 행위를 설명하기 위해서입니다.

#### PUT

- The PUT method **replaces all** current representations of the target resource with the request content.

#### DELETE

- The DELETE method **deletes** the specified resource.

#### PATCH

- The PATCH method **applies partial modifications** to a resource.

### JSON(JavaScript Object Notation)

- 사람이 읽을 수 있고 시스템에서 구문 분석할 수 있는 방식으로 데이터를 저장하고 교환하기 위한 텍스트 기반 형식입니다.

#### JSON 데이터 유형

- 객체: JSON 객체 데이터는 {}(중괄호) 사이에 삽입된 한 쌍의 이름 또는 값입니다. 키는 반드시 문자열이어야 하며, 쉼표로 구분되고, 고유 값이어야 합니다.
- 배열: 배열 데이터 유형은 순서가 지정된 값의 모음입니다. JSON에서 배열 값은 문자열, 숫자, 객체, 배열, Boolean 또는 Null 유형이어야 합니다.
- 문자열: JSON에서 문자열은 큰따옴표로 묶이고, 유니코드 문자를 포함할 수 있으며, 일반적으로 이름, 주소 또는 설명과 같은 텍스트 기반 데이터를 저장하고 전송하는 데 사용됩니다.
- Boolean: Boolean 값은 true 또는 false로 지정됩니다. Boolean 값은 따옴표로 묶이지 않으며 문자열 값으로 취급됩니다.
- Null: Null은 의도적으로 비어 있는 값을 나타냅니다. 키에 어떤 값도 할당되어 있지 않은 경우 해당 키는 Null로 취급할 수 있습니다.
- 숫자: 숫자는 계산, 비교 또는 데이터 분석과 같은 다양한 용도로 숫자 값을 저장하는 데 사용됩니다. JSON은 양수 및 음수와 소수점을 모두 지원합니다. JSON 숫자는 JavaScript의 배정도수 부동소수점 형식을 따릅니다.

## Mission

## 기능 요구사항

1. 게시판 기능 요구사항 기본 정보
   1. 이 게시판에 존재하는 정보는 오직 **게시물**이다.
   2. 게시물은 게시물 id, 제목, 본문, 작성자, 게시일이 포함되어야 한다.

1. 게시물 생성 기능
   1. 게시물을 생성하는 기능이다.
   2. 게시물은 게시물 id, 제목, 본문, 작성자, 게시일이 포함되어야 한다.
   3. 게시물 id는 중복 되어선 안된다.
   4. 제목, 본문, 작성자만 사용자에게 입력 받는다.
   5. 위 중 하나라도 포함되어 있지 않으면 생성이 불가해야 한다.

1. 게시물 단건 삭제 기능
   1. 게시물을 삭제하는 기능이다.
   2. 게시물 id를 이용해 게시물 한 개를 삭제할 수 있어야 한다.
   3. 게시물 id가 존재하지 않으면 적절한 에러 메세지와 코드를 반환 해야 한다.
   4. 한 번 삭제하면 복구가 불가능해야 한다.

1. 게시물 단건 수정 기능
   1. 게시물을 수정하는 기능이다.
   2. 게시물 id를 이용해 게시물 한 개를 수정할 수 있어야 한다.
      1. 수정 가능한 정보는 제목, 본문, 작성자이다.
   3. 게시물 id가 존재하지 않으면 적절한 에러 메세지와 코드를 반환 해야 한다.
   4. 수정 시, 빈 값으로 수정이 불가능하다.

1. 게시물 단건 조회 기능
   1. 게시물을 조회하는 기능이다.
   2. 게시물 id를 이용해 게시물을 조회할 수 있어야 한다.
   3. 게시물 id가 존재하지 않으면 적절한 에러 메세지와 코드를 반환 해야 한다.

1. 게시물 전체 조회 기능
   1. 저장된 전체 게시물을 조회하는 기능이다.
   2. 게시물 생성 시간의 내림차순으로 조회 되어야 한다.
   3. 게시물이 없는 경우, 빈 응답값을 반환해야 한다.

### 공통

#### Default Header

- **Content-Type**: `application/json` (요청/응답 본문 형식)
- **Accept**: `application/json` (원하는 응답 형식)

#### 📢 공통 메시지 응답 규격 (Common Message Response)

데이터(객체/리스트)를 직접 반환하지 않는 모든 응답(생성, 수정, 삭제 성공 및 모든 에러 상황)은 아래 규격을 따릅니다.

| 이름    | 타입   | 설명                                 |
| ------- | ------ | ------------------------------------ |
| message | String | 처리 결과 또는 에러 원인에 대한 설명 |

### 게시물 생성 기능

게시물을 생성하는 기능이다.

- **HTTP Method: POST**
- **URL**: /posts

### Request

#### Body

| 이름   | 타입   | 설명               | 세부 사항        |
| ------ | ------ | ------------------ | ---------------- |
| title  | String | 게시물 제목        | 사용자 입력 필수 |
| text   | String | 게시물 본문 내용   | 사용자 입력 필수 |
| author | String | 게시물 작성자 이름 | 사용자 입력 필수 |

### Response

#### Header

| 이름     | 내용                                      |
| -------- | ----------------------------------------- |
| Location | 추가된 게시물에 접근할 수 있는 엔드포인트 |

#### Body

- 공통 메시지 응답 규격을 사용합니다.

### Example

#### Request

```json
POST /posts HTTP/1.1

{
    "title": "API 명세서 작성법",
    "text": "API 명세 죽습니다 진짜",
    "author": "고래"
}
```

#### Response 성공

```json
HTTP/1.1 201 Created
Location: /posts/1

{
    "message": "게시물이 성공적으로 생성되었습니다."
}
```

#### Response 실패 - 입력 공백

```json
HTTP/1.1 400 Bad Request

{
  "message": "제목, 본문, 작성자는 필수 입력입니다."
}
```

---

### 게시물 단건 삭제 기능

게시물을 삭제하는 기능이다.  
⚠️ **주의**: 이 작업은 물리 삭제(Hard Delete)를 수행하므로, 한 번 삭제된 데이터는 복구가 불가능합니다.

- **HTTP Method: DELETE**
- **URL**: /posts/${id}

### Request

#### Path Variable

| 이름 | 타입 | 설명                 | 필수 |
| :--- | :--- | :------------------- | :--- |
| id   | int  | 삭제할 게시물 식별자 | Y    |

#### Body

- 본문(Body)을 사용하지 않습니다.

### Response

#### Body

- 공통 메시지 응답 규격을 사용합니다.

### Example

#### Request

```json
DELETE /posts/1 HTTP/1.1
```

#### Response 성공

```json
HTTP/1.1 200 OK

{
    "message": "게시물이 성공적으로 삭제되었습니다."
}
```

#### Response 실패 - 존재하지 않는 게시물 ID

```json
HTTP/1.1 404 Not Found

{
    "message": "존재하지 않는 게시물입니다."
}
```

---

### 게시물 단건 수정 기능

게시물을 수정하는 기능이다.

- **HTTP Method: PUT**
- **URL**: /posts/${id}

### Request

#### Path Variable

| **이름** | **타입** | **설명**             | **필수** |
| -------- | -------- | -------------------- | -------- |
| id       | int      | 수정할 게시물 식별자 | Y        |

#### Body

| 이름   | 타입   | 설명               | 세부 사항        |
| ------ | ------ | ------------------ | ---------------- |
| title  | String | 게시물 제목        | 사용자 입력 필수 |
| text   | String | 게시물 본문 내용   | 사용자 입력 필수 |
| author | String | 게시물 작성자 이름 | 사용자 입력 필수 |

### Response

#### Body

- 공통 메시지 응답 규격을 사용합니다.

### Example

#### Request

```json
PUT /posts/1 HTTP/1.1

{
    "title": "수정할 제목",
    "text": "수정할 본문 내용",
    "author": "수정할 작성자"
}
```

#### Response 성공

```json
HTTP/1.1 200 OK

{
    "message": "게시물이 성공적으로 수정되었습니다."
}
```

#### Response 실패 - 존재하지 않는 게시물 ID

```json
HTTP/1.1 404 Not Found

{
    "message": "존재하지 않는 게시물입니다."
}
```

#### Response 실패 - 입력 공백

```json
HTTP/1.1 400 Bad Request

{
  "message": "제목, 본문, 작성자는 필수 입력입니다."
}
```

---

### 게시물 단건 조회 기능

게시물을 조회하는 기능이다.

- **HTTP Method: GET**
- **URL**: /posts/${id}

### Request

#### Path Variable

| **이름** | **타입** | **설명**             | **필수** |
| -------- | -------- | -------------------- | -------- |
| id       | int      | 조회할 게시물 식별자 | Y        |

#### Body

- 본문(Body)을 사용하지 않습니다.

### Response

#### Body - 200 OK

| 이름     | 타입   | 설명                        |
| -------- | ------ | --------------------------- |
| id       | int    | 게시물 식별자               |
| title    | String | 게시물 제목                 |
| text     | String | 게시물 본문 내용            |
| author   | String | 게시물 작성자 이름          |
| postedAt | String | 게시물 생성 날짜 (ISO 8601) |

#### Body - 404 Not Found

- 공통 메시지 응답 규격을 사용합니다.

### Example

#### Request

```json
GET /posts/1 HTTP/1.1
```

#### Response 성공

```json
HTTP/1.1 200 OK

{
    "id": 1,
    "title": "API 명세서 작성법",
    "text": "조회 기능은 GET 메서드를 사용합니다.",
    "author": "고래",
    "postedAt": "2026-03-17T19:00:00Z"
}

```

#### Response 실패 - 존재하지 않는 게시물 ID

```json
HTTP/1.1 404 Not Found

{
    "message": "존재하지 않는 게시물입니다."
}
```

---

### 게시물 전체 조회 기능

저장된 전체 게시물을 조회하는 기능이다.

- **정렬 조건**: 게시물 생성 시간(postedAt) 기준 **내림차순(최신순)**으로 정렬된다.
- **HTTP Method: GET**
- **URL**: /posts

### Request

#### Body

- 본문(Body)을 사용하지 않습니다.

### Response

#### Body - 200 OK

| 이름     | 타입   | 설명                               |
| -------- | ------ | ---------------------------------- |
| (Array)  | List   | 아래 객체들을 포함하는 리스트 형식 |
| id       | int    | 게시물 식별자                      |
| title    | String | 게시물 제목                        |
| text     | String | 게시물 본문 내용                   |
| author   | String | 게시물 작성자 이름                 |
| postedAt | String | 게시물 생성 날짜 (ISO 8601)        |

### Example

#### Request

```json
GET /posts HTTP/1.1
```

#### Response 성공

```json
HTTP/1.1 200 OK

[
  {
    "id": 3,
    "title": "세 번째 게시물",
    "text": "가장 최근에 쓴 글입니다.",
    "author": "서여",
    "postedAt": "2026-03-19T19:00:00Z"
  },
  {
    "id": 2,
    "title": "두 번째 게시물",
    "text": "중간에 쓴 글입니다.",
    "author": "제이콥",
    "postedAt": "2026-03-18T19:00:00Z"
  },
  {
    "id": 1,
    "title": "첫 번째 게시물",
    "text": "가장 먼저 쓴 글입니다.",
    "author": "고래",
    "postedAt": "2026-03-17T19:00:00Z"
  }
]
```

#### Response 성공 - 게시물이 없는 경우, 빈 응답값을 반환해야 한다.

```json
HTTP/1.1 200 OK

[]
```

### 사용된 HTTP 상태 코드 요약

| **상태 코드** | **이름**    | **발생 상황**                                          |
| ------------- | ----------- | ------------------------------------------------------ |
| **200**       | OK          | 조회, 수정, 삭제 요청이 성공적으로 처리됨              |
| **201**       | Created     | 새로운 게시물이 성공적으로 생성됨 (Location 헤더 포함) |
| **400**       | Bad Request | 필수 입력값(제목, 본문, 작성자) 누락 또는 공백 입력    |
| **404**       | Not Found   | 유효하지 않은 게시물 식별자(ID)로 접근 시              |
| **409**       | Conflict    | 서버 내 기존 데이터와 충돌(식별자 중복 등) 발생 시     |
