# H.A.S. Design Lab 홈페이지

호서대학교 권영재 교수 연구실(H.A.S. Design Lab, Happiness & Space Design) 홈페이지의 소스입니다.

- 주소: https://www.haslab.kr
- 방식: HTML 파일로 된 정적 사이트를 GitHub Pages로 배포합니다. 따로 서버나 데이터베이스가 없습니다.
- 반영: 이 저장소의 `main` 브랜치에 올리면 1~2분 뒤 사이트에 자동으로 반영됩니다.

---

## 1. 폴더 구성

| 파일·폴더 | 내용 |
|---|---|
| `index.html` | 첫 화면(연구실 소개, 철학, 활동, 메뉴) |
| `research.html` | 연구업적 |
| `projects.html` | 주요 프로젝트 |
| `book.html` | 「디자인으로 행복할 수 있을까?」 도서 소개 |
| `happy-space.html` | 행복한 공간 레시피 30선. **직접 고치지 말고** `_src/`에서 만든다(아래 4번) |
| `lecture.html` | 강의 「환경심리 기반 공간디자인」 소개와 주차별 목록 |
| `lecture/week01.html` ~ `week15.html` | 주차별 강의 슬라이드(웹). 공통 스타일은 `lecture/assets/` |
| `lab-plan.html` | 2026 공공디자인 실험실 세부계획 |
| `assets/` | 사이트 공통 이미지, 로고, `site.css`(디자인), `site.js`(움직임) |
| `assets/docs/` | 내려받기용 문서(PDF) |
| `_src/` | 레시피 페이지를 만드는 원본: `recipes.json`(내용), `happy-space.template.html`(틀), `build.py`(생성) |
| `CNAME` | 사이트 도메인(`www.haslab.kr`). **지우지 마십시오** |
| `.nojekyll` | GitHub Pages가 파일을 그대로 쓰게 하는 표시. 지우지 마십시오 |

---

## 2. 글을 고칠 때

1. 고칠 페이지의 HTML 파일을 엽니다. 예: 연구업적은 `research.html`.
2. 바꿀 문장을 찾아 글자만 고칩니다. `<p>`, `<h2>` 같은 꺾쇠 표시와 `class="…"`는 그대로 둡니다.
3. 저장한 뒤 브라우저로 그 파일을 열어 확인하고, GitHub에 올립니다(5번).

간단한 수정은 GitHub 웹사이트에서 바로 할 수 있습니다. 저장소에서 파일을 열고 연필 아이콘(Edit)을 눌러 고친 뒤 **Commit changes**를 누르면 됩니다.

## 3. 사진을 바꾸거나 더할 때

- 사진은 `assets/`에 넣습니다. 파일 이름은 영문 소문자와 하이픈으로 짓습니다(예: `workshop-2026.jpg`).
- 가로 1600–2000px, JPG로 저장하면 화질과 속도가 적당합니다. 5MB가 넘는 원본은 줄여서 넣으십시오.
- HTML에서 기존 사진 파일 이름(예: `assets/workshop.jpg`)을 새 이름으로 바꾸면 됩니다.
- 같은 이름으로 덮어쓰면 HTML을 고칠 필요가 없습니다. 브라우저에 예전 사진이 남아 보이면 새로고침(Ctrl+F5)하십시오.

## 4. 행복한 공간 레시피를 고칠 때

`happy-space.html`은 `_src/recipes.json`의 내용으로 자동 생성됩니다. 내용은 `recipes.json`만 고칩니다.

- `parts`: 여섯 묶음(마음을 편안하게, 몸을 회복하게, 머리를 맑게, 기분을 다독이게, 몸을 움직이게, 사람을 연결하게)
- `recipes`: 레시피 30개. 하나는 다음 항목으로 되어 있습니다.
  `part`(묶음 번호), `title`(제목), `lead`(한 줄 요약), `level`(난이도 ★), `cost`(비용 ₩), `places`(적용 장소 목록), `problem`(문제 상황), `steps`(방법 목록), `why`(원리), `evidence`(연구 근거 목록), `tips`(팁), `ref`(참고문헌)

고친 뒤 이 폴더에서 다음을 실행하면 `happy-space.html`이 다시 만들어집니다.

```
python3 _src/build.py
```

- Windows에서는 `python _src/build.py`로 실행하고, 한글이 깨지는 오류가 나면 먼저 `set PYTHONUTF8=1`을 입력하십시오.
- `recipes.json`은 쉼표와 따옴표 하나만 빠져도 오류가 납니다. 고친 뒤 위 명령이 "30 recipes"처럼 끝나는지 확인하십시오.

## 5. 사이트에 반영하기

가장 쉬운 방법은 **GitHub Desktop**입니다.

1. GitHub Desktop에서 이 저장소를 내 컴퓨터로 받습니다(Clone).
2. 파일을 고치면 GitHub Desktop에 바뀐 파일이 보입니다.
3. 아래 칸에 무엇을 고쳤는지 한 줄 적고 **Commit to main** → **Push origin**을 누릅니다.
4. 1~2분 뒤 https://www.haslab.kr 에서 확인합니다. 저장소의 **Actions** 탭에서 배포가 끝났는지 볼 수 있습니다.

명령어로 할 때는 `git add .` → `git commit -m "고친 내용"` → `git push`입니다.

## 6. 도메인과 GitHub Pages 설정

- 도메인: `haslab.kr`(반값도메인, 다우기술 등록). 만료일 **2029년 9월 28일**. 만료 전에 갱신해야 사이트 주소가 유지됩니다.
- DNS 설정(도메인 관리 화면):

  | 종류 | 이름 | 값 |
  |---|---|---|
  | A | `@` (haslab.kr) | 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153 |
  | CNAME | `www` | `(저장소 소유자 GitHub 아이디).github.io` |

- GitHub Pages: 저장소 **Settings → Pages**에서 Source는 `main` 브랜치 `/ (root)`, Custom domain은 `www.haslab.kr`, **Enforce HTTPS** 켜기.
- 저장소 소유자가 바뀌면 `www`의 CNAME 값을 새 소유자 아이디로 바꿔야 합니다. 바꾼 뒤 HTTPS가 다시 켜지기까지 최대 하루가 걸릴 수 있습니다.

## 7. 디자인 원칙(요약)

사이트를 고칠 때 아래 원칙을 지키면 지금의 인상이 유지됩니다. 자세한 기준은 원자료 폴더의 「디자인_가이드.md」에 있습니다.

- 강조색은 로고색 진녹색 `#013D00` 하나만 씁니다.
- 둥근 모서리를 쓰지 않습니다(사진, 버튼, 박스 모두 각지게).
- 01, 02 같은 두 자리 번호를 쓰지 않습니다. 순서가 필요하면 "1주차", "Step 1"처럼 씁니다.
- 정보는 박스로 감싸지 않고 여백과 얇은 선으로 나눕니다.
- 글꼴은 Pretendard, 한글은 어절 단위로 줄을 바꿉니다.
- 이모지 아이콘, 여러 색 강조, 그림자 남용을 피합니다.

## 8. 원자료

사이트를 만들 때 쓴 원자료(로고 원본과 CDR, 연구업적·교육업적 PDF, 프로젝트 목록, 활동 사진, 강의자료, 도서 원고 등)는 Google Drive의 `HAS Lab_홈페이지` 폴더에 있습니다. 이 저장소에는 사이트에 실제로 쓰는 파일만 넣습니다. 이력서 같은 개인 문서는 공개 저장소에 올리지 마십시오.
