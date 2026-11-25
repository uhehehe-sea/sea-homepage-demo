# S.E.A. 홈페이지 데모

정적 사이트(빌드 없음). 폴더 통째로 올리면 바로 배포됩니다.

## 구성
- `index.html` — 인트로(64 큐브 → SEA) + 메인 페이지 + KO/EN 전환 + AI 상담 창
- `img/` — 장비·현장 사진 6장 (출처: sea-e2e.com)
- `assets/video/` — 메인 히어로 영상 자리 (`hero.mp4`, 선택 `hero.webm`)
- `netlify.toml` — Netlify 설정

## 배포
- **Netlify**: app.netlify.com → Add new site → Deploy manually → 이 폴더(또는 zip)를 끌어다 놓기
- **GitHub Pages / 다른 정적 호스팅**: 폴더 내용을 그대로 업로드
- 로컬 확인: 폴더에서 `python -m http.server` 후 http://localhost:8000

## 설정 바꾸기
`index.html` 맨 위 `<script>` 안:
- `const DEFAULT_LANG='en';` (현재 영문판 기본) → `'ko'` 로 바꾸면 처음 열 때 한국어판 (방문자가 KO/EN 버튼으로 고른 언어는 그 브라우저에 저장돼 그쪽이 우선)
- `const CUBE_SCALE=1.4;` → 인트로 큐브 크기 배율 (1 = 이전 크기)

## 영상 넣기
현재 영상: 2026-11-24 받은 공정 영상(원본 .mov 882×1920 세로, 15초) — 가운데 가로 화면만 잘라 1280×720, 소리 없이 `hero.mp4`·`hero.webm`으로 넣음. 첫 화면 `img/hero-poster.jpg`.
바꿀 때는 `assets/video/hero.mp4` 를 교체하고 다시 배포. 코드 수정 필요 없음.
영상이 없으면 사진(`img/lab.webp`)이 보이고, 화면 밖이면 영상이 멈추며, '동작 줄이기' 설정이면 재생하지 않습니다.

## 외부에서 불러오는 것 (인터넷 필요)
- three.js r128 (cdnjs) — 인트로 큐브
- Google Fonts (Geist, Noto Sans KR)

## 알아둘 점
- **AI 상담 창**은 Claude 아티팩트 안에서만 동작합니다. 일반 호스팅에서는 "오프라인"으로 표시되고 입력이 막힙니다. 실제 사이트에서 쓰려면 별도 챗봇 API 연결이 필요합니다.
- 언어 선택은 브라우저에 저장됩니다(같은 브라우저에서만).
- 내용 출처: sea-e2e.com, eng.sea-e2e.com (2026-11-24 확인). 공지 2건 날짜는 "11월 초"로 추정 표기.
