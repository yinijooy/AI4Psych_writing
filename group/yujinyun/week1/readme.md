# Introduction Enhancement Pipeline 사용 가이드

학술 논문 Introduction 섹션을 5개의 전문 AI Agent로 자동 개선하는 Multi-Agent 시스템입니다.

---

## 🎯 목표 (Objective)

**"Introduction 초안을 출판 가능한 수준으로 자동 변환"**

### 핵심 목표
1. **구조 개선**: 논리적 흐름과 각 문단의 역할 명확화
2. **인용 관리**: 누락된 citation 찾기 및 추가 권장
3. **언어 품질**: 명확성, 간결성, 학술적 톤 향상
4. **흐름 최적화**: 문단 간 전환(transition) 매끄럽게
5. **품질 검증**: 최종 출판 준비도 평가

---

## 🤖 5-Agent 파이프라인 구조

```
[draft.txt] → Introduction 초안 입력
    ↓
┌─────────────────────────────────────────┐
│ Agent 1: Structure Analyzer             │  ← 구조 분석
│  - 문단 분리 및 역할 파악               │
│  - Hook/Gap/Method/Hypothesis 식별      │
└─────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────┐
│ Agent 2: Citation Manager               │  ← 인용 관리
│  - 기존 citation 추출                   │
│  - 누락된 참고문헌 찾기                 │
│  - 인용 필요 위치 권장                  │
└─────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────┐
│ Agent 3: Language Enhancer              │  ← 언어 개선
│  - 명확성 향상 (jargon 제거)           │
│  - 간결성 향상 (redundancy 제거)       │
│  - 학술적 톤 조정                       │
└─────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────┐
│ Agent 4: Flow Optimizer                 │  ← 흐름 최적화
│  - 문단 간 transition 분석              │
│  - Smooth/Adequate/Abrupt 평가          │
│  - 개선 제안                            │
└─────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────┐
│ Agent 5: Quality Checker                │  ← 품질 검증
│  - 정량 지표 (단어 수, 문장 길이 등)   │
│  - 정성 평가 (Clarity, Flow, Impact)   │
│  - 출판 준비도 점수 (X/50)              │
└─────────────────────────────────────────┘
    ↓
[3개 출력 파일]
  1. Introduction_Enhanced_Gemini_[timestamp].txt
  2. Enhancement_Report_Gemini_[timestamp].md
  3. Introduction_Visualization_Gemini_[timestamp].html
```

---

## 🚀 빠른 시작 (Quick Start)

### 1. 필수 준비사항

```bash
# 패키지 설치
pip install google-generativeai python-dotenv

# API 키 설정
export GOOGLE_API_KEY='your-gemini-api-key'
```

### 2. 파일 준비

```
week6/
├── Introduction_Enhancement_Pipeline_Gemini.ipynb
└── draft.txt  ← 당신의 Introduction 초안
```

**draft.txt 예시:**
```
# Introduction

Children's screen use is widespread and increasing...
(중략)
```

### 3. 실행

**Jupyter Notebook에서:**
1. `Introduction_Enhancement_Pipeline_Gemini.ipynb` 열기
2. **Run All** 클릭 (또는 Shift+Enter로 순차 실행)
3. 약 5-10분 소요 (API 호출 시간 포함)

**명령줄에서 (옵션):**
```bash
jupyter nbconvert --to notebook --execute Introduction_Enhancement_Pipeline_Gemini.ipynb
```

---

## 📊 출력 파일 상세

### 1. Enhanced Introduction (`.txt`)
**파일명:** `Introduction_Enhanced_Gemini_YYYYMMDD_HHMMSS.txt`

**내용:** Agent 3가 개선한 텍스트를 Agent 4가 통합한 최종 버전

**예시:**
```
# Introduction (Enhanced by Gemini 2.0 Flash)

The widespread and increasing use of screens among children has sparked
considerable debate regarding its impact on mental health. While observational
studies and meta-analyses typically report small average associations between
total screen time and child mental health problems, notable inconsistencies
emerge across cohorts, developmental windows, and screen modalities...
```

**사용법:**
- 논문에 바로 복사-붙여넣기
- Word/LaTeX 문서에 삽입
- 원본과 비교 검토

---

### 2. Enhancement Report (`.md`)
**파일명:** `Enhancement_Report_Gemini_YYYYMMDD_HHMMSS.md`

**내용:** 전체 개선 과정의 상세 보고서

**구조:**
```markdown
# Introduction Enhancement Report (Gemini)

## Summary
- Original words: 878
- Enhanced words: 906 (+3.2%)
- Paragraphs processed: 9

## Quality Assessment
Clarity: 9/10 - Enhanced version is clearer...
Conciseness: 8/10 - More concise phrasing...
Overall: 43/50 - Publication readiness: Minor revision

## Paragraph-by-Paragraph Changes
### Paragraph 1: Hook/Problem statement
**Original (111 words):**
Children's screen use is ubiquitous...

**Enhanced (131 words, +18.0%):**
The widespread and increasing use of screens...

---

### Paragraph 2: Literature review
...

## Citation Analysis
- Citations found: 0
- Paragraphs needing citations: 4

**Recommended additions:**
- P1: Hook/Problem statement, Gap identification
- P2: Literature review

## Flow Analysis
**P1 → P2:** Smooth (good logical flow)
**P2 → P3:** Abrupt (needs work)
```

**사용법:**
- 개선 사항 검토
- 추가 수정이 필요한 부분 파악
- 지도교수/공저자와 공유

---

### 3. Visualization HTML
**파일명:** `Introduction_Visualization_Gemini_YYYYMMDD_HHMMSS.html`

**내용:** 인터랙티브 품질 리포트 (브라우저에서 열기)

**포함 내용:**
- 정량 지표 카드 (문단 수, 단어 변화율, 인용 수)
- 품질 평가 점수
- 시각적으로 보기 좋은 레이아웃

**사용법:**
```bash
# 브라우저에서 열기
open Introduction_Visualization_Gemini_20251102_115013.html

# 또는 더블클릭
```

---

## 📋 각 Agent 상세 설명

### Agent 1: Structure Analyzer
**역할:** 문단 구조 분석

**수행 작업:**
1. Introduction을 문단 단위로 분리
2. 각 문단의 역할 식별:
   - Hook/Problem statement (문제 제기)
   - Literature review (선행연구)
   - Gap identification (연구 공백)
   - Methodological approach (방법론)
   - Hypotheses (가설)
   - Significance/Contribution (의의)

**출력 예시:**
```
[P1] Hook/Problem statement, Gap identification (111 words)
[P2] Literature review (103 words)
[P3] Gap identification (83 words)
[P4] Methodological approach (90 words)
```

**중요도:** ⭐⭐⭐⭐⭐ (구조가 명확해야 나머지 agent가 효과적)

---

### Agent 2: Citation Manager
**역할:** 인용 관리 및 검증

**수행 작업:**
1. 정규식으로 in-text citation 추출
   - 패턴: `(Author et al., Year)` 또는 `(Author & Author, Year)`
2. 인용이 없는 문단 중 empirical claim이 있는 곳 찾기
3. 추가 인용이 필요한 위치 권장

**출력 예시:**
```
Found 0 in-text citations

⚠️ WARNING: No citations found!

Recommendations:
  1. Add citations for 'Observational studies and meta-analyses'
  2. Cite GRF methodology papers
  3. Reference ABCD Study design papers

Paragraphs needing citations: 4
  - P1: Hook/Problem statement
  - P2: Literature review
```

**중요도:** ⭐⭐⭐⭐ (학술 논문은 citation 필수)

---

### Agent 3: Language Enhancer
**역할:** 언어 품질 향상

**수행 작업 (각 문단마다):**
1. **Clarity**: Jargon 제거, 기술 용어 정의
2. **Conciseness**: Redundancy 제거, 간결하게
3. **Precision**: 정확한 표현 사용
4. **Flow**: 문장 다양성 및 전환어 개선
5. **Tone**: 학술적이지만 접근 가능한 톤

**제약 조건:**
- 의미 보존 (factual claims 유지)
- 길이 유사 (±10% words)
- Active voice 선호
- 문장 길이 최대 30-35 단어

**출력 예시:**
```
[P1] Original: 111 words → Enhanced: 131 words (+18.0%)

Before: "Children's screen use is ubiquitous and rising..."
After:  "The widespread and increasing use of screens among children..."
```

**중요도:** ⭐⭐⭐⭐⭐ (가장 큰 변화를 만드는 agent)

---

### Agent 4: Flow Optimizer
**역할:** 문단 간 전환 개선

**수행 작업:**
1. 인접 문단 간 연결 분석
2. 각 transition을 평가:
   - **Smooth**: 논리적 흐름이 좋음
   - **Adequate**: 괜찮지만 개선 가능
   - **Abrupt**: 작업 필요
3. 개선 제안 제공

**출력 예시:**
```
P1 → P2: Smooth (good logical flow)

P2 → P3: Abrupt (needs work)
Suggestion: Explicitly introduce the concept of precision
developmental science and connect it to the previously mentioned factors.

P3 → P4: Adequate (acceptable but could improve)
Suggestion: Briefly connect "individualized risk profiling" to
the use of ABCD cohort.
```

**중요도:** ⭐⭐⭐⭐ (전체 논리 흐름 결정)

---

### Agent 5: Quality Checker
**역할:** 최종 품질 검증

**수행 작업:**
1. **정량 지표**:
   - 단어 수 변화
   - 문장 수
   - 평균 문장 길이
2. **정성 평가** (1-10점):
   - Clarity (명확성)
   - Conciseness (간결성)
   - Academic tone (학술적 톤)
   - Flow (논리 흐름)
   - Impact (영향력)
3. **출판 준비도** 평가:
   - Major revision (대폭 수정)
   - Minor revision (소폭 수정)
   - Accept (수락)

**출력 예시:**
```
📊 Quantitative Metrics:
  Word count: 878 → 906 (+3.2%)
  Sentences: 45 → 45
  Avg sentence length: 19.5 → 20.1 words

🔍 Qualitative Assessment:
Clarity: 9/10 - Enhanced version is clearer
Conciseness: 8/10 - More concise phrasing
Academic tone: 9/10 - Good formal tone
Flow: 9/10 - Improved logical flow
Impact: 8/10 - Compelling introduction

Overall: 43/50 - Publication readiness: Minor revision
```

**중요도:** ⭐⭐⭐⭐⭐ (최종 품질 보증)

---

## 💡 실전 사용 팁

### 1. draft.txt 작성 요령

**최소 요구사항:**
- 500자 이상
- 3-5개 문단
- 명확한 문단 구분 (빈 줄로 분리)

**권장사항:**
- 7-9개 문단 (이 예제처럼)
- 각 문단 100-150 단어
- 이미 기본 구조 갖춤 (Hook → Gap → Method → Hypotheses)

**좋은 예:**
```
Children's screen use is widespread...

Previous research has shown...

However, three major gaps remain...

To address these gaps, we employ...
```

**나쁜 예:**
```
Screen time is bad. We study it. [너무 짧음]

This is a very long paragraph that talks about everything
including the problem, literature, gaps, methods, and hypotheses
all in one giant block of text without any clear separation...
[구조 없음]
```

---

### 2. API 사용량 관리

**Gemini 2.0 Flash 무료 플랜:**
- **분당 요청 제한**: 10 requests/minute
- **하루 제한**: 1,500 requests/day

**이 파이프라인의 API 호출 수:**
- Agent 1: 9회 (문단 9개)
- Agent 2: 1회
- Agent 3: 9회 (문단 9개)
- Agent 4: 8회 (transition 8개)
- Agent 5: 1회
- **총: 약 28회**

**Rate limit 초과 시 대처:**
```python
# 코드에 이미 포함된 time.sleep()으로 자동 조절
time.sleep(0.5)  # Agent 1, 4
time.sleep(1)    # Agent 3 (더 긴 프롬프트)
time.sleep(2)    # Error 발생 시
```

**여러 Introduction 처리 시:**
```python
# 배치 처리 간 대기
for draft in drafts:
    run_pipeline(draft)
    time.sleep(60)  # 1분 대기
```

---

### 3. 결과 검토 체크리스트

**✅ 반드시 확인:**
- [ ] 의미가 보존되었는가? (factual claims 유지)
- [ ] 중요한 용어가 변경되지 않았는가?
- [ ] 인용 추가 권장 사항 검토
- [ ] Abrupt transition 개선 제안 반영
- [ ] 전체 톤이 논문에 적합한가?

**⚠️ 주의사항:**
- AI가 생성한 텍스트는 항상 검토 필요
- 전문 용어 정확성 확인
- 지도교수/공저자에게 최종 검토 요청

---

## 🔧 커스터마이징

### 1. Agent 3 개선 강도 조절

```python
# 더 보수적 (원본에 가깝게)
"Maintain similar length (±5% words)"  # 기본: ±10%

# 더 공격적 (많이 변경)
"Maintain similar length (±20% words)"
```

### 2. 특정 Agent만 실행

```python
# Agent 1, 2만 실행 (구조 분석 + 인용 확인만)
agent1_output = agent1_structure_analyzer(draft_text)
agent2_output = agent2_citation_manager(draft_text)

# Agent 3 스킵하고 바로 Agent 5
agent5_output = agent5_quality_checker(draft_text, draft_text, [])
```

### 3. 다른 섹션 적용 (Methods, Discussion)

```python
# draft.txt 대신 methods.txt 사용
methods_path = "methods.txt"
with open(methods_path, "r") as f:
    methods_text = f.read()

# Agent 1 프롬프트 수정
"Analyze this Methods paragraph and identify its PURPOSE..."
```

---

## 🆚 OpenAI vs Gemini 버전 비교

| 항목 | OpenAI 버전 | Gemini 버전 (이 파일) |
|------|-------------|----------------------|
| **모델** | GPT-4o / GPT-4o-mini | Gemini 2.0 Flash |
| **API 설정** | `openai.OpenAI()` | `genai.GenerativeModel()` |
| **호출 방법** | `client.chat.completions.create()` | `MODEL.generate_content()` |
| **응답 추출** | `response.choices[0].message.content` | `response.text` |
| **무료 플랜** | $5 크레딧 (1회성) | 분당 10회, 하루 1,500회 |
| **속도** | 빠름 | 매우 빠름 |
| **품질** | 우수 | 우수 |
| **가격** | $0.005/1K tokens (input) | 무료 (제한 내) |

**권장 사용:**
- **OpenAI**: 더 정교한 개선 필요 시 (예: Nature/Science 급)
- **Gemini**: 빠르고 무료로 여러 번 시도하고 싶을 때

---

## 🐛 트러블슈팅

### 문제 1: "429 Quota exceeded"
**증상:**
```
429 You exceeded your current quota
* Quota exceeded for metric: generate_content_free_tier_requests
Please retry in 44.433s
```

**원인:** 분당 10회 요청 제한 초과

**해결:**
1. **대기 후 재실행** (44초 후)
2. **time.sleep() 늘리기:**
```python
time.sleep(2)  # 기본: 0.5초 → 2초로 변경
```

---

### 문제 2: "Agent가 원본 텍스트 그대로 반환"
**증상:** Enhanced 텍스트가 Original과 동일

**원인:**
1. API quota 초과로 error 발생
2. 프롬프트가 모델에 명확하지 않음

**해결:**
1. **Quota 확인:**
```python
# Agent 3 출력 확인
# "⚠️ Error: 429 ..." 메시지 있는지 확인
```

2. **프롬프트 수정:**
```python
# 더 명확한 지시
"**Output:** Return ONLY the enhanced paragraph.
Make AT LEAST 3 improvements."
```

---

### 문제 3: "HTML 파일이 제대로 안 보임"
**증상:** HTML 파일이 깨지거나 스타일이 안 나옴

**해결:**
```html
<!-- HTML 파일 인코딩 확인 -->
<meta charset="UTF-8">

<!-- 파일 저장 시 UTF-8 확인 -->
with open(html_file, "w", encoding="utf-8") as f:
```

---

## 📈 성능 벤치마크

**테스트 조건:**
- Introduction 길이: 878 words, 9 paragraphs
- 모델: Gemini 2.0 Flash
- 날짜: 2025-11-02

**결과:**
| 지표 | 원본 | 개선 후 | 변화 |
|------|------|---------|------|
| **단어 수** | 878 | 906 | +3.2% |
| **문장 수** | 45 | 45 | 0% |
| **평균 문장 길이** | 19.5 words | 20.1 words | +3.1% |
| **Clarity** | - | 9/10 | - |
| **Conciseness** | - | 8/10 | - |
| **Academic tone** | - | 9/10 | - |
| **Flow** | - | 9/10 | - |
| **Impact** | - | 8/10 | - |
| **Overall** | - | 43/50 | **Minor revision** |

**실행 시간:**
- Agent 1: ~1분
- Agent 2: ~5초
- Agent 3: ~2분 (quota 초과로 일부 원본 유지)
- Agent 4: ~1분
- Agent 5: ~10초
- **총: 약 4.5분**

## 📚 참고 자료

### 관련 파일
- `Introduction_Enhancement_Pipeline_Gemini.ipynb`: 메인 노트북
- `draft.txt`: Introduction 초안 예시
- `Academic_Writing_Assistant_Guide.md`: 전체 writing 보조 기능 가이드

### 외부 링크
- [Google Gemini API Docs](https://ai.google.dev/tutorials/python_quickstart)
- [Gemini Rate Limits](https://ai.google.dev/gemini-api/docs/rate-limits)
- [APA Style Guide](https://apastyle.apa.org/)

---

## 🎯 요약 (TL;DR)

### 30초 사용법
```bash
# 1. API 키 설정
export GOOGLE_API_KEY='your-key'

# 2. draft.txt 준비
echo "Your introduction text..." > draft.txt

# 3. Jupyter Notebook 실행
jupyter notebook Introduction_Enhancement_Pipeline_Gemini.ipynb
# → Run All 클릭

# 4. 결과 확인
# - Introduction_Enhanced_Gemini_*.txt (개선된 텍스트)
# - Enhancement_Report_Gemini_*.md (상세 보고서)
# - Introduction_Visualization_Gemini_*.html (시각화)
```

### 핵심 특징
✅ **5개 전문 Agent**: 구조, 인용, 언어, 흐름, 품질
✅ **자동화**: Run All 한 번으로 완성
✅ **무료**: Gemini 2.0 Flash 사용 (제한 내)
✅ **빠름**: 약 5분 소요
✅ **품질 보증**: 43/50점 (Minor revision 수준)
