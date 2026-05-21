# wscrony.github.io

POSTECH 한욱신 교수의 개인 홈페이지 (Academic Pages / Minimal Mistakes 기반 Jekyll 사이트).

## CV/Resume 정보 동기화 규칙

다음 세 파일은 **동일한 CV 정보를 공유**하며, 한쪽을 수정하면 다른 두 쪽도 함께 갱신해야 한다.

| 파일 | 용도 | 범위 |
|---|---|---|
| `_pages/about.md` | 웹 홈페이지(About me) | 핵심 정보 요약 — 경력, Honors, Professional Activities, PC Memberships, Keynote 등 |
| `resume/cv-short.docx` | 단축형 이력서 (Word, 8pt) | 위와 유사한 요약 + Selected Publications/Journals 일부 |
| `resume/cv-full.docx` | 전체 이력서 (Word) | 모든 항목 포함 (개인 정보, 전체 출판물 목록 등) |

### 동기화 가이드

- Honors, Professional Activities(Editors/Organizers/PC Members/Reviewers), Keynote, Selected Publications 등 핵심 섹션은 세 파일 모두에 반영한다.
- 항목 순서는 **역연대순(최신 위쪽)**.
- 일부 학회는 명칭 규약이 다르므로 다음을 지킨다:
  - SIGMOD, VLDB, KDD, ICDE, EDBT, WWW, CIKM 등 DB 계열: **Program Committee Member**
  - ACL, EMNLP, NeurIPS, ICML, ICLR 등 ML/NLP 계열: **Reviewer**
- VLDB Endowment Trustee 등 임기가 있는 항목은 가장 최신 임기 표기에 맞춘다.
- 새 publication 추가 시 about.md(역연대순 번호 없음) ↔ cv-short(번호 자동) ↔ cv-full(번호 자동) 세 곳 모두 같은 entry로 반영.
- **`resume/`의 두 CV 파일(`cv-short.docx`, `cv-full.docx`)의 모든 콘텐츠는 영어로만 작성한다.** about.md에 한글 항목이 있더라도(예: `논문공헌상 SILVER`) CV에 넣을 때는 영어로 번역한다 (예: `Silver Paper Contribution Award, KIISE`).

### 작업 팁

- `.doc` ↔ `.docx` 변환: macOS `textutil -convert docx <file>.doc`
- `.docx` 콘텐츠 비교: `pandoc -f docx -t plain <file>.docx`로 텍스트 추출 후 diff
- `.docx` 프로그래밍 편집: `python-docx`로 paragraph element를 `deepcopy`해 텍스트만 교체하면 폰트/번호/리스트 스타일이 보존됨

## 디자인

- 메인 스타일은 `_sass/_variables.scss`(폰트·색·간격), `_sass/_base.scss`(타이포), `_sass/_masthead.scss`, `_sass/_sidebar.scss`, `_sass/_page.scss`에서 관리.
- 폰트는 `_includes/head.html`에서 Google Fonts(Inter + IBM Plex Serif) + Pretendard(한글) 로드.
- Accent color: deep navy `#0a2540`, link blue `#1d4ed8`, slate neutral scale.
- 로컬 SCSS 컴파일 점검: `tail -n +3 assets/css/main.scss | npx -y sass --load-path=_sass --no-source-map --stdin -` (Jekyll 빌드 없이 문법만 확인할 때 사용).

## 배포

- `master` 브랜치 push 시 GitHub Pages가 자동 빌드 (Actions 워크플로: `pages-build-deployment`).
- 배포 URL: <https://wscrony.github.io>.
