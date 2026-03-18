## 📋 Spring & Lombok 어노테이션 정리

### 🍃 Spring Framework: 구조와 흐름 (The Manager)

> 객체의 역할을 정의하고 외부 요청(HTTP)과 연결하는 핵심 엔진입니다.

- **역할 정의**
  - `@RestController`: 데이터(JSON)를 반환하는 웹 API의 입구입니다.
  - `@Service`: 핵심 비즈니스 로직을 수행하는 계층입니다.
  - `@Repository`: 데이터베이스(DB)와 직접 소통하는 창구입니다.
- **데이터 매핑**
  - `@XxxMapping`: HTTP Method(GET, POST 등)와 자바 메서드를 연결합니다.
  - `@PathVariable`: URL 경로에 포함된 변수(ID 등)를 추출합니다.
  - `@RequestBody`: HTTP Body에 담긴 JSON 데이터를 객체로 변환합니다.

### 🌶️ Lombok Library: 코드 자동화 (The Secretary)

> 자바의 반복적인 코드를 대신 작성해주는 보조 도구입니다.

- **의존성 관리**
  - `@RequiredArgsConstructor`: `final` 필드에 대한 생성자를 자동으로 생성하여, 객체 간의 연결(의존성 주입)을 깔끔하게 처리합니다.
