# 🍃 Spring 처음 스터디

## 🎯 학습 목표

- [ ] 웹에 대한 기초 지식 습득
- [ ] 간단한 API 명세 설계 능력 배양
- [ ] MySQL을 이용한 간단한 DB 스키마 설계
- [ ] Spring Initializr를 이용한 프로젝트 생성
- [ ] Spring Boot 기반 REST API 구현
- [ ] Postman을 활용한 API 테스트 및 검증

---

## 📈 학습 순서

### Step 1. API 명세 설계

- [ ] 기능 요구사항 분석 및 API 직접 설계
  - [ ] 키워드 학습: `API`, `URL`, `URI`, `Body`, `HTTP Method(GET, POST, etc.)`, `JSON`, `Response Code`

### Step 2. 최소 Annotation 학습

- [ ] 설계한 API에 각 어노테이션이 필요한 이유 고찰
  - [ ] `@RestController`, `@Service`, `@Repository`, `@RequiredArgsConstructor`
  - [ ] `@PostMapping`, `@GetMapping`, `@DeleteMapping`, `@PatchMapping`
  - [ ] `@PathVariable`, `@RequestBody`

### Step 3. 프로젝트 생성 및 환경 설정

- [ ] [Spring Initializr](https://start.spring.io/)를 통한 프로젝트 생성
- [ ] `build.gradle`의 역할 및 `dependency` 개념 이해

### Step 4. 데이터베이스 설계 및 연결

- [ ] MySQL을 이용한 정보 저장 구조 설계
- [ ] Spring과 DB 연결 방식 학습 (JPA, Entity)
- [ ] 관련 어노테이션 학습
  - [ ] `@Entity`, `@Id`, `@Column`
  - [ ] `@NotBlank`, `@NotNull`

### Step 5. API 구현 및 테스트

- [ ] 게시물 생성 API 구현
- [ ] Postman을 사용한 API 작동 테스트
- [ ] 나머지 CRUD API(조회, 수정, 삭제) 완성 및 피드백 공유

---

## 📝 기능 요구사항

### 1. 기본 정보

- [ ] 도메인 모델: **게시물(Post)**
- [ ] 필수 데이터: `게시물 id`, `제목`, `본문`, `작성자`, `게시일`

### 2. 게시물 생성 (`POST`)

- [ ] 제목, 본문, 작성자를 입력받아 생성
- [ ] 게시물 id 중복 방지 로직 적용
- [ ] 필수 입력값(제목, 본문, 작성자) 누락 시 생성 불가 처리

### 3. 게시물 단건 삭제 (`DELETE`)

- [ ] 게시물 id를 이용한 삭제 기능
- [ ] 존재하지 않는 id 요청 시 적절한 에러 메시지 및 코드 반환
- [ ] 삭제 후 복구 불가능 확인

### 4. 게시물 단건 수정 (`PATCH` or `PUT`)

- [ ] 게시물 id를 이용한 수정 기능
- [ ] 수정 가능 항목: `제목`, `본문`, `작성자`
- [ ] 존재하지 않는 id 요청 시 에러 처리
- [ ] 빈 값(Empty String)으로 수정 불가 처리

### 5. 게시물 단건 조회 (`GET`)

- [ ] 게시물 id를 이용한 상세 정보 조회
- [ ] 존재하지 않는 id 요청 시 에러 처리

### 6. 게시물 전체 조회 (`GET`)

- [ ] 모든 게시물 리스트 조회
- [ ] **게시일 기준 내림차순(최신순)** 정렬
- [ ] 데이터가 없는 경우 빈 배열(`[]`) 반환
