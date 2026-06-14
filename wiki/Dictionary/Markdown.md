# Markdown (마크다운)

마크다운(Markdown)은 텍스트 기반의 가벼운 마크업 언어로, 일반 텍스트 문서의 서식을 쉽게 지정할 수 있도록 설계되었습니다. 오늘날 마크다운은 기술 문서 작성, 블로그, 위키, 그리고 [[wiki/Concepts/Obsidian|Obsidian]]과 같은 개인 지식 관리 도구에서 널리 사용되고 있습니다.

---

## 1. 역사 및 파편화

* **2004년 탄생**: 존 그루버(John Gruber)가 아론 스와츠(Aaron Swartz)와의 협업을 통해 개발했습니다. 초기 설계 목적은 단순하고 읽기 쉬운 이메일 형식의 마크업을 만드는 것이었습니다. ([Daring Fireball 프로젝트 페이지](https://daringfireball.net/projects/markdown/))
* **2009년 파편화**: 마크다운의 인기가 높아지면서 여러 플랫폼과 툴체인에서 각자만의 확장 기능을 추가하기 시작했습니다. 
  * 예를 들어, GitHub는 표(Table) 작성 및 코드 구문 강조(Syntax Highlighting) 기능을 자체적으로 추가했고, 여러 위키 엔진들도 고유의 마크업 구문을 결합하면서 호환성 문제가 대두되었습니다.

---

## 2. 마크다운 표준화 노력

### 2-1. CommonMark (2014년~)
파편화된 마크다운 구문을 표준화하여 사양(Specification)을 엄격하게 정의하려는 프로젝트입니다.
* 헬싱키 대학교의 철학 교수이자 Pandoc 개발자인 존 맥팔레인(John MacFarlane, jgm) 등이 참여하여 주도했습니다.
* 제목, 본문, 목록, 강조 등 마크다운의 가장 핵심적인 논리 구조를 일관되게 파싱할 수 있는 표준 명세서(Spec 0.31.2 등)를 개발해 오고 있습니다.
* 관련 링크: [CommonMark 홈페이지](https://commonmark.org/) / [Pandoc GitHub](https://github.com/jgm/pandoc)

### 2-2. GFM (GitHub Flavored Markdown, 2017년~)
GitHub 서비스 내에서 사용하기 위해 개발된 마크다운 확장 구문입니다. 현재 개발자 생태계에서 가장 표준적으로 널리 쓰이는 마크다운 버전 중 하나입니다.
* **구조**: CommonMark 사양을 전적으로 수용하면서, 협업에 필요한 기능들을 **확장 문법(Extensions)**으로 얹은 형태입니다.
* **대표적인 추가 문법**:
  * **표(Tables)**
  * **작업 목록(Task Lists)**: `- [ ]` 또는 `- [x]` 형태의 체크리스트
  * **취소선(Strikethrough)**: `~~텍스트~~`
  * **자동 링크(Autolinks)**: 웹 주소를 그대로 쓰면 자동으로 하이퍼링크 처리
* 관련 링크: [GitHub 기본 쓰기 및 서식 명세](https://docs.github.com/ko/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) / [GFM Spec](https://github.github.com/gfm/)

---

## 3. 마크다운과 Obsidian
[[wiki/Concepts/Obsidian|Obsidian]]은 마크다운 파일(`.md`)을 로컬 파일 시스템에 그대로 저장하는 **Local-first** 지식 관리 도구입니다. GFM을 기본적으로 완벽히 지원하며, 이중 대괄호(`[[링크]]`)를 통한 페이지 간의 위키 스타일 연결과 같은 추가적인 확장 마크업 문법을 지원합니다.

---

## 4. References & Sources (근거 자료)

* [[refined_MyNote/1 md, Obsidian, llm-wiki.md|refined_MyNote/1 md, Obsidian, llm-wiki.md]]: 존 그루버의 마크다운 탄생 배경, 2009년 파편화 이슈, CommonMark 및 GFM 표준화 역사, 존 맥팔레인(jgm)과 Pandoc 정보.
* [[Clippings/GitHub Docs. GitHub 설명서 시작하기 - GitHub 문서.md|Clippings/GitHub Docs. GitHub 설명서 시작하기 - GitHub 문서.md]]: GitHub 쓰기 및 서식 구문 링크 참조.
