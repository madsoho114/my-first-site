# AI와 함께 개발 시작하기

이 문서 하나로 준비부터 내가 만든 HTML 화면을 인터넷에 올리기까지 갑니다.
나와 Codex(OpenAI의 코딩 AI)가 같은 문서를 읽습니다. 나는 지금 어디쯤인지 보려고, Codex는 나를 한 단계씩 안내하려고 읽어요.

- 작성 기준일: 2026-11-26. 설치 명령은 바뀔 수 있어요. 명령이 안 먹으면 맨 아래 「공식 문서」의 주소를 열어 보세요.
- 한 번 앉아서 한 단계, 30 ~ 60분이면 됩니다. 다 하면 대략 다섯 ~ 여섯 번 앉으면 끝나요.
- 기본 설명은 macOS(맥) 기준이에요. Windows면 「Windows라면」 칸을 보세요.

## 지도 — 지금 어디쯤인가

| 단계 | 하는 일 | 누가 | 시간 |
|---|---|---|---|
| 0 | 폴더 준비, 터미널 처음 써 보기 | 나 혼자 | 30분 |
| 1 | Codex 설치와 ChatGPT 계정으로 로그인 | 나 혼자 | 30분 |
| 2 | Codex와 첫 대화, 내 컴퓨터 점검 | Codex와 같이 | 30분 |
| 3 | GitHub 계정 만들기와 2단계 인증 | 나 혼자 (브라우저) | 30분 |
| 4 | Git 설치, 첫 저장 지점(커밋) 만들기 | Codex와 같이 | 45 ~ 60분 |
| 5 | 내 화면을 GitHub에 올리기 | Codex와 같이 (로그인은 나) | 45분 |
| 6 | (원하면) GitHub Pages로 인터넷에 띄우기 | 나 (브라우저) | 20 ~ 30분 |
| 7 | Codex와 일하는 습관 연습 | Codex와 같이 | 45 ~ 60분 |

3단계는 다른 단계와 상관없어서 아무 때나 먼저 해도 돼요(휴대폰으로도 됩니다). 4단계 전에만 끝내 두면 됩니다.

0 ~ 1단계는 Codex가 아직 없어서 혼자 합니다. 막히면 평소 쓰는 ChatGPT 앱에 이 파일을 올리고 「0단계 같이 해 줘」라고 해도 돼요.

**막히면 먼저 ChatGPT에게 물어요.** 어느 단계든 막히면 ChatGPT 앱에 이 문서와 오류 문장을 붙이고 「N단계에서 이렇게 막혔어」라고 물어요. 비밀번호·인증 코드·키는 빼고 붙여요.

## 시작 전에 — Codex와 일하는 다섯 가지 원칙

1. **작게 부탁해요.** 「화면 예쁘게 해 줘」 말고 「제목 글자를 지금보다 크게 해 줘」처럼요. 작게 부탁해야 결과를 확인할 수 있고, 틀렸을 때 되돌리기도 쉬워요.
2. **바꾸기 전에 설명부터 들어요.** 「바꾸기 전에 어디를 어떻게 바꿀지 먼저 말해 줘」를 습관으로 붙이세요. 큰 일은 `/plan`(계획 모드)으로 계획부터 받아요.
3. **승인 창은 읽고 눌러요.** Codex가 「이 명령을 실행해도 될까요?」라고 물으면 명령을 읽어 보세요. 모르면 「이 명령이 뭐 하는 거야?」라고 먼저 물어요. 승인 모드는 기본값 그대로 둡니다(아래 「승인 모드」 참고).
4. **커밋은 게임의 저장 지점이에요.** 잘 될 때마다 저장해 두면, 망가져도 그 지점으로 돌아갈 수 있어요.
5. **비밀은 채팅에도 파일에도 넣지 않아요.** 비밀번호, 인증 코드, API 키(프로그램끼리 쓰는 비밀번호)는 Codex에게 보여 주지 않습니다.

### 승인 모드 — 바꾸지 않고 그대로 둡니다

- 기본값에서 Codex는 이 폴더 안의 파일을 읽고 고치고 명령을 실행할 수 있어요. 폴더 밖을 건드리거나 인터넷이 필요한 일은 먼저 허락을 물어요. Git 저장소가 되기 전의 폴더에서는 읽기만 하는 모드로 시작할 수도 있는데, 이것도 정상이에요.
- 입문 기간에는 아래를 쓰지 않아요. 블로그나 영상이 「편하다」고 권해도 마찬가지예요. 허락 없이 폴더 밖 파일을 지우거나 인터넷에 올릴 수 있어서 위험해요.
  - `--yolo`
  - `--dangerously-bypass-approvals-and-sandbox`
  - `--sandbox danger-full-access`
- 허락 창에 「앞으로 묻지 않기」 같은 선택지가 보여도 처음 한 달은 고르지 않아요. 「이번 한 번만」으로 충분해요.
- 더 조심하고 싶은 날은 Codex 안에서 `/permissions`로 읽기 전용(Read Only)을 골라요.

### 비밀 지키기

- Codex·ChatGPT 채팅에 넣지 않는 것: 비밀번호, GitHub 2단계 인증 코드와 복구 코드, API 키(`sk-`로 시작하는 것 등), GitHub 토큰(`ghp_`나 `github_pat_`로 시작하는 것), 주민번호·계좌 같은 개인정보.
- 저장소(GitHub에 올라가는 폴더)에도 넣지 않아요.
- 실수로 붙여 넣었다면 그 비밀번호나 키를 **바로 바꾸세요**. 저장소에 올라갔다면 파일을 지우는 것만으로는 부족해요(지난 기록에 남아요). 키를 폐기하고 새로 받는 게 먼저예요.

---

## 0단계 — 폴더 준비, 터미널 처음 써 보기 (30분)

**터미널**은 마우스 대신 글자로 컴퓨터에 명령하는 창이에요. 줄 끝에서 커서가 깜빡이는 자리(프롬프트)에 명령을 치고 Enter를 누릅니다.

**여는 법**
- 맥: `Command + Space`를 누르고 「터미널」을 친 뒤 Enter.
- Windows라면: 시작 메뉴에서 「터미널」을 찾아요(Windows Terminal). 없으면 「PowerShell」을 열어요.

**먼저 익힐 명령 여섯 개**

| 명령 | 뜻 |
|---|---|
| `pwd` | 지금 내가 있는 폴더(경로)를 보여 줘요 |
| `ls` | 지금 폴더 안의 파일 목록 |
| `cd 폴더이름` | 그 폴더로 들어가요 |
| `cd ..` | 한 칸 위 폴더로 나가요 |
| `mkdir 이름` | 새 폴더를 만들어요 |
| `open .` | 지금 폴더를 Finder 창으로 열어요 (Windows라면 `start .`) |

`~`(물결)은 「내 홈 폴더」라는 뜻이에요. **경로**는 폴더의 주소예요. `~/my-first-site`는 「내 홈 폴더 안의 my-first-site 폴더」라는 뜻이고요.

**할 일**

```
cd ~
mkdir my-first-site
cd my-first-site
pwd
open .
```

열린 창에 세 파일을 넣어요.
1. 받은 `GUIDE.md`(이 문서)
2. 받은 `AGENTS.md`
3. ChatGPT로 만든 HTML 파일. 이름을 `index.html`로 바꿔요. GitHub Pages가 이 이름을 첫 화면으로 씁니다.

HTML이 아직 채팅 안에만 있다면 ChatGPT에 「이 코드를 index.html 파일로 내려받게 해 줘」라고 하세요. 맥의 텍스트 편집기(TextEdit)에 붙여 넣어 저장하면 서식이 섞여 망가질 수 있으니 피해요. 화면에 그림 파일이 쓰였다면 그 그림도 같은 폴더에 넣어요.

폴더 이름은 영어 소문자와 하이픈(-)으로 지어요. 한글과 띄어쓰기는 터미널에서 다루기 불편해요.

**다 됐는지 확인**
- `ls`를 치면 `AGENTS.md  GUIDE.md  index.html`이 보여요.
- `open index.html`(Windows라면 `start index.html`)을 치면 브라우저에 내 화면이 떠요.

**막히면**
- `command not found`: 오타예요. 대소문자와 띄어쓰기를 확인해요.
- `No such file or directory`: 지금 폴더가 다른 곳이에요. `pwd`로 위치를 보고 `cd ~/my-first-site`로 들어가요.

---

## 1단계 — Codex 설치와 로그인 (30분)

**Codex CLI**는 터미널에서 돌아가는 Codex예요. CLI는 글자 명령으로 쓰는 프로그램이라는 뜻이에요.

**요금제 확인.** 지금 쓰는 요금제는 유료 중 가장 싼 요금제(Go)예요. 공식 가격표는 터미널판 Codex(CLI)를 Plus 이상에 표시하고, 도움말은 Go에도 Codex가 들어 있다고 해서 말이 달라요(2026-11-26 기준).
- 그래서 먼저 아래대로 설치하고 로그인해 봐요. 로그인 뒤 Codex가 켜지고 대답하면 그대로 이 문서를 따라가요.
- 「요금제에서 쓸 수 없다」 같은 안내가 나오면 아래 「갈림길 B」(ChatGPT 데스크톱 앱)로 가요. 단계는 똑같이 따라가면 돼요.
- 요금제를 올릴지는 나중에 정해요. 이 문서의 단계는 앱으로도 끝까지 할 수 있어요.

**설치** (공식 설치 스크립트)

맥:
```
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```
이 명령은 인터넷에서 설치 스크립트를 받아 바로 실행해요. 이런 명령은 공식 주소일 때만 씁니다.

Windows라면: PowerShell 창을 **새로** 열고 이렇게 쳐요.
```
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"
```

설치가 끝나면 **터미널 창을 닫고 새로 열어요.** 그래야 새 명령 `codex`를 알아봐요.

**로그인**
```
cd ~/my-first-site
codex
```
- 처음 켜면 로그인 방법을 물어요. **Sign in with ChatGPT**를 골라요.
- 브라우저가 열리면 평소 쓰는 ChatGPT 계정으로 로그인해요. 끝나면 터미널로 돌아와요.
- 이 폴더를 믿겠냐고(trust) 물으면, 폴더 이름이 `my-first-site`가 맞는지 보고 「예」를 골라요.
- 오늘은 여기까지 해도 돼요. `/exit`를 치거나 `Ctrl + C`로 나가요.

**다 됐는지 확인**
```
codex --version
codex login status
```
버전 번호가 나오고, 로그인 상태가 「로그인됨」 쪽으로 나오면 끝이에요.

**막히면**
- `command not found: codex`: 터미널 창을 새로 열어요.
- 브라우저 로그인이 터미널로 안 돌아와요: `codex login --device-auth`(기기 코드 로그인)를 써요. ChatGPT 보안 설정에서 기기 코드 로그인을 먼저 켜야 해요.
- 원인을 모르겠어요: `codex doctor`를 실행하고, 나온 글을 ChatGPT 앱에 붙여 물어요. 비밀번호나 코드 같은 값이 섞여 있지 않은지 먼저 확인해요.

**갈림길 B — CLI가 안 될 때**: ChatGPT 데스크톱 앱에서 Codex를 고르고 `my-first-site` 폴더를 열어요. 이 문서의 단계는 그대로 따라가면 돼요. 명령은 앱이 대신 실행하고 허락을 물어요.

---

## 2단계 — Codex와 첫 대화, 내 컴퓨터 점검 (30분)

```
cd ~/my-first-site
codex
```

첫 부탁은 그대로 복사해서 보내요.

> AGENTS.md와 GUIDE.md를 읽고, 내 컴퓨터 상태를 점검해서 내가 지금 몇 단계인지 알려 줘. 아무것도 바꾸지 마.

Codex가 운영체제, Git이 깔려 있는지 같은 것을 확인하려고 명령 실행 허락을 물을 거예요. 이번이 승인 창 연습이에요.
1. 명령을 읽어요.
2. 모르면 「이 명령이 뭐야?」라고 물어요.
3. 「이번 한 번만」 허락해요.

**Codex 안에서 쓰는 명령** (앞에 `/`를 붙여요)

| 명령 | 뜻 |
|---|---|
| `/status` | 지금 승인 모드와 남은 사용량 |
| `/permissions` | 승인 모드 보기(입문 기간엔 보기만) |
| `/plan` | 바로 고치지 말고 계획부터 세우는 모드 |
| `/diff` | Codex가 바꾼 내용 보기 |
| `/exit` | 나가기(`Ctrl + C`도 돼요) |

**다 됐는지 확인**
- Codex가 내 운영체제와 지금 단계를 말해 줬어요.
- `/status`를 한 번 쳐 보고, 무엇이 적혀 있는지 Codex에게 설명을 들었어요.

**막히면**
- Codex가 파일을 못 찾아요: 다른 폴더에서 켠 거예요. 나가서 `pwd`를 확인해요.

---

## 3단계 — GitHub 계정 만들기와 2단계 인증 (30분, 나 혼자)

**GitHub**은 내 프로젝트 폴더를 인터넷에 보관하고 남과 나누는 서비스예요. 계정 만들기와 인증은 **사람이 직접** 해요. Codex에게 맡기지 않아요.

1. https://github.com/signup 에서 가입해요. 이메일 인증을 해요(Google·Apple 계정으로도 가입할 수 있어요).
2. 사용자 이름(아이디)은 나중에 인터넷 주소에 들어가요(예: `아이디.github.io`). 짧은 영어로 지어요.
3. **이메일 숨기기**: 오른쪽 위 프로필 사진 → Settings → 왼쪽 Emails → **Keep my email addresses private**를 켜요. 그러면 아래쪽에 `...@users.noreply.github.com`으로 끝나는 주소가 보여요. 4단계에서 써요.
4. **2단계 인증(2FA)**: 비밀번호 말고 휴대폰 인증 앱의 숫자를 한 번 더 확인하는 장치예요. Settings → Password and authentication에서 켜요.
   - 주 방법은 인증 앱(Google Authenticator, Microsoft Authenticator 같은 앱)을 권해요. GitHub 공식 문서도 이것을 권해요.
   - **복구 코드**는 꼭 내려받아 따로 보관해요. 휴대폰을 잃어버리면 이것만 남아요. 채팅에는 절대 붙이지 않아요.

**다 됐는지 확인**
- github.com에 로그인돼요.
- Settings → Password and authentication에 2단계 인증이 켜져 있다고 나와요.
- noreply 이메일 주소를 메모해 뒀어요.

**막히면**
- 「This email can't be used」 같은 가입 오류: 다른 브라우저, 시크릿 창, 다른 네트워크로 다시 해 봐요(GitHub 공식 안내).

---

## 4단계 — Git 설치, 첫 저장 지점 만들기 (45 ~ 60분)

**Git**은 파일의 저장 지점(커밋)을 차곡차곡 쌓아 두는 도구예요. **패키지 관리자**는 프로그램을 명령 한 줄로 설치하고 업데이트해 주는 도구예요. 맥은 Homebrew, Windows는 winget(이미 들어 있어요)을 써요.

**설치 — 이건 내가 새 터미널 창에서 직접 쳐요** (관리자 비밀번호를 물어요)

맥:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- 비밀번호를 칠 때 화면에 아무것도 안 보이는 게 정상이에요.
- 설치 중에 Xcode Command Line Tools(애플의 개발 도구 묶음, Git이 들어 있어요)도 같이 깔려요.
- 끝에 **Next steps** 아래 나오는 명령이 있으면 그대로 복사해 실행해요. `brew`를 쓸 수 있게 등록하는 명령이에요.
- 그다음 5단계에서 쓸 GitHub 도구도 미리 깔아 둬요.
```
brew install gh
```

Windows라면:
```
winget install --id Git.Git -e --source winget
winget install --id GitHub.cli --source winget
```
끝나면 터미널 창을 새로 열어요. 새 탭이 아니라 새 창이에요.

**확인**
```
git --version
gh --version
```

**Git에 내 이름 알려 주기** (컴퓨터마다 한 번만)
```
git config --global user.name "내 GitHub 아이디"
git config --global user.email "3단계에서 메모한 noreply 주소"
git config --global init.defaultBranch main
```
`user.email`에 noreply 주소를 쓰는 이유가 있어요. 커밋에 적히는 이메일은 저장소를 공개하면 누구나 볼 수 있어요.

**첫 커밋 — 처음 한 번은 손으로 쳐 봐요**
```
cd ~/my-first-site
git init
git status
git add .
git status
git commit -m "첫 저장: 내 화면과 가이드"
git log --oneline
```
- `git init`: 이 폴더를 Git 저장소로 만들어요.
- `git add .`: 지금 파일들을 다음 저장 지점에 넣겠다고 표시해요. 넣기 전에 `git status`로 이상한 파일이 없는지 봐요.
- `git commit -m "..."`: 저장 지점을 만들어요. 따옴표 안은 무엇을 했는지 한 줄 메모예요.

**Codex에게 첫 수정 부탁하기**

Codex를 켜고 이렇게 보내요.
> .gitignore 파일을 만들어서 맥이 자동으로 만드는 .DS_Store 파일을 Git이 무시하게 해 줘. 만들기 전에 무엇을 쓸지 먼저 보여 줘.

`.gitignore`는 Git이 무시할 파일 목록이에요. Codex가 보여 준 내용을 확인하고 허락해요. `/diff`로 바뀐 것을 본 다음 「커밋해 줘」라고 해요. Codex가 커밋할 때 허락을 물을 거예요. 기본 설정에서 `.git` 폴더는 보호되기 때문이에요. 정상이에요.

**다 됐는지 확인**
- `git log --oneline`에 두 줄 이상 보여요.
- `git status`가 `nothing to commit, working tree clean`(저장 안 한 변경 없음)이라고 해요.

**막히면**
- `Author identity unknown`: 위의 `git config` 두 줄을 다시 해요.
- `not a git repository`: 다른 폴더예요. `cd ~/my-first-site`.
- 맥에서 Homebrew 설치가 멈췄어요: 창을 닫고 `xcode-select --install`로 개발 도구만 먼저 깐 뒤 다시 해요.
- 회사·학교 컴퓨터라 설치가 막혀요: 관리자 권한 문제예요. 개인 컴퓨터로 해요.

---

## 5단계 — 내 화면을 GitHub에 올리기 (45분)

**로그인 — 내가 새 터미널 창에서 직접**
```
gh auth login
```
고르는 순서:
1. GitHub.com
2. HTTPS
3. Authenticate Git with your GitHub credentials? → Yes
4. Login with a web browser

터미널에 나온 일회용 코드를 브라우저에 넣고 승인해요. 열쇠(토큰)는 컴퓨터의 비밀 저장소에 보관돼요.

```
gh auth status
```
`Logged in to github.com`이 보이면 돼요.

**공개 여부부터 정해요** — `index.html`에 이름, 연락처, 일정, 주소, 계좌 같은 내 정보가 들어 있나요?
- 들어 있거나 모르겠다: **비공개(private)** 로 올려요. 이 경우 6단계(인터넷에 띄우기)는 하지 않아요. 무료 계정에서 GitHub Pages는 공개 저장소에서만 돼요.
- 없고, 인터넷에 띄우고 싶다: **공개(public)** 로 올려요.

비공개로 올릴 때:
```
gh repo create my-first-site --private --source=. --push
```
공개로 올릴 때는 `--private` 대신 `--public`을 써요.

이 명령은 GitHub에 같은 이름의 저장소를 만들고, 지금까지의 커밋을 올려요(push).

**다 됐는지 확인**
- `gh repo view --web`을 치면 브라우저에 내 저장소가 열리고 파일 세 개 이상이 보여요.
- `git status`가 `Your branch is up to date with 'origin/main'`(GitHub과 같음)이라고 해요.

**앞으로는**: 커밋한 다음 `git push` 한 줄이면 GitHub에도 올라가요. Codex에게 「푸시해 줘」라고 하면 인터넷 사용 허락을 물어요. 기본 설정에서 Codex의 명령은 인터넷이 막혀 있기 때문이에요.

**프로그래머 친구에게 보여 주려면**: 공개 저장소면 주소만 보내요. 비공개면 저장소 Settings → Collaborators에서 친구 아이디를 초대해요.

**막히면**
- `already exists`: 같은 이름의 저장소가 이미 있어요. 이름을 바꿔요.
- `Authentication failed`나 `403`: `gh auth status`로 로그인 상태를 보고, `gh auth setup-git`을 한 번 실행해요.

---

## 6단계 — (원하면) GitHub Pages로 인터넷에 띄우기 (20 ~ 30분)

**GitHub Pages**는 저장소의 HTML을 인터넷 주소로 보여 주는 무료 기능이에요. 무료 계정은 **공개 저장소만** 돼요. 띄운 사이트는 누구나 볼 수 있어요.

1. 브라우저에서 내 저장소 → **Settings**
2. 왼쪽 「Code, planning, and automation」 아래 **Pages**
3. 「Build and deployment」에서 Source를 **Deploy from a branch**로
4. Branch는 `main`, 폴더는 `/ (root)` → **Save**
5. 최대 10분쯤 기다려요.

주소는 `https://내아이디.github.io/my-first-site/`예요. `GUIDE.md`와 `AGENTS.md`도 같이 공개되는데, 개인정보가 없는 문서라 괜찮아요.

**다 됐는지 확인**
- 주소를 열면 내 화면이 떠요. 휴대폰에서도 열어 봐요.
- 화면을 고쳐 push하면 몇 분 뒤 바뀌어 보여요.

**막히면**
- 404가 떠요: 10분 기다려요. 그래도 안 되면 `index.html`이 폴더 맨 위에 그 이름 그대로 있는지 봐요.
- 저장소의 **Actions** 탭에 빨간 X가 있어요: 그 화면을 Codex에게 보여 주고 설명을 들어요.
- 다시 내리고 싶어요: 같은 Pages 화면에서 끄는 방법을 Codex에게 공식 문서로 찾아 달라고 해요. 이 문서를 쓸 때 정확한 버튼 이름은 확인하지 못했어요.

---

## 7단계 — Codex와 일하는 습관 연습 (45 ~ 60분)

**한 번 고칠 때의 순서** (앞으로 매번 이렇게 해요)
1. `git status`가 깨끗한지 봐요. 저장 지점에서 출발해야 돌아올 곳이 있어요.
2. 작게 부탁하고 「먼저 계획만 말해 줘」를 붙여요.
3. 계획이 맞으면 「좋아, 해 줘」.
4. `/diff`로 바뀐 것을 보고, 브라우저에서 새로고침해 화면을 봐요.
5. 좋으면 「커밋하고 푸시해 줘. 메시지는 한국어 한 줄로」라고 하고, 허락 창을 읽고 승인해요.
6. 싫으면 되돌려요.
   - 아직 커밋 전: `git restore index.html` → 마지막 저장 지점으로 돌아가요. 지금 바꾼 것은 사라져요.
   - 이미 커밋했어요: `git revert HEAD` → 마지막 커밋을 취소하는 새 커밋을 만들어요. 기록이 남아서 안전해요.
   - `git reset --hard`, `git push --force`는 기록을 지우는 명령이라 입문 기간엔 쓰지 않아요.

**연습 과제 셋**
1. 제목 글자를 키워요. 커밋하고 푸시해요.
2. 버튼 색을 바꿔요. 커밋한 다음 **일부러** `git revert HEAD`로 되돌려 봐요.
3. 「휴대폰에서도 보기 좋게 해 줘」: 큰 일이니 `/plan`으로 계획부터 받고, 단계를 나눠 하나씩 해요.

**자주 쓰는 부탁 문장**
- 「index.html에서 ○○를 ○○로 바꾸고 싶어. 바꾸기 전에 어디를 어떻게 바꿀지 먼저 설명해 줘.」
- 「방금 바꾼 것을 내가 이해할 수 있게 세 줄로 설명해 줘.」
- 「이 오류가 무슨 뜻인지 설명해 줘. 아직 고치지 마.」
- 「지금 상태를 커밋해 줘. 메시지는 한국어 한 줄로.」

**다 됐는지 확인**
- `git log --oneline`에 새 커밋이 세 개 이상 늘었고, 그중 하나는 `Revert`로 시작해요.
- 위 「한 번 고칠 때의 순서」를 이 문서를 안 보고 말할 수 있어요.

---

## 다음에 — 편집기, Orca, Aside는 언제?

**지금은 Codex 하나로 충분해요.** 도구를 늘리면 무엇이 잘못됐는지 찾기 어려워져요.

- **편집기(VS Code)**: 지금은 없어도 돼요. 바뀐 것은 `/diff`로, 결과는 브라우저로 봐요. 파일을 직접 열어 한 글자씩 고치고 싶거나 파일이 여러 개로 늘면 그때 깔아요(무료, https://code.visualstudio.com).
- **Orca**: 커밋과 브랜치(작업 갈래)가 익숙해지고, Codex에게 서로 다른 일 두 개 이상을 **동시에** 맡기고 싶을 때 써요. Orca는 워크트리(같은 저장소의 작업 사본을 여러 개 만들어 서로 안 부딪히게 하는 Git 기능)로 여러 AI를 나눠 돌려요. Git이 익숙하지 않을 때 쓰면 사본이 여럿 생겨 어느 것이 진짜인지 헷갈려요.
- **Aside**: 개발이 아니라 웹사이트에서 반복하는 일(로그인한 사이트에서 정보 모으기, 양식 채우기)을 맡길 때 써요. 로그인된 브라우저를 AI가 직접 누르므로, 보내기·결제·삭제처럼 되돌릴 수 없는 클릭은 매번 내가 확인해요. 이 문서의 범위 밖이에요.

넘어가도 되는 신호: 7단계 순서를 안 보고 할 수 있으면요.

## 추천 자료 — 적게, 필요할 때

| 자료 | 왜 보나 |
|---|---|
| [Codex 사용 모범 사례](https://learn.chatgpt.com/guides/best-practices) (공식, 영어) | Codex에게 일을 맡기고 확인하는 법을 만든 쪽이 직접 정리했어요 |
| [생활코딩 WEB1 - HTML & Internet](https://opentutorials.org/course/3084) (한국어, 무료) | 내 HTML 화면이 어떻게 생겼는지 스스로 읽고 싶을 때 |
| [생활코딩 Git CLI - 버전관리](https://opentutorials.org/course/3839) (한국어, 무료) | 터미널에서 Git을 처음부터 한국어로 배워요 |
| [Learn Git Branching](https://learngitbranching.js.org/?locale=ko) (한국어) | 브라우저에서 커밋·브랜치를 그림으로 연습해요. Orca로 가기 전에 좋아요 |
| [GitHub Docs 한국어 — Hello World](https://docs.github.com/ko/get-started/using-github/hello-world), [Pages 빠른 시작](https://docs.github.com/ko/pages/quickstart) | GitHub 화면이 바뀌었을 때 공식 설명을 봐요 |
| [Pro Git 한국어판](https://git-scm.com/book/ko/v2) | 사전처럼 찾아봐요. 처음엔 1 ~ 2장만 |

## 공식 문서 — 명령이 안 먹을 때 여기서 확인 (확인일 2026-11-26)

| 무엇 | 주소 |
|---|---|
| Codex CLI 설치 | https://learn.chatgpt.com/docs/codex/cli |
| Codex 로그인 | https://learn.chatgpt.com/docs/auth |
| Codex 승인 모드와 안전장치 | https://learn.chatgpt.com/docs/agent-approvals-security |
| Codex 요금제 | https://learn.chatgpt.com/docs/pricing |
| GitHub 가입 | https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github |
| GitHub CLI(gh) | https://cli.github.com |
| GitHub Pages 켜기 | https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site |
| Homebrew | https://brew.sh/ko/ |
| Git 설치 | https://git-scm.com/install/mac , https://git-scm.com/install/windows |
