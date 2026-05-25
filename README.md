# @swayloop/tsconfig-base

swayloop org 공통 TypeScript 컴파일러 설정 모음. 3개 variant 제공:

| Variant | 대상 환경 | module / moduleResolution | jsx |
|---|---|---|---|
| `base.json` | Node (CLI · 라이브러리 · 서버) | `NodeNext` / `NodeNext` | — |
| `next.json` | Next.js | `esnext` / `bundler` | `preserve` |
| `react.json` | Vite / 일반 React | `ESNext` / `bundler` | `react-jsx` |

## 설치

```bash
pnpm add -D @swayloop/tsconfig-base typescript
```

## 사용

Node 프로젝트 (`tsconfig.json`):

```json
{
  "extends": "@swayloop/tsconfig-base/base.json",
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  },
  "include": ["src/**/*"]
}
```

Next.js 프로젝트:

```json
{
  "extends": "@swayloop/tsconfig-base/next.json",
  "compilerOptions": {
    "paths": { "@/*": ["./src/*"] },
    "plugins": [{ "name": "next" }]
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

Vite/React 프로젝트:

```json
{
  "extends": "@swayloop/tsconfig-base/react.json",
  "compilerOptions": {
    "types": ["vite/client"]
  },
  "include": ["src"]
}
```

## 공통으로 포함된 strict / safety 옵션

3개 variant 모두 공통:

- `strict`, `noUncheckedIndexedAccess`, `noImplicitOverride`, `noFallthroughCasesInSwitch`
- `esModuleInterop`, `skipLibCheck`, `resolveJsonModule`, `forceConsistentCasingInFileNames`, `isolatedModules`

## variant 별 차이

| | base | next | react |
|---|---|---|---|
| target | ES2022 | ES2022 | ES2022 |
| lib | `["ES2022"]` | `["DOM", "DOM.Iterable", "ES2022"]` | `["DOM", "DOM.Iterable", "ES2022"]` |
| module | NodeNext | esnext | ESNext |
| moduleResolution | NodeNext | bundler | bundler |
| jsx | — | preserve | react-jsx |
| noEmit | false (default) | true | true |
| verbatimModuleSyntax | true | false | true |
| allowJs | false | true | false |
| incremental | false | true | false |

## 표준

브랜치/커밋/릴리즈 규칙은 [swayloop/.github](https://github.com/swayloop/.github/blob/main/docs/workflow.md) 참고.
