# 4.머스테치로 화면 구성하기

## 진도 기록

|공부 날짜|공부한 페이지 수|
|---|---|
|2020.04.24|125p ~ 161p |

## 개요
- 머스테치를 통해 화면 영역을 개발하는 방법을 배워보자.
- 서버 템플릿 엔진과 클라이언트 템플릿 엔진의 차이는 무엇인지 알아보자.

## 4.1 서버 템플릿 엔진과 머스테치 소개
- 일반적으로 웹 개발에 있어 템플릿 엔진이란, 지정된 템플릿 양식과 데이터가 합쳐져 HTML 문서를 출력하는 소프트웨어를 이야기합니다.
- 서버 템플릿 엔진
  - JSP, Freemarker
  - 서버에서 구동
- 클라이언트 템플릿 엔진
  - Vue.js, React.js, 머스테치
  - 브라우저에서 구동
- 머스테치란
  - 수많은 언어를 지원하는 가장 심플한 템플릿 엔진입니다.
  - 루비, 자바스크립트, 파이썬, PHP, 자바, 펄, Go, ASP 등 현조하는 대부분 언어를 지원하고 있습니다.
  - 자바언어를 사용하면 서버 템플릿 엔진, 자바스크립트언어를 사용하면 클라이언트 템플릿 엔진으로 사용할 수 있습니다.
- 머스테치 장점
  - 문법이 다른 템플릿 엔진보다 심플합니다.
  - 로직 코드를 사용할 수 없어 View의 역할과 서버의 역할을 명확하게 분리됩니다.
  - Mustache.js와 Mustache.java 2가지가 다있어, 하나의 문법으로 클라이언트/서버 템플릿을 모두 사용 가능합니다.

## 4.2 기본 페이지 만들기
- 의존성 추가(머스테치 스타터)
- src/main/resources/templates에 파일 위치
- 머스테치 스타터 덕분에 컨트롤러에서 문자열을 반환항 때 앞의 경로와 두의 파일 확장자는 자동으로 지정됩니다.

## 4.3 게시글 등록 화면 만들기
- 부트스트랩, 제이쿼리 등 프론트엔드 라이브러리를 사용할 수 있는 방법은 크게 2가지가 있습니다.
  - 외부 CDN(실제 서비스에서는 잘 사용되지 않는다. 외부 서비스에 의존하게 때문에)
  - 직접 라이브러를 받아서 사용하는 방법
- 레이아웃 방식
  - 공통 영역을 별도의 파일로 분리하여 필요한 곳에서 가져다 쓰는 방식
  - ex) footer, header영역을 파일(부트스트랩, 제이쿼리등이 추가 되어 있음) 만들어 다른 머스테치 파일에서도 재사용할 수 있게 하자.
- 자바스크립트 페이지 로딩 속도
  - css는 header, js는 footer에 위치
  - HTML은 head가 다 실행되고서야 body가 실행됩니다.
  - js에도 우선순위가 있기 때문에 우선순위가 높은것부터 낮은순으로 위에서 아래로 배치하자.
- 기본적으로 자바스크립트는 함수형 스코프다.(공용공간/중복된 함수가 발생할 수 있다.)
- 스프링 부트는 기본적으로 src/main/resources/static에 위치한 자바스크립트, css, 이미지등 정적 파일들은 URL에서 /로 설정됩니다.

## 4.4 전체 조회 화면 만들기
- {{#posts}}, {{id}}
- Repository - @Query
- Querydsl
  - 타입 안정성이 보장됩니다.
  - 국내 많은 회사에서 사용 중입니다.
  - 레퍼런스가 많습니다.
- @Transactional(readOnly = true)
  - 트랜잭션 범위는 유지화되, 조회 기능만 남겨두어 조회 속도가 개선되기 때문에 등록, 수정, 삭제 기능이 전혀 없는 서비스 메소드에서 사용하자.
  - Hibernate Flush Mode Never가 된다.
- Model

## 4.5 게시글 수정, 삭제 화면 만들기
- 수정, 삭제

## 궁금한 점 스스로 찾아보기
### 1. @Transactional(readOnly = true)를 사용하면 쿼리가 하나라도 Hibernate에서 성능 최적화를 할 수 있다고한다.
- [Spring Transaction](https://kwonnam.pe.kr/wiki/springframework/transaction)
- [플러시(Flush)의 개념과 동작 과정](https://gmlwjd9405.github.io/2019/08/07/what-is-flush.html)

## 회고
- 템플릿 엔진에 대해서 리마인드 할 수 있었다.
- @Transactional(readOnly = true)의 성능 최적화 부분이 있다는걸 알게 되었다.
- 타임리프 말고도 많은 템플릿 엔진이 있군 ㅎㅎㅎㅎ. 프론트 프레임워크를 그래도 공부해보고 싶다.