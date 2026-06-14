
## Markdown

### 역사
* 2004 존 그루버 ([daringfireball.net/projects/markdown/](https://daringfireball.net/projects/markdown/))
* 2009 파편화 (Github는 표, 코드 하이라이팅 기능을 자체 추가, Wiki는 별도 문법 사용.)
* 2014 CommonMark: 표준 구문 제정. 제목, 본문, 목록, 강조 등 
* 2017 GFM: CommonMark 수용 + 확장 문법. 표, 취소선, 작업목록, 자동링크 등
* 2020 Obsidian ←()

### Common Mark 문법
* [Home](https://commonmark.org/) / [Help(ref.)](https://commonmark.org/help/), [Tutorial](https://commonmark.org/help/tutorial/), [Demo](https://spec.commonmark.org/dingus/), [Spec](https://spec.commonmark.org/)(ver [0.31.2](https://spec.commonmark.org/0.31.2/))
* [Github](https://github.com/commonmark) / [Spec](https://github.com/commonmark/commonmark-spec) 
* by John MacFarlane [Github/jgm](https://github.com/jgm) / [pandoc](https://github.com/jgm/pandoc) (markup converter)

### GFM 문법
* 공식문서 [Docs](https://docs.github.com/ko) / [get-started](https://docs.github.com/ko/get-started) / [writing-on-github](https://docs.github.com/ko/get-started/writing-on-github) 및 [GFM Spec](https://github.github.com/gfm/) 

### Obsidian 문법
* ㅁㄴㄹ

## Obsidian
* 개인 지식 관리(PKM) 및 Note taking 앱. 2020 베타, 2022 정식.
* 어원은 생각의 단단한 결정체. (또는 MS게임 마크 흑요석...) by 아웃라이너 Dynalist 개발자.
* Local-first(↔ Evernote, Notion) 및 Zettelkasten(Second Brain)에서 시작.
* SW Plug-in 생태계 갖춤. 데이터 주권 강조. 

### 설치



### 시작
### 보관함(Vault) 관리
* 새 보관함 생성
	* 로컬 보관함 생성
		* 보관함 이름(A) = Root 폴더명 (한글 가능하나, 안전하게 영숫자_- 위주로)
		* 위치(B) = 위 폴더의 생성 위치. 생성 후 `B/A/.obsidian/` 메타데이터 폴더 생성됨. 
* 보관함 폴더 열기
	* 열기→ 폴더(보관함) 선택→ 편집 창 열림
		* .obsidian 폴더 있는 보관함 폴더 선택
		* 아무 폴더 선택하면 위 보관함 생성과 같아짐.
		* 보관함 속 보관함도 가능한 듯. (굳이?)
* Obsidian sync: 아직 안 써봄. 
* 개별 보관함 메뉴(≡)
	* 보관함ID 확인, 보관함ID 유지한 채 이름변경, 이동 가능.  
	* 목록에서 삭제 - 삭제해도 실제 폴더와 메타데이터는 보존. (탐색기에서 별도 삭제)
		* 외부에서 폴더 먼저 삭제시, 보관함 열지 못했다는 메시지 뜸.



## LLM Wiki
* Github: [Andrej karpathy](https://gist.github.com/karpathy) / [llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 
	* 구조: `Raw/`원본(by휴먼) + `Wiki/`정리(by에이전트) + `Schema/`규칙
	* 명령: `Ingest`(섭취. raw→wiki) + `Query`(질의. wiki 기반 답변) + `Lint`(오류검사) 
	* Graphify:
		* 링크 수작업 점검: Obsidian의 그래프 확인. 
	* 팁. Query 성능 높이기
		* 관심사별 Vault 분리
		* 목적·산출물 고려하기
* CLI 도구 실행위치 = Git 프로젝트 폴더 = Obsidian Vault 
* AI Agent 사용법: Context 주입법
	* 직접 주입 (add context)
		* @ (Mention) : 참조할 부분 명시. @Filename, CodeBlock, Folder, Git이력 등.
		* / (Action / Slash cmd) : 사전 정의된 단축 명령어. 정형화된 작업의 명령 짧아짐. 
		* Browser : 웹검색 or 지정URL 내용 참조. 최신 정보 획득. 
		* Media : 비전. 이미지, 스크린샷 참조. OCR로 내용 확인 및 UI layout 에러 확인.
		* 모델에 따라, 그냥 자연어로 blabla 말해도, 의도 잘 알아들을 수 있음. 
	* AGENTS.md (url) : 폴더에 들어온 Agent가 가장 먼저 읽는 파일.
		* [Claude](https://docs.claude.com/en/docs/claude-code/memory), [OpenAI](https://developers.openai.com/codex/guides/agents-md), [Github/nvk](https://github.com/nvk/llm-wiki), 
* LLM Wiki 설치법
	* URL 붙여넣고, "어떻게 써야 해?" 질문. 
* 관련 논문
	* Wiki-memory Compile, Evaluate, Refine ([arxiv](https://arxiv.org/abs/2605.07068))