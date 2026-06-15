내 LLM-wiki와는 다를 수 있음. 발전시키는데 참고할 수 있음. 
https://youtu.be/S6w4g2OQlVQ?si=VtjLgK3cbhphbLZE&t=1319

## 1. Ingest (정보 흡수 및 등록)
새로운 정보 소스(데이터, 문서 등)를 지식 베이스에 추가하라는 요청을 받았을 때의 절차임.

- **When asked to ingest a new source:**
  새로운 소스를 수집/흡수하라는 요청을 받았을 때:
	- **1. Read the raw source file.**
	  가공되지 않은 원본 소스 파일을 읽음. 
	- **2. Create or update a page in `wiki/sources/`.**
	  `wiki/sources/` 폴더 내에 페이지를 새로 생성하거나 기존 페이지를 업데이트함.
	- **3. Update relevant pages in `wiki/entities/` and `wiki/concepts/`.**
	  `wiki/entities/`(개체) 및 `wiki/concepts/`(개념) 폴더 내의 관련 페이지들을 업데이트함.
	- **4. Add/catalog external links.**
	  외부 링크를 추가하고 카탈로그화(분류)함.
	- **5. Update `index.md`.**
	  메인 인덱스 파일(`index.md`)을 업데이트함.
	- **6. Append an entry to `log.md`.**
	  변경 사항 로그 파일(`log.md`)에 새로운 항목을 추가함.
	- **7. If there are major unresolved questions, note them in the affected page and optionally in `index.md`.**
	  아직 해결되지 않은 중요한 질문이 있다면, 영향을 받는 해당 페이지에 기록하고 필요한 경우 `index.md`에도 선택적으로 기록함.

## 2. Query (질문 및 검색 대응)
지식 베이스를 기반으로 특정 질문에 답변할 때의 절차임.

* ***When asked a question about the knowledge base:**
  지식 베이스에 대해 질문을 받았을 때:
	* **1. Read `index.md`.**
	  `index.md`(인덱스 파일)를 읽음.
	* **2. Read the most relevant wiki pages.**
	  질문과 가장 관련성이 높은 위키 페이지들을 읽음.
	* **3. Use raw sources only to verify or fill gaps.**
	  원본 소스는 내용을 검증하거나 누락된 공백을 채울 때만 제한적으로 사용함.
	* **4. Answer with citations to wiki pages and raw sources where useful.**
	  유용한 경우, 위키 페이지 및 원본 소스에 대한 인용(출처)을 포함하여 답변함.
	* **5. If the result is reusable, save it in `wiki/analyses/` and update `index.md` and `log.md`.**
	  도출된 결과가 재사용 가능한 가치가 있다면, 이를 `wiki/analyses/` 폴더에 저장하고 `index.md`와 `log.md`를 업데이트함. (앞서 질문하신 '___ 폴더명'의 해답이 이 가이드라인에서는 `analyses/`로 정의되어 있음)

## 3. Lint (지식 베이스 품질 및 무결성 검사)
위키의 전반적인 상태를 점검하고 유지보수할 때의 검사 항목임.

* **When asked to lint or health-check the wiki:**
  위키의 린트(오류 검사) 또는 헬스체크(상태 점검)를 요청받았을 때:
	* **1. Look for duplicate pages.**
	  중복된 페이지가 있는지 확인함.
	* **2. Look for stale claims and unresolved contradictions.**
	  기한이 지나 유효하지 않은 주장이나 해결되지 않은 모순점이 있는지 확인함.
	* **3. Look for orphan pages with weak linking.**
	  다른 페이지와의 연결(링크)이 부실하여 고립된 페이지(Orphan pages)가 있는지 확인함.
	* **4. Look for important entities or concepts that lack dedicated pages.**
	  전용 페이지가 개설되지 않은 중요한 개체(Entities)나 개념(Concepts)이 있는지 확인함.
	* **5. Suggest follow-up sources or questions.**
	  후속 조치가 필요한 소스나 추가 질문을 제안함.
	* **6. Record the lint pass in `log.md`.**
	  린트 검사 수행 결과를 `log.md`에 기록함.