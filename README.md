# @swayloop/tsconfig-base

swayloop org 공통 TypeScript 컴파일러 설정 베이스라인. strict + safety 옵션 + NodeNext.

## 설치

```bash
pnpm add -D @swayloop/tsconfig-base typescript
```

## 사용

`tsconfig.json`:

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

`outDir` / `rootDir` / `include` 등 프로젝트 구조 관련은 각자 추가.

## 포함된 옵션

| 카테고리 | 옵션 |
|---|---|
| 타겟 | `target: ES2022`, `module: NodeNext`, `moduleResolution: NodeNext`, `lib: ["ES2022"]` |
| Strict | `strict`, `noUncheckedIndexedAccess`, `noImplicitOverride`, `noFallthroughCasesInSwitch` |
| Interop | `esModuleInterop`, `skipLibCheck`, `resolveJsonModule`, `forceConsistentCasingInFileNames`, `verbatimModuleSyntax`, `isolatedModules` |
| 빌드 | `sourceMap: true`, `declaration: false` (활성화는 프로젝트에서) |

## 다른 환경 오버라이드

React / browser / deno 등은 자기 `tsconfig.json` 에서 덮어쓰기:

```json
{
  "extends": "@swayloop/tsconfig-base/base.json",
  "compilerOptions": {
    "lib": ["ES2022", "DOM", "DOM.Iterable"],
    "jsx": "preserve",
    "module": "ESNext",
    "moduleResolution": "Bundler"
  }
}
```

## 표준

브랜치/커밋/릴리즈 규칙은 [swayloop/.github](https://github.com/swayloop/.github/blob/main/docs/workflow.md) 참고.
