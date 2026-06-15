---
title: "llm-wiki"
source: "https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f"
author:
published:
created: 2026-06-14
description: "llm-wiki. GitHub Gist: instantly share code, notes, and snippets."
tags:
  - "clippings"
---
# LLM Wiki Abstract

## asdf


# Ref. Github llm-wiki original 
by Andrej karpathy 안드레 카파시

## LLM Wiki

A pattern for building personal knowledge bases using LLMs.
LLM을 활용하여 개인 지식 기반을 구축하는 패턴.

This is an idea file, it is designed to be copy pasted to your own LLM Agent (e.g. OpenAI Codex, Claude Code, OpenCode / Pi, or etc.). 
Its goal is to communicate the high level idea, but your agent will build out the specifics in collaboration with you.
이 파일은 아이디어 파일이며, OpenAI Codex, Claude Code, OpenCode/Pi 등과 같은 LLM 에이전트에 복사하여 붙여넣도록 설계되었습니다. 
이 파일의 목적은 고수준의 아이디어를 전달하는 것이며, 구체적인 내용은 에이전트가 귀하와 협력하여 구체화할 것입니다.

## The core idea 핵심 아이디어

Most people's experience with LLMs and documents looks like RAG: 
you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. 
This works, but the LLM is rediscovering knowledge from scratch on every question. 
There's no accumulation. 
Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. 
Nothing is built up. 
NotebookLM, ChatGPT file uploads, and most RAG systems work this way.
대부분의 사람들이 LLM(학습 언어 관리자)과 문서를 사용하는 경험은 RAG(랜덤 속성 알고리즘)와 유사합니다. 
파일 모음을 업로드하면 LLM이 질의 시점에 관련 있는 부분을 찾아 답변을 생성합니다. 
이 방식은 작동하지만, LLM은 매 질문마다 처음부터 지식을 재발견해야 합니다. 
지식이 축적되지 않는 것이죠. 
다섯 개의 문서를 종합해야 하는 미묘한 질문을 한다면, LLM은 매번 관련 조각들을 찾아 조합해야 합니다. 
아무것도 축적되지 않는 것입니다. 
NotebookLM, ChatGPT 파일 업로드 방식, 그리고 대부분의 RAG 시스템이 이러한 방식으로 작동합니다.

The idea here is different. 
Instead of just retrieving from raw documents at query time, the LLM **incrementally builds and maintains a persistent wiki** — a structured, interlinked collection of markdown files that sits between you and the raw sources. 
When you add a new source, the LLM doesn't just index it for later retrieval. 
It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. 
The knowledge is compiled once and then *kept current*, not re-derived on every query.
여기서 핵심 아이디어는 다릅니다. 
LLM은 단순히 쿼리 시점에 원시 문서에서 정보를 검색하는 대신, 구조화되고 상호 연결된 마크다운 파일 모음인 영구적인 위키를 점진적으로 구축하고 유지 관리합니다. 이 위키는 사용자와 원시 소스 사이에 위치합니다. 
새로운 소스를 추가하면 LLM은 단순히 나중에 검색할 수 있도록 색인을 생성하는 데 그치지 않습니다. 
소스를 읽고 핵심 정보를 추출하여 기존 위키에 통합합니다. 
즉, 엔티티 페이지를 업데이트하고, 주제 요약을 수정하고, 새로운 데이터가 기존 주장과 모순되는 부분을 표시하고, 진화하는 종합적인 내용을 강화하거나 수정합니다. 
지식은 한 번만 컴파일되면 항상 최신 상태로 유지되며 , 쿼리할 때마다 다시 생성되지 않습니다.

This is the key difference: 
**the wiki is a persistent, compounding artifact.** 
The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. 
The wiki keeps getting richer with every source you add and every question you ask.
핵심적인 차이점은 바로 이것입니다. 
위키는 지속적이고 축적되는 산물입니다. 
상호 참조는 이미 존재하고, 모순되는 부분은 이미 표시되어 있으며, 종합적인 내용은 여러분이 읽은 모든 내용을 반영하고 있습니다. 
위키는 여러분이 자료를 추가하고 질문을 할 때마다 더욱 풍부해집니다.

You never (or rarely) write the wiki yourself 
— the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. 
The LLM does all the grunt work — the summarizing, cross-referencing, filing, and bookkeeping that makes a knowledge base actually useful over time. 

In practice, I have the LLM agent open on one side and Obsidian open on the other. 
The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. 
Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.
위키를 직접 작성하는 경우는 거의 없습니다. 
LLM(학습 관리 담당자)이 모든 것을 작성하고 관리합니다. 
여러분은 자료 수집, 탐색, 그리고 적절한 질문을 던지는 역할을 맡습니다. 
LLM은 요약, 상호 참조, 정리, 그리고 기록 관리와 같은 기본적인 작업을 모두 처리하여 시간이 지남에 따라 지식 기반이 실제로 유용해지도록 만듭니다. 
실제로 저는 한쪽에는 LLM 에이전트를, 다른 쪽에는 Obsidian을 열어 놓고 작업합니다. 
LLM은 대화를 바탕으로 편집 작업을 진행하고, 저는 실시간으로 결과를 확인하며 링크를 따라가고, 그래프 보기를 확인하고, 업데이트된 페이지를 읽습니다. 
Obsidian은 IDE이고, LLM은 프로그래머이며, 위키는 코드베이스입니다.

This can apply to a lot of different contexts. A few examples:
이는 다양한 상황에 적용될 수 있습니다. 몇 가지 예를 들면 다음과 같습니다.

- **Personal**: tracking your own goals, health, psychology, self-improvement — filing journal entries, articles, podcast notes, and building up a structured picture of yourself over time.
- **Research**: going deep on a topic over weeks or months — reading papers, articles, reports, and incrementally building a comprehensive wiki with an evolving thesis.
- **Reading a book**: filing each chapter as you go, building out pages for characters, themes, plot threads, and how they connect. By the end you have a rich companion wiki. Think of fan wikis like [Tolkien Gateway](https://tolkiengateway.net/wiki/Main_Page) — thousands of interlinked pages covering characters, places, events, languages, built by a community of volunteers over years. You could build something like that personally as you read, with the LLM doing all the cross-referencing and maintenance.
- **Business/team**: an internal wiki maintained by LLMs, fed by Slack threads, meeting transcripts, project documents, customer calls. Possibly with humans in the loop reviewing updates. The wiki stays current because the LLM does the maintenance that no one on the team wants to do.
- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives** — anything where you're accumulating knowledge over time and want it organized rather than scattered.

* **개인적인 용도** : 자신의 목표, 건강, 심리 상태, 자기 계발 등을 추적하며 일기, 기사, 팟캐스트 메모 등을 정리하고 시간이 지남에 따라 자신에 대한 체계적인 그림을 그려나갑니다.
- **연구** : 몇 주 또는 몇 달에 걸쳐 특정 주제를 심층적으로 탐구하는 과정으로, 논문, 기사, 보고서를 읽고 점진적으로 발전하는 논지를 바탕으로 포괄적인 위키를 구축해 나가는 것입니다.
- **책을 읽으면서** 각 장을 읽고, 등장인물, 주제, 줄거리, 그리고 그것들이 어떻게 연결되는지 페이지를 만들어 나가는 것처럼 말입니다. 그렇게 하다 보면 결국 풍부한 정보를 담은 위키를 만들게 됩니다. [톨킨 게이트웨이](https://tolkiengateway.net/wiki/Main_Page) 같은 팬 위키를 생각해 보세요. 수천 개의 서로 연결된 페이지로 등장인물, 장소, 사건, 언어 등을 다루고, 수년에 걸쳐 자원봉사자 커뮤니티가 구축한 것입니다. LLM이 모든 상호 참조와 유지 관리를 담당하는 동안, 여러분도 책을 읽으면서 개인적으로 그런 위키를 만들어 나갈 수 있습니다.
- **비즈니스/팀** : LLM(Leadership Leadership Manager)이 관리하는 내부 위키로, 슬랙 스레드, 회의록, 프로젝트 문서, 고객 통화 내용 등이 업데이트됩니다. 필요에 따라 담당자가 업데이트를 검토할 수도 있습니다. LLM이 팀원 중 누구도 하기 싫어하는 유지 관리를 담당하기 때문에 위키는 항상 최신 상태를 유지합니다.
- **경쟁사 분석, 실사, 출장 계획, 강의 노트, 취미 관련 심층 분석** 등 시간이 지남에 따라 축적되는 지식을 흩어지지 않고 체계적으로 정리하고 싶은 모든 것에 적합합니다.

## Architecture 아키텍처

There are three layers:
세 가지 층이 있습니다.

**Raw sources** — your curated collection of source documents. Articles, papers, images, data files. These are immutable — the LLM reads from them but never modifies them. This is your source of truth.
**원본 자료** — 직접 선별한 자료 모음입니다. 논문, 보고서, 이미지, 데이터 파일 등이 포함됩니다. 이러한 자료는 변경 불가능합니다. LLM은 이러한 자료에서 읽기만 할 뿐 절대 수정하지 않습니다. 이것이 바로 여러분이 찾는 진실의 원천입니다.

**The wiki** — a directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, an overview, a synthesis. The LLM owns this layer entirely. It creates pages, updates them when new sources arrive, maintains cross-references, and keeps everything consistent. You read it; the LLM writes it.
**위키는** LLM이 생성한 마크다운 파일의 디렉토리입니다. 요약, 개체 페이지, 개념 페이지, 비교, 개요, 종합 등이 포함됩니다. LLM은 이 계층을 전적으로 관리합니다. 페이지를 생성하고, 새로운 자료가 추가되면 업데이트하고, 상호 참조를 유지하며, 모든 내용의 일관성을 유지합니다. 여러분은 읽는 것이고, 작성하는 것은 LLM입니다.

**The schema** — a document (e.g. CLAUDE.md for Claude Code or AGENTS.md for Codex) that tells the LLM how the wiki is structured, what the conventions are, and what workflows to follow when ingesting sources, answering questions, or maintaining the wiki. This is the key configuration file — it's what makes the LLM a disciplined wiki maintainer rather than a generic chatbot. You and the LLM co-evolve this over time as you figure out what works for your domain.
**스키마는** LLM에게 위키 구조, 규칙, 소스 입력, 질문 답변, 위키 유지 관리 시 따라야 할 워크플로를 알려주는 문서입니다(예: Claude Code의 경우 CLAUDE.md, Codex의 경우 AGENTS.md). 이 핵심 구성 파일 덕분에 LLM은 일반적인 챗봇이 아닌 체계적인 위키 관리자가 될 수 있습니다. 사용자는 도메인에 맞는 최적의 방식을 찾아나가면서 LLM과 함께 이 스키마를 점진적으로 발전시켜 나갑니다.

## Operations 운영

**Ingest.** You drop a new source into the raw collection and tell the LLM to process it. An example flow: the LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. A single source might touch 10-15 wiki pages. Personally I prefer to ingest sources one at a time and stay involved — I read the summaries, check the updates, and guide the LLM on what to emphasize. But you could also batch-ingest many sources at once with less supervision. It's up to you to develop the workflow that fits your style and document it in the schema for future sessions.
**데이터 수집.** 새로운 소스를 원시 컬렉션에 추가하고 LLM에게 처리를 지시합니다. 예시 흐름은 다음과 같습니다. LLM은 소스를 읽고, 핵심 내용을 여러분과 논의하고, 위키에 요약 페이지를 작성하고, 색인을 업데이트하고, 위키 전체의 관련 엔티티 및 개념 페이지를 업데이트하고, 로그에 항목을 추가합니다. 하나의 소스가 10~15개의 위키 페이지에 영향을 미칠 수 있습니다. 개인적으로는 소스를 한 번에 하나씩 수집하고 직접 참여하는 방식을 선호합니다. 요약을 읽고, 업데이트를 확인하고, LLM에게 어떤 부분을 강조해야 하는지 안내합니다. 하지만 감독을 최소화하면서 여러 소스를 한 번에 일괄 수집할 수도 있습니다. 여러분의 스타일에 맞는 워크플로를 개발하고 향후 세션을 위해 스키마에 문서화하는 것은 여러분의 몫입니다.

**Query.** You ask questions against the wiki. The LLM searches for relevant pages, reads them, and synthesizes an answer with citations. Answers can take different forms depending on the question — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas. The important insight: **good answers can be filed back into the wiki as new pages.** A comparison you asked for, an analysis, a connection you discovered — these are valuable and shouldn't disappear into chat history. This way your explorations compound in the knowledge base just like ingested sources do.
**질의.** 위키에 질문을 던지면 LLM이 관련 페이지를 검색하고, 내용을 읽고, 인용문을 포함하여 답변을 종합합니다. 답변은 질문에 따라 마크다운 페이지, 비교표, 슬라이드(Marp), 차트(matplotlib), 캔버스 등 다양한 형태로 제공될 수 있습니다. 중요한 점은 **좋은 답변은 새로운 페이지로 위키에 다시 저장될 수 있다는 것입니다.** 사용자가 요청한 비교, 분석, 발견한 연결점 등은 가치 있는 정보이므로 채팅 기록으로만 남아서는 안 됩니다. 이렇게 하면 사용자의 탐색 활동이 마치 입력된 자료처럼 지식 기반에 축적될 수 있습니다.

**Lint.** Periodically, ask the LLM to health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search. The LLM is good at suggesting new questions to investigate and new sources to look for. This keeps the wiki healthy as it grows.
**정기적으로 LLM에게 위키의 상태를 점검해 달라고 요청 하세요** . 점검 항목에는 페이지 간의 모순, 최신 자료로 대체된 오래된 주장, 외부 링크가 없는 고립된 페이지, 언급되었지만 별도의 페이지가 없는 중요한 개념, 누락된 상호 참조, 웹 검색으로 채울 수 있는 데이터 공백 등이 포함됩니다. LLM은 조사해야 할 새로운 질문과 찾아야 할 새로운 자료를 제안하는 데 능숙합니다. 이러한 과정을 통해 위키는 성장하면서 건강하게 유지될 수 있습니다.

## Indexing and logging 인덱싱 로깅

Two special files help the LLM (and you) navigate the wiki as it grows. They serve different purposes:
두 개의 특별한 파일은 LLM(및 여러분)이 위키가 성장함에 따라 위키를 탐색하는 데 도움을 줍니다. 이 파일들은 서로 다른 목적을 가지고 있습니다.

**index.md** is content-oriented. It's a catalog of everything in the wiki — each page listed with a link, a one-line summary, and optionally metadata like date or source count. Organized by category (entities, concepts, sources, etc.). The LLM updates it on every ingest. When answering a query, the LLM reads the index first to find relevant pages, then drills into them. This works surprisingly well at moderate scale (~100 sources, ~hundreds of pages) and avoids the need for embedding-based RAG infrastructure.
**index.md** 는 콘텐츠 중심적입니다. 위키에 있는 모든 항목의 카탈로그 역할을 하며, 각 페이지는 링크, 한 줄 요약, 그리고 선택적으로 날짜나 출처 수와 같은 메타데이터와 함께 나열됩니다. 엔티티, 개념, 출처 등과 같은 범주별로 정리되어 있습니다. LLM(Long List Manager)은 데이터를 수집할 때마다 index.md를 업데이트합니다. 쿼리에 응답할 때 LLM은 먼저 인덱스를 읽어 관련 페이지를 찾은 다음 해당 페이지로 이동합니다. 이 방식은 중간 규모(약 100개 출처, 수백 개 페이지)에서 놀라울 정도로 잘 작동하며, 임베딩 기반 RAG(Resource Assessment Group) 인프라가 필요하지 않습니다.

**log.md** is chronological. It's an append-only record of what happened and when — ingests, queries, lint passes. A useful tip: if each entry starts with a consistent prefix (e.g. `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools — `grep "^## \[" log.md | tail -5` gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the LLM understand what's been done recently.
**log.md 파일** 은 시간 순서대로 기록됩니다. 데이터 수집, 쿼리, 린트 검사 등 발생한 모든 작업과 시간을 기록하는 추가 전용 로그 파일입니다. 유용한 팁: 각 항목이 일관된 접두사(예: `<log_name>` `## [2026-04-02] ingest | Article Title`)로 시작하면 간단한 Unix 도구를 사용하여 로그를 파싱할 수 있습니다. 예를 들어 `log_name> `grep "^## \[" log.md | tail -5``을 사용하면 최근 5개 항목을 얻을 수 있습니다. 이 로그 파일은 위키의 발전 과정을 시간 순서대로 보여주며, LLM(Limited Leadership Manager)이 최근 작업 내용을 파악하는 데 도움을 줍니다.

## Optional: CLI tools

At some point you may want to build small tools that help the LLM operate on the wiki more efficiently. A search engine over the wiki pages is the most obvious one — at small scale the index file is enough, but as the wiki grows you want proper search. [qmd](https://github.com/tobi/qmd) is a good option: it's a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. It has both a CLI (so the LLM can shell out to it) and an MCP server (so the LLM can use it as a native tool). You could also build something simpler yourself — the LLM can help you vibe-code a naive search script as the need arises.
어느 시점에선가 LLM이 위키에서 더 효율적으로 작동하도록 돕는 작은 도구들을 만들고 싶어질 수도 있습니다. 위키 페이지 검색 엔진이 가장 대표적인 예입니다. 규모가 작을 때는 인덱스 파일만으로도 충분하지만, 위키 규모가 커질수록 제대로 된 검색 기능이 필요해집니다. [qmd](https://github.com/tobi/qmd) 는 좋은 선택입니다. qmd는 마크다운 파일용 로컬 검색 엔진으로, 하이브리드 BM25/벡터 검색과 LLM 재순위 지정 기능을 모두 기기 내에서 사용할 수 있습니다. LLM이 직접 실행할 수 있는 CLI(명령줄 인터페이스)와 LLM이 네이티브 도구처럼 사용할 수 있는 MCP 서버를 모두 제공합니다. 더 간단한 검색 스크립트를 직접 만들 수도 있습니다. 필요에 따라 LLM이 직관적으로 코드를 작성하는 데 도움을 줄 수 있습니다.

## Tips and tricks 팁 요령

- **Obsidian Web Clipper** is a browser extension that converts web articles to markdown. Very useful for quickly getting sources into your raw collection.
- **Download images locally.** In Obsidian Settings → Files and links, set "Attachment folder path" to a fixed directory (e.g. `raw/assets/`). Then in Settings → Hotkeys, search for "Download" to find "Download attachments for current file" and bind it to a hotkey (e.g. Ctrl+Shift+D). After clipping an article, hit the hotkey and all images get downloaded to local disk. This is optional but useful — it lets the LLM view and reference images directly instead of relying on URLs that may break. Note that LLMs can't natively read markdown with inline images in one pass — the workaround is to have the LLM read the text first, then view some or all of the referenced images separately to gain additional context. It's a bit clunky but works well enough.
- **Obsidian's graph view** is the best way to see the shape of your wiki — what's connected to what, which pages are hubs, which are orphans.
- **Marp** is a markdown-based slide deck format. Obsidian has a plugin for it. Useful for generating presentations directly from wiki content.
- **Dataview** is an Obsidian plugin that runs queries over page frontmatter. If your LLM adds YAML frontmatter to wiki pages (tags, dates, source counts), Dataview can generate dynamic tables and lists.
- The wiki is just a git repo of markdown files. You get version history, branching, and collaboration for free.

- **Obsidian Web Clipper** 는 웹 기사를 마크다운 형식으로 변환해주는 브라우저 확장 프로그램입니다. 원본 자료를 빠르게 수집하는 데 매우 유용합니다.
- **이미지를 로컬에 다운로드하세요.** Obsidian 설정 → 파일 및 링크에서 "첨부 파일 폴더 경로"를 고정된 디렉터리(예: `raw/assets/`)로 설정합니다. 그런 다음 설정 → 단축키에서 "다운로드"를 검색하여 "현재 파일의 첨부 파일 다운로드"를 찾고 단축키(예: Ctrl+Shift+D)에 할당합니다. 기사를 클리핑한 후 단축키를 누르면 모든 이미지가 로컬 디스크에 다운로드됩니다. 이 기능은 선택 사항이지만 유용합니다. LLM이 URL에 의존하지 않고 이미지를 직접 보고 참조할 수 있기 때문입니다. LLM은 기본적으로 인라인 이미지가 포함된 마크다운을 한 번에 읽을 수 없습니다. 해결 방법은 LLM이 먼저 텍스트를 읽은 다음 참조된 이미지의 일부 또는 전부를 별도로 보고 추가적인 컨텍스트를 얻는 것입니다. 다소 번거롭지만 충분히 잘 작동합니다.
- **Obsidian의 그래프 보기는** 위키의 구조를 파악하는 가장 좋은 방법입니다. 무엇이 무엇과 연결되어 있는지, 어떤 페이지가 허브 역할을 하는지, 어떤 페이지가 고립된 페이지인지 알 수 있습니다.
- **Marp** 는 마크다운 기반 슬라이드 데크 형식입니다. Obsidian에는 이를 위한 플러그인이 있습니다. 위키 콘텐츠에서 직접 프레젠테이션을 생성하는 데 유용합니다.
- **Dataview** 는 페이지 프런트매터에 대한 쿼리를 실행하는 Obsidian 플러그인입니다. LLM에서 위키 페이지에 YAML 프런트매터(태그, 날짜, 출처 수 등)를 추가하는 경우 Dataview를 사용하여 동적 테이블과 목록을 생성할 수 있습니다.
- 위키는 마크다운 파일들을 모아놓은 Git 저장소일 뿐입니다. 버전 기록, 브랜칭, 공동 작업 기능을 무료로 이용할 수 있습니다.

## Why this works 효과적인 이유

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The wiki stays maintained because the cost of maintenance is near zero.
지식 기반을 유지 관리하는 데 있어 지루한 부분은 읽거나 생각하는 것이 아니라, 바로 장부 정리입니다. 상호 참조를 업데이트하고, 요약을 최신 상태로 유지하고, 새로운 데이터가 기존 주장과 모순될 때 이를 기록하고, 수십 개의 페이지에 걸쳐 일관성을 유지하는 것 말입니다. 사람들이 위키를 포기하는 이유는 유지 관리 부담이 가치보다 빠르게 증가하기 때문입니다. 반면, 언어 관리자(LLM)는 지루해하지 않고, 상호 참조 업데이트를 잊지 않으며, 한 번에 15개 파일을 수정할 수 있습니다. 위키는 유지 관리 비용이 거의 들지 않기 때문에 지속적으로 유지 관리됩니다.

The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.
인간 연구자의 역할은 자료를 선별하고, 분석 방향을 제시하고, 좋은 질문을 던지고, 그 모든 것의 의미를 생각해내는 것입니다. 법학 석사(LLM) 과정 학생의 역할은 그 외의 모든 것입니다.

The idea is related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. Bush's vision was closer to this than to what the web became: private, actively curated, with the connections between documents as valuable as the documents themselves. The part he couldn't solve was who does the maintenance. The LLM handles that.
이 아이디어는 바네바 부시의 메멕스(Memex, 1945)와 정신적으로 관련이 있습니다. 메멕스는 문서 간의 연관성을 보여주는 개인 맞춤형 지식 저장소입니다. 부시의 비전은 현재의 웹보다는 이러한 메멕스에 더 가까웠습니다. 즉, 사적이고 능동적으로 관리되는 저장소이며, 문서 간의 연결 고리가 문서 자체만큼이나 가치 있는 것입니다. 그가 해결하지 못한 문제는 누가 유지 관리를 담당하는가였습니다. LLM이 바로 그 부분을 담당합니다.

## Note

This document is intentionally abstract. It describes the idea, not a specific implementation. The exact directory structure, the schema conventions, the page formats, the tooling — all of that will depend on your domain, your preferences, and your LLM of choice. Everything mentioned above is optional and modular — pick what's useful, ignore what isn't. For example: your sources might be text-only, so you don't need image handling at all. Your wiki might be small enough that the index file is all you need, no search engine required. You might not care about slide decks and just want markdown pages. You might want a completely different set of output formats. The right way to use this is to share it with your LLM agent and work together to instantiate a version that fits your needs. The document's only job is to communicate the pattern. Your LLM can figure out the rest.
이 문서는 의도적으로 추상적입니다. 구체적인 구현 방법이 아닌 아이디어를 설명하는 문서입니다. 정확한 디렉터리 구조, 스키마 규칙, 페이지 형식, 도구 등은 모두 도메인, 선호도, 선택한 LLM(로컬 라이프사이클 관리) 시스템에 따라 달라집니다. 위에 언급된 모든 내용은 선택 사항이며 모듈식으로 구성되어 있으므로 필요한 부분만 선택하고 필요 없는 부분은 무시하면 됩니다. 예를 들어, 소스가 텍스트뿐이라면 이미지 처리가 전혀 필요하지 않을 수 있습니다. 위키 규모가 작아서 색인 파일만으로 충분하고 검색 엔진이 필요 없을 수도 있습니다. 슬라이드 자료는 필요 없고 마크다운 페이지만 원할 수도 있습니다. 완전히 다른 출력 형식을 원할 수도 있습니다. 이 문서를 가장 효과적으로 사용하는 방법은 LLM 담당자와 공유하고 협력하여 필요에 맞는 버전을 구현하는 것입니다. 이 문서의 유일한 목적은 패턴을 전달하는 것이며, 나머지는 LLM 담당자가 알아서 처리할 것입니다.