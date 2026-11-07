# Seoulmate — 작업 안내서

## 한 줄 요약
KoreaTalk(한국인↔외국인 영상통화 언어교환 앱)의 **화면 디자인 시안**을 Claude Design에서 내보낸 것.
실제 앱 코드는 `ktalk` 저장소(Flutter + Supabase)에 있다.

## 파일
```
index.html                     시안 목록 (링크 모음)
export/KoreaTalk.dc.html       메인 화면 시안
export/Partner Match.dc.html   상대 매칭 시안
export/Video Call.dc.html      영상통화 시안
export/support.js, image-slot.js   Claude Design 화면 런타임 (수정 금지)
```
- `*.dc.html`은 Claude Design 형식. 디자인을 바꾸려면 Claude Design에서 고친 뒤 다시 내보내는 것이 안전하다.
- 이미지 일부는 Unsplash 주소를 직접 씀.

---

## 공통 작업 원칙 (IUX 프로젝트 전체)
- **언어:** 화면 문구·문서·커밋 메시지는 한국어. 쉬운 말, 기술 용어 최소화.
- **퍼블리싱 시안:** 순수 HTML/CSS + 간단한 스크립트만 넣는다. 서버·DB 연동 코드는 개발 단계에서 따로 붙인다.
- **아이콘:** Lucide. 디자인 시스템을 따로 정하지 않았으면 스포티파이 스타일(다크/화이트 + 포인트 컬러)을 기본으로 쓴다.
- **배포:** GitHub `main` → Vercel 자동 배포. 도메인은 가비아 `iux.kr`의 서브도메인(`*.iux.kr` CNAME → Vercel)을 쓴다.
- **DB:** Supabase 무료 플랜은 활성 프로젝트 2개까지라, 새 프로젝트를 만들지 말고 기존 `iux-cloud`(studio) 프로젝트에 테이블을 얹는 것을 먼저 검토한다.
- **비밀값:** 공개 저장소다. 서비스 키·AI 키·비밀번호는 절대 커밋하지 않는다. 키는 Vercel 환경 변수나 Supabase secrets에 둔다. Supabase anon(public) 키만 코드에 넣을 수 있다.
- **확인:** 고친 뒤에는 브라우저 콘솔 오류 0개, 모바일(390px)과 PC 화면을 눈으로 확인하고 나서 완료라고 한다.
- **브랜치:** `main`은 배포 중인 상태. 큰 작업이나 검증 전 작업은 브랜치(`wip/…`, `claude/…`)에 올리고, `main`을 강제 푸시(-f)로 덮어쓰지 않는다.
- **전체 프로젝트 목록:** https://github.com/handgoldking1234/iux-app/blob/main/docs/PROJECTS.md
