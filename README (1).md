# 📰 CEEM Research Highlights 관리 가이드 

> 이 문서는 CEEM Research Highlights GitHub 저장소의 관리자를 위한 안내서입니다.
> 코딩을 전혀 몰라도 이 문서만 따라 하면 웹진을 발간할 수 있습니다.

---

## 📁 저장소 구조 한눈에 보기

```
ceem-webzine/
│
├── 🚫 index.html          ← 절대 건드리지 마세요
├── 🚫 style.css           ← 절대 건드리지 마세요
├── 🚫 main.js             ← 절대 건드리지 마세요
│
├── ✅ data.json           ← 새 호 발간 시 업데이트하는 파일 (현재 최신호)
│
├── assets/
│   └── images/            ← (선택) 논문 관련 이미지 저장 폴더
│
└── archives/              ← 과거호 JSON 파일 보관 폴더
    ├── 2025-01.json       ← 2025년 첫 번째 호
    ├── 2025-02.json       ← 2025년 두 번째 호
    └── ...
```

---

## 🚫 절대 건드리면 안 되는 파일

아래 세 파일은 웹진의 뼈대입니다. **내용을 수정하면 웹사이트 전체가 깨질 수 있습니다.**

| 파일 | 역할 |
|------|------|
| `index.html` | 웹진의 전체 틀(레이아웃) |
| `style.css` | 디자인, 색상, 글꼴 등 꾸미기 |
| `main.js` | 데이터를 읽어서 화면에 표시하는 프로그램 |

> ✅ **관리자가 수정하는 파일은 `data.json` 하나뿐입니다.**

---

## 📂 과거호 파일 이름 규칙 (archives 폴더)

웹진은 **비정기 발행**이므로 파일 이름을 **년도-발행순서** 형식으로 지어주세요.

### 규칙

```
YYYY-NN.json
```

### 예시

| 파일명 | 의미 |
|--------|------|
| `2025-01.json` | 2025년 첫 번째 호 |
| `2025-02.json` | 2025년 두 번째 호 |
| `2026-01.json` | 2026년 첫 번째 호 |
| `2026-02.json` | 2026년 두 번째 호 |

> 월이 아닌 **발행 순서**로 번호를 매기므로, 발간 간격이 불규칙해도 일관되게 관리할 수 있습니다.

---

## ✍️ 신간호 발간 방법 (단계별)

### 1단계 — `data.json` 수정하기

`data.json` 파일이 현재 웹진에 표시되는 내용의 전부입니다.

1. GitHub에서 `data.json` 파일을 클릭합니다.
2. 우측 상단 **연필 아이콘(✏️ Edit)** 을 클릭합니다.
3. 아래 구조를 참고하여 내용을 수정합니다.
4. 수정이 끝나면 **`Commit changes`** 버튼을 눌러 저장합니다.

---

### `data.json` 구조 설명

```json
{
  "issueInfo": {
    "vol": "Vol. 13",
    "issue": "No. 1",
    "date": "February 2026",
    "editorsNote": "이번 호 에디터 노트 내용을 여기에 씁니다."
  },
  "citationTip": {
    "intro": "CEEM 논문을 인용하실 때는 아래 형식을 따라 주세요.",
    "format": "저자명. 논문 제목. Clin Exp Emerg Med. 발행연도;권(호):시작페이지-끝페이지. doi:DOI번호",
    "example": "Hong GD, et al. 논문 제목. Clin Exp Emerg Med. 2026;13(1):1-10. doi:10.xxxx/xxxxx",
    "note": "※ 추가 안내 사항이 있으면 여기에 씁니다. 없으면 이 줄을 지워도 됩니다."
  },
  "papers": [
    {
      "badges": ["original-article"],
      "yearInfo": "2026; 13(1): 1-10",
      "title": "논문 제목을 여기에 입력",
      "author": "Hong GD, Kim JS, Lee HK",
      "abstract": "논문 초록 내용을 여기에 입력합니다.",
      "pearl": "이 논문의 핵심 한 줄 요약 문장을 여기에 씁니다.",
      "doiLink": "https://doi.org/10.xxxx/xxxxx"
    },
    {
      "badges": ["review-article"],
      "yearInfo": "2026; 13(1): 11-25",
      "title": "두 번째 논문 제목",
      "author": "Park SH, Choi MJ",
      "abstract": "두 번째 논문 초록.",
      "pearl": "두 번째 논문 핵심 요약.",
      "doiLink": "https://doi.org/10.xxxx/xxxxx"
    }
  ]
}
```

### 각 항목 설명

| 항목 | 설명 |
|------|------|
| `vol` / `issue` | 권호 정보 (헤더에 표시됨) |
| `date` | 발간 연월 (헤더에 표시됨) |
| `editorsNote` | 에디터 노트 본문 |
| `citationTip.intro` | 인용팁 섹션 안내 문구 |
| `citationTip.format` | 인용 형식 설명 |
| `citationTip.example` | 인용 예시 (선택사항 — 없으면 줄 삭제) |
| `citationTip.note` | 추가 안내 문구 (선택사항 — 없으면 줄 삭제) |
| `badges` | 논문 유형 배지. `original-article`, `review-article`, `case-report`, `systematic-review` 등 |
| `yearInfo` | 논문 출판 연도 및 권호 페이지 정보 |
| `title` | 논문 제목 |
| `author` | 저자명 |
| `abstract` | 초록 |
| `pearl` | 핵심 요약 한 줄 (PEARL 박스에 표시됨) |
| `doiLink` | 논문 DOI 링크 (Full Text / View PDF 버튼에 연결됨) |

> 논문을 추가하려면 `{ ... }` 블록 전체를 복사해서 마지막 논문 뒤에 `, ` 를 붙이고 붙여넣기 하면 됩니다.

---

### 2단계 — 웹진 발행 확인

`data.json` 저장 후 약 1~2분 뒤에 아래 주소에서 확인합니다.

```
https://ceem-webzine.github.io/ceem-webzine/
```

---

## 🗂️ 새 호 발간 시 이전 호를 Archive로 보관하는 방법

새 호를 올리기 **직전에** 아래 순서를 따라 이전 호를 archive에 저장합니다.

### 순서

**① 현재 `data.json` 내용을 복사합니다**
- GitHub에서 `data.json`을 열고 전체 내용을 복사합니다 (`Ctrl+A` → `Ctrl+C`)

**② `archives/` 폴더에 새 파일을 만듭니다**
- `archives/` 폴더 클릭 → `Add file` → `Create new file`
- 파일 이름을 `2025-01.json` 형식으로 입력합니다 (해당 호의 년도-발행번호)
- 복사한 내용을 붙여넣기 합니다
- **`Commit changes`** 를 눌러 저장합니다

**③ 그 다음 `data.json`을 새 호 내용으로 업데이트합니다**

---

## 🔗 과거 호 열람 주소

과거 호는 아래와 같이 주소 끝에 `?issue=년도-발행번호` 를 붙이면 볼 수 있습니다.

```
https://ceem-webzine.github.io/ceem-webzine/?issue=2025-01
https://ceem-webzine.github.io/ceem-webzine/?issue=2025-02
https://ceem-webzine.github.io/ceem-webzine/?issue=2026-01
```

레이아웃은 최신호와 완전히 동일하게 표시됩니다.

---

## 📋 호수별 주소 목록 관리 (GitHub Wiki 활용)

매 호 주소를 체계적으로 기록하고 싶다면 **GitHub Wiki**를 활용하세요.

### Wiki 시작하기

1. 저장소 상단 탭에서 **`Wiki`** 를 클릭합니다.
2. **`Create the first page`** 를 클릭합니다.
3. 아래 예시처럼 호수별 주소를 기록합니다.
4. **`Save page`** 를 눌러 저장합니다.

### Wiki 작성 예시

```
# CEEM Research Highlights Archive 목록

| 호수 | 발간일 | archive 파일명 | 주소 |
|------|--------|----------------|------|
| Vol.13 No.2 | 2026년 4월 | 2026-02.json | https://ceem-webzine.github.io/ceem-webzine/?issue=2026-02 |
| Vol.13 No.1 | 2026년 2월 | 2026-01.json | https://ceem-webzine.github.io/ceem-webzine/?issue=2026-01 |
| Vol.12 No.4 | 2025년 12월 | 2025-04.json | https://ceem-webzine.github.io/ceem-webzine/?issue=2025-04 |
```

> 새 호를 발간할 때마다 Wiki에 한 줄씩 추가해두면, 나중에 특정 호를 찾을 때 편리합니다.

---

## ✅ 발간 체크리스트

새 호 발간 전 아래 순서대로 진행하세요.

- [ ] 현재 `data.json`을 `archives/YYYY-NN.json`으로 복사해 저장했는가?
- [ ] `data.json`을 새 호 내용으로 업데이트했는가?
- [ ] 웹사이트에서 정상적으로 표시되는지 확인했는가?
- [ ] GitHub Wiki에 새 호 주소를 추가했는가?

---

## ❓ 문제가 생겼을 때

| 증상 | 원인 및 해결 |
|------|-------------|
| 웹진이 텅 비어 있음 | `data.json` 문법 오류. 쉼표(`,`)나 따옴표(`"`)가 빠진 곳이 있는지 확인 |
| 과거 호 링크가 안 열림 | `archives/` 폴더에 해당 JSON 파일이 있는지 확인 |
| 수정 후 반영이 안 됨 | GitHub Pages 배포는 최대 2분 소요. 기다린 후 새로고침 |

---

*이 가이드는 CEEM Research Highlights 관리자 인계용 문서입니다.*

Created by 허세진 | CEEM, 2026
