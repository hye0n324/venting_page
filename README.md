# 환기 (Venting)

환기 게임 소개 페이지와 프롤로그 튜토리얼 베타를 담은 정적 웹사이트예요.
빌드 도구 없이 HTML, CSS, JavaScript만 써서, 파일을 그대로 올리면 동작해요.

```
venting-site/
├─ index.html            게임 소개(랜딩) 페이지. 체험판 포함
├─ prologue/
│  └─ index.html         프롤로그 튜토리얼 베타 (플레이 버전)
├─ .nojekyll             GitHub Pages가 파일을 가공하지 않게 하는 빈 파일
└─ README.md
```

## 로컬에서 열어 보기

- `index.html`을 브라우저로 열면 돼요. 폰트는 구글 폰트를 쓰므로 인터넷이 연결돼 있어야 원래 글꼴로 보여요.
- 페이지 간 이동까지 정확히 확인하려면 터미널에서 `python3 -m http.server 8000`을 실행하고 `http://localhost:8000`을 여세요.

## GitHub Pages로 배포하기

1. GitHub에서 새 저장소를 만들어요. 이름은 예를 들어 `venting`으로 해요.
2. 이 폴더의 파일을 저장소 맨 위(루트)에 올려요. `index.html`이 저장소 맨 위에 있어야 해요.
3. 저장소의 Settings → Pages에서 Source를 `Deploy from a branch`로 하고, Branch는 `main`, 폴더는 `/ (root)`로 저장해요.
4. 1~2분 뒤 `https://<계정명>.github.io/venting/`로 열려요. 프롤로그는 `.../venting/prologue/`예요.

무료 플랜에서는 공개 저장소여야 Pages를 쓸 수 있어요. 비공개로 두려면 GitHub Education으로 Pro를 받거나, Netlify·Vercel에 폴더를 끌어다 놓는 방법이 있어요.

## 코드 위치 (프롤로그)

`prologue/index.html` 안에서 아래 이름으로 찾으면 돼요.

| 바꾸고 싶은 것 | 찾을 이름 |
|---|---|
| 색, 글꼴 | 맨 위 `:root` |
| 방의 물건 이름과 설명 | `ITEMS` |
| 방 안 물건의 위치와 크기 | `objects()` |
| 전화 대사와 분기 | `CN()` |
| 행동별 규칙(체력·시간 소모, 메시지) | `COST`, `TIME`, `doAct()` |
| 장면 전환 카드("D-366") | `renderOverlay()` 안의 `jump` |
| 견적서 내용 | `renderPanel()` 안의 `p==='dm'` |

## 메모

- 랜딩 `index.html`은 팀원이 만든 원본에서 세 가지만 바꿨어요: 탭 제목에서 `(Copy)`를 뺐고, "체험해보기" 버튼 세 곳(메뉴, 홈 하단, 스토리 끝)이 기존 체험판 대신 프롤로그(`prologue/index.html`)를 열도록 했고(`data-href`), 그 이동용 짧은 스크립트를 파일 끝에 붙였어요.
- 기존 체험판(의뢰 #001) 코드는 `index.html` 안에 그대로 남아 있어요. 버튼은 연결되지 않지만 주소 끝에 `#trial`을 붙이면 아직 열려요. 필요 없으면 `v-trial` 부분과 `TR` 스크립트를 지워도 돼요.
- 프롤로그의 "이어하기"는 브라우저의 localStorage에 저장해요. 다른 기기나 브라우저와는 공유되지 않아요.
- 파일을 css, js로 나누는 정리는 아직 하지 않았어요. 나눌 때는 원본을 먼저 커밋하고, 분리는 별도 커밋으로 하면 되돌리기 쉬워요.
