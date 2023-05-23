# base-monorepository

## 요약

-   yarn workspace와 yarn berry를 이용한 monorepo 기본 틀입니다.

## 구성

1. husky와 lint-staged를 이용한 commit전 prettier 검사 및 eslint fix
2. tsconfig base 지정
3. react-library 패키지 사용
4. nextJS CI 빌드까지 적용
5. global typecheck 추가 (병렬적으로 동작)
6. VS Code extension 추천 및 설정
