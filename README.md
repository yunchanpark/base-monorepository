# base-monorepository

1. nvm 설치
2. vscode 설치
3. yarn 설치
4. yarn berry 버전 변경

```
// project 폴더 생성
mkdir basemonorepository
cd basemonorepository

// yarn 버전 확인
yarn -v

// yarn 버전 변경
yarn set version stable
```

5. yarn workspace 패키지 생성

```
yarn init -w
```

6. 작업 공간 생성

-   작업할 공간 `apps` 폴더 추가

```
// ./package.json
{
  "name": "base-mono-repository",
  "packageManager": "yarn@3.5.1",
  "private": true,
  "workspaces": [
    "apps/*",
    "packages/*"
  ]
}
```

7. next 프로젝트 생성

```
// root 경로에서
cd ./apps
npx create-next-app@lastest
```

8. typescript error 발생

-   yarn berry pnp는 `node_modules` 모듈을 불러오는 방식이 다르기 때문에 error가 발생
-   typescript 허용 메시지뜨면 `허용`

```
yarn add -D typescript
yarn dlx @yarnpkg/sdks vscode
```

9. extensions 다운

```
// .vscode/extensions.json을 보면 나와있는 extension 다운
```

10. tsconfig 설정
    @todo

11. react library 추가

```
cd packages
mkdir design-system
cd design-system

// root 경로에서
yarn workspace @design-system/ui add typescript react-dom react @types/node @types/react @types/react-dom -D
```

12. react library 사용

```
yarn workspace next-web add @design-system/ui
```

13. react library 사용예시
    @todo

14. eslint/prettier 적용

```
yarn add prettier eslint eslint-config-prettier -D
```

-   .prettierrc 파일 생성 (원하는 옵션 설정)

```
{
    "printWidth": 105,
    "tabWidth": 4,
    "useTabs": false,
    "trailingComma": "all",
    "semi": true,
    "singleQuote": true,
    "jsxSingleQuote": false,
    "bracketSpacing": true,
    "jsxBracketSameLine": false
}
```

15. husky, lint-staged 적용

-   commit 전에 lint fix와 prettier 적용
-   pre-commit이 실행 파일이 아닐 경우 설정

```
chmod 755 .husky/pre-commit
```

16. typecheck

-   전역적으로 typecheck를 하기 위해 설치

```
yarn plugin import workspace-tools
```

-   typescript를 사용하는 프로젝트에 스크립트 등록

```
"scripts" {
  "typecheck": "tsc --project ./tsconfig.json --noEmit"
}
```

-   workspaces에서 typecheck할 때 병렬적으로 수행

```
"scripts" {
  "g:typecheck": "yarn workspaces foreach -pv run typecheck"
}
```
