# Vue.js TMDB API를 이용한 영화정보 사이트

Vue.js와 TMDB API를 활용한 영화 정보 제공 사이트입니다. 사용자들은 최신 영화, 인기 영화, 개봉 예정 영화, 최고 평점 영화 등 다양한 카테고리의 영화 정보를 탐색하고, 영화 검색 기능을 통해 원하는 영화를 찾을 수 있습니다.

[사이트보기](https://movie-project-ecru.vercel.app/)

## 프로젝트 목표

- Vue.js 프레임워크를 이용한 SPA(Single Page Application) 개발
- TMDB API를 사용하여 실시간 영화 데이터 연동
- 사용자 친화적인 UI/UX 디자인 구현

## 기술 스택

- **프론트엔드**: Vue.js
- **스타일링**: SCSS
- **API**: TMDB API
- **라우팅**: Vue Router
- **HTTP 클라이언트**: Axios

## 프로젝트 구조

- `src/assets`: 스타일 시트 및 이미지 파일
- `src/components`: Vue 컴포넌트
- `src/views`: 페이지 뷰
- `src/router`: Vue Router 설정
- `src/App.vue`: 메인 애플리케이션 컴포넌트
- `src/main.js`: 애플리케이션 시작점

## 구현 기능

- **영화 카테고리별 조회**: 최신 영화, 인기 영화, 개봉 예정 영화, 최고 평점 영화 등 카테고리별 영화 목록 제공
- **영화 상세 정보**: 선택한 영화의 상세 정보 및 출연진 정보 제공
- **영화 검색**: 키워드를 통한 영화 검색 기능
- **반응형 웹 디자인**: 모바일 및 태블릿을 포함한 다양한 디바이스 지원

## 라이브러리 설치

```bash
npm install sass
npm install axios
npm install vue-router
```

## 셋팅

```
Vue.js - The Progressive JavaScript Framework

√ Project name: ... .
√ Package name: ... movie
√ Add TypeScript? ... No
√ Add JSX Support? ... Yes
√ Add Vue Router for Single Page Application development? ... Yes
√ Add Pinia for state management? ... No
√ Add Vitest for Unit Testing? ... No
√ Add an End-to-End Testing Solution? » No
√ Add ESLint for code quality? ... Yes
√ Add Prettier for code formatting? ... Yes

Scaffolding project in C:\Users\line\Documents\GitHub\movie-project2023...

Done. Now run:

  npm install
  npm run format
  npm run dev
```

## 작업 순서

1. **프로젝트 설정**: Vue.js 프로젝트 생성 및 초기 설정
2. **API 연동**: TMDB API를 사용하여 영화 데이터 가져오기
3. **라우팅 설정**: Vue Router를 이용하여 페이지 라우팅 설정
4. **컴포넌트 설계**: 영화 정보 표시를 위한 컴포넌트 설계 및 구현
5. **스타일링**: SCSS를 사용하여 스타일링
6. **영화 검색 기능 구현**: 사용자가 입력한 키워드로 영화 검색
7. **반응형 웹 디자인**: 다양한 화면 크기에 맞게 UI 조정
8. **최종 검토 및 배포**: 코드 리뷰, 최종 검토 후 사이트 배포

### 추가내용

- ref
  - 컴포넌트 내에서 상태를 저장하는 데 사용되는 함수
  - .value 속성을 통해 값을 읽거나 쓸 수 있음
  - Vue.js의 ref는 일반적으로 불변성을 가진 객체를 반환
- onMounted
  - 컴포넌트가 마운트된 후에 실행되는 함수
  - 컴포넌트가 화면에 나타난 직후에 어떤 동작을 수행하고 싶을 때 사용
- postman
  - API 테스트 및 디버깅에 유용한 도구
  - 프로젝트 개발 중에 API 요청과 응답을 테스트하고 디버깅하는 데 사용
- v-for
  - 배열이나 객체의 각 항목을 반복하면서 템플릿 요소를 렌더링하는 데 사용
- v-bind(또는 :)
  - 요소의 속성에 JavaScript 표현식을 바인딩하는 데 사용

## 트러블 슈팅

<details>
<summary></summary>

</details>
