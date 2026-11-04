# 엠밸리테크 Astro 사이트

## GitHub에 올릴 파일

이 프로젝트는 `node_modules`, `.astro`, `dist`를 제외한 소스 프로젝트입니다.
GitHub 저장소에는 이 폴더 안의 파일과 폴더를 업로드하면 됩니다.

## 로컬 실행

Node.js 22 이상을 설치한 뒤 프로젝트 루트에서 실행합니다.

```bash
npm ci
npm run dev
```

## 빌드

```bash
npm run build
npm run preview
```

빌드 결과는 `dist/`에 생성됩니다. `node_modules/`, `.astro/`, `dist/`는 `.gitignore`에 따라 GitHub에 올리지 않습니다.

## Netlify 연결

- Build command: `npm run build`
- Publish directory: `dist`
- Base directory: 비워 둠 (프로젝트 루트에 `package.json`이 있는 경우)

GitHub 저장소를 Netlify에 연결하면 Netlify가 의존성 설치와 빌드를 수행합니다. `node_modules`를 GitHub에 업로드할 필요는 없습니다.

## 중요: 현재 사이트 구조

현재 `src/pages/index.astro`는 메뉴 전환을 한 페이지 안에서 처리하는 단일 페이지 구조입니다. 이 패키지에서는 Netlify의 모든 경로를 `/index.html`로 강제 연결하던 규칙을 제거했습니다. 따라서 향후 `/products/`, `/tech/` 등 실제 Astro 페이지 파일을 추가할 수 있는 상태입니다.

단, 이 ZIP만으로 제품/기술자료 메뉴가 각각 독립된 SEO 페이지로 이미 분리된 것은 아닙니다. 개별 주소와 고유한 페이지 제목·설명·본문을 갖추려면 다음 단계에서 기존 단일 페이지를 공통 레이아웃과 실제 Astro 라우트로 분리해야 합니다.

## 외부 데이터

제품 및 기술자료는 빌드 시 Google 스프레드시트에서 가져옵니다. 따라서 Netlify 빌드 시 해당 스프레드시트가 공개적으로 읽을 수 있어야 합니다.
