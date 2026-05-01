# 맛슐랭 법적 문서 정적 사이트 (#269)

GitHub Pages로 즉시 호스팅 가능한 Jekyll 사이트. 출시 전 App Store Connect의 "개인정보 처리방침 URL" 입력 필수.

## 1단계 — GitHub Pages 활성화 (10분)

1. **레포 Settings → Pages** 진입
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / **Folder**: `/legal/site`
4. **Save** → 1~2분 후 `https://{org}.github.io/{repo}/legal/site/` URL 활성화

또는 **커스텀 도메인** 사용 시:
- `legal/site/CNAME` 파일에 `legal.matroad.app` 등 입력
- DNS provider에 CNAME 레코드 (`legal.matroad.app` → `{org}.github.io`)
- App Store Connect 입력 URL = `https://legal.matroad.app/privacy/`

## 2단계 — privacy / terms 동기화

이 디렉토리(`legal/site/`)의 `privacy.md` / `terms.md`는 상위 `legal/privacy-policy.md` / `legal/terms-of-service.md`의 **복사본**.

**동기화 정책**:
- 원본은 `legal/*.md` (개발 작업용 — markdown 직접 편집)
- 사이트는 `legal/site/*.md` (호스팅 배포용 — Jekyll frontmatter 추가됨)
- 원본 변경 시 사이트도 같이 업데이트 (PR로 함께)
- 큰 변경(주요 정책 변경)은 변호사 검토 → 양쪽 동시 업데이트

## 3단계 — App Store Connect 입력

App Store Connect → 앱 → 앱 정보:
- **개인정보 처리방침 URL**: `https://legal.matroad.app/privacy/` (또는 GitHub Pages URL)
- **이용약관 URL** (선택, IAP 있으면 사실상 필수): `https://legal.matroad.app/terms/`

## 4단계 — Kakao Developers 콘솔 입력

Kakao Developers → 앱 → 동의항목 → "개인정보 보호 책임자":
- 동일 URL 입력 (Apple과 일관)

## 변호사 검토 진행 (출시 전 필수)

본 문서는 **법률 자문이 아닌 초안 템플릿**입니다.
1. 한국 변호사 (가능하면 IT/플랫폼 전문)
2. KISA 가이드라인 대조
3. 검토 완료 후 markdown 갱신 + 사이트 재배포 (자동 — 커밋만 하면 GitHub Pages 자동 빌드)

## 향후 변경 시

- 정책 변경 → 본 문서 markdown 갱신
- App Store는 정책 변경 시 유저에게 in-app 안내 권장 (앱 시작 시 modal)
- 정보통신망법 §27의 5 — 개인정보 처리방침 변경 시 7일 전 공지 의무
