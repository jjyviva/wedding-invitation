# 모바일 청첩장 (장재영 ♥ 정한나)

## 프로젝트 개요
- 배포 주소: https://jjyviva.github.io/wedding-invitation/ (GitHub Pages, main 브랜치 push 시 자동 배포, 반영까지 1~2분)
- 빌드 도구 없음 — `index.html` 단일 파일 (바닐라 HTML/CSS/JS). React 등 도입하지 말 것.
- 예식 정보: **2027년 3월 20일 (토) 오후 4시 30분, 대전 라도무스아트센터 루미니스홀** (유성구 동서대로 639, 042-823-5220)
- 혼주: 장계철·양금점의 장남 재영 / 정건원·박미선의 장녀 한나

## 작업 규칙
- **작업 시작 전 반드시 `git pull`** — 두 대 이상의 PC를 오가며 작업하므로 pull 없이 시작하면 충돌 남.
- 작업 끝나면 커밋 + push (push가 곧 배포).
- 사진: 원본은 `사진/` 폴더(gitignore됨, 저장소에 안 올라감). 웹용은 `photos/img01~30.jpg`
  (긴 변 1600px, 품질 82%, EXIF 방향 보정 완료). 새 사진 추가 시 같은 규격으로 리사이즈해서 photos/에 넣을 것.
- 갤러리 사진 순서는 index.html의 `PHOTOS` 배열이 결정 (현재: 스냅촬영 → 여행 → 일상 순).

## 디자인 결정 (사용자 확정 사항 — 임의 변경 금지)
- 전체 프레임: 미니멀 스타일 (크림 배경 #f1ece4, Noto Serif KR 명조, 더스티로즈 포인트 #b08d84), 참고: wedding-invitation-91z.pages.dev
- 표지: 사진 전체배경 + 좌상단 세로 이름("장재영 그리고 정한나") + 하단 필기체 영문(Great Vibes) 및 일시·장소
- 2페이지 최상단: D-day + 실시간 카운트다운 (사용자가 특별히 요청한 위치)
- 갤러리: 한 장씩 스와이프 미리보기 + "전체 보기" 별도 오버레이(2단, 세로 스크롤) + 라이트박스
  - 주의: 전체보기 그리드는 CSS columns를 스크롤 박스 안 래퍼(.cols)에 적용한 구조.
    스크롤 박스에 직접 columns 주면 가로로 넘침 (한 번 버그났던 부분).

## 확인된 사실 (재검증 없이 바꾸지 말 것)
- 하객 사진·영상 공유 앨범: 구글 포토 공유 앨범 "재영♥한나 결혼식"
  (https://photos.app.goo.gl/uuCbjQkyRz7Kz3dM8, 링크 공유 + 공동작업 허용 켜짐).
  index.html의 `GUEST_ALBUM_URL`에 연결돼 있음.
- 홀 이름 공식 표기는 "루미니스홀"(Luminis) — 사용자가 "루미너스홀"로 부르지만 공식 홈페이지(ladomus.co.kr) 기준 루미니스가 맞음. 사용자에게 이미 안내함.
- 대중교통 안내(유성온천역 → 106번 흥도초 하차 / 706번 등기소 하차)는 공식 홈페이지 기준 (2026-07 확인). 예식 임박 시(2027년 초) 노선 재확인 필요.
- 약도: 구글 지도 keyless 임베드 (`maps.google.com/maps?q=라도무스아트센터&output=embed`).
  처음에 OpenStreetMap을 썼다가 좌표 오류 + 해당 지역 데이터 부실로 교체함 (2026-09).
  OSM으로 되돌리지 말 것.

## 남은 작업 (미확정 항목)
- RSVP 구글폼: 참석 의사 전달 섹션의 `RSVP_FORM_URL`이 비어 있음 (현재 준비 중 안내 표시).
  사용자가 구글폼 만들어 링크 주면 연결. 항목 추천: 성함/신랑·신부측/참석 여부/동행 인원/식사 여부.
- 인사말 확정 문구 (현재 임시 문구)
- 계좌번호 (현재 ○○ 자리표시) — 신랑측/신부측 아코디언에 채울 것
- 갤러리 사진 최종 선별 (현재 예시 30장 전부 노출 중)
- 카카오톡 공유 미리보기 실기기 테스트 (og 태그는 넣어둠. og 이미지 바꾸면
  https://developers.kakao.com/tool/debugger/sharing 에서 캐시 초기화 필요)

## 배포 트러블슈팅
- Pages 배포가 "Deployment failed, try again later"로 실패하면:
  `POST https://api.github.com/repos/jjyviva/wedding-invitation/pages/builds` 로 강제 빌드 요청 (과거 두 번 발생, 이 방법으로 해결).
- GitHub API 토큰은 `printf "protocol=https\nhost=github.com\n" | git credential fill` 로 꺼낼 수 있음 (해당 PC에서 GitHub 로그인이 된 경우).
