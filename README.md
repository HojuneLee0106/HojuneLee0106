<p align="center">
  <img src="assets/banner.png" alt="이호준 · Hojune Lee — AI/ML Engineer" width="100%"/>
</p>

<p align="center">
  <a href="mailto:hojune0106@naver.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
  </a>
  <img src="https://img.shields.io/badge/🏆_KTB_AI_성능_개선_대회-최우수상-FFB000?style=for-the-badge&labelColor=1a1a19" alt="최우수상"/>
  <img src="https://komarev.com/ghpvc/?username=HojuneLee0106&style=for-the-badge&color=2a78d6&label=PROFILE+VIEWS" alt="Profile views"/>
</p>

---

## 👋 About Me

음성 인식(STT)과 음성 합성(TTS)에서 시작해, 지금은 **RAG와 LLM 에이전트**를 만들고 있습니다.

성능을 "올렸다"고 말하려면 먼저 재봐야 한다고 생각합니다. 생활법률 RAG를 만들 때 프롬프트를 고칠 때마다 점수가 오르내렸는데, 문항당 3회씩 반복 측정해 보니 **그 등락의 대부분이 노이즈**였습니다. 그 뒤로는 개선을 주장하기 전에 평가 파이프라인부터 세웁니다.

| | |
|---|---|
| 🎓 | **숭실대학교 소프트웨어학부** (2020.03 ~ 2026.02) |
| 🚀 | **카카오테크 부트캠프 AI 실무개발 4기** (2026.05 ~ ) |
| 🎖️ | 해병대 1263기 병장 만기전역 (2020.10 ~ 2022.04) |
| 🔬 | RAG Architecture · Agent Systems · LLM Fine-tuning · Evaluation |

---

## 🏆 KTB 4기 AI 성능 개선 대회 — 최우수상

> **카카오 약관 QA 시스템** · 13팀 ·  **88.889 / 100**
> 검색 MRR `1.0000` · 키팩트 F1 `0.6721` · LLM 판정 `97.450`
> 공개 10문항 검색 recall **12/12** · precision **12/12**

카카오 약관 4종에서 질문에 해당하는 조항을 찾아 **답변과 근거 조항을 함께** 반환하는 RAG입니다.
Google Colab T4 한 대, 외부 API 없이 동작합니다. → [저장소 보기](https://github.com/HojuneLee0106/Performance_Improvement_Contest)

---

## 💼 Experience

### AItheNutrigene · AI/ML 인턴 <sub>2024.12 ~ 2025.02</sub>

**SK Shieldus STT 성능 개선 프로젝트** (약 12주) — `Python` `NVIDIA NeMo` `KenLM`

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/stt-improvement-dark.png">
  <img src="assets/stt-improvement.png" alt="STT 성능 개선: WER 18.64%→14.11%, CER 6.83%→5.57%" width="100%"/>
</picture>

N-gram Language Modeling으로 도메인 어휘를 반영하고, Neural Rescoring으로 후보 문장을 다시 정렬해 인식 오류를 줄였습니다.

---

## 🚀 Projects

### ⚖️ [생활법률 RAG 챗봇 "법대로"](https://github.com/HojuneLee0106/online_law)

법조문 · 대법원 판례 · 생활법령을 근거로 답하는 법률 Q&A 어시스턴트.
답변의 조문 번호와 사건번호를 **원문에서 그대로 가져와** 인용합니다.

<img src="assets/law-ui.png" alt="법대로 서비스 화면 — 답변과 함께 검색한 조문 원문을 오른쪽 패널에 표시" width="100%"/>

<br/>

**아키텍처**

```mermaid
flowchart LR
    U["사용자 질문"] --> A["LangGraph<br/>단일 에이전트"]
    A -.->|search_law| L[("법조문<br/>5,390 청크")]
    A -.->|search_case| C[("대법원 판례<br/>29,820 청크")]
    A -.->|search_qa| Q[("생활법령<br/>21,610 청크")]
    L --> A
    C --> A
    Q --> A
    A --> R["답변 + 출처 인용<br/>조문번호 · 사건번호"]
    R ==>|SSE 토큰 스트리밍| U
```

한 턴에 세 도구를 **병렬 호출**하므로 도구를 3개 쓰는 질문도 LLM 왕복은 2회뿐입니다.

<br/>

**무엇을 재고 어떻게 정했나**

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/rag-quality-dark.png">
  <img src="assets/rag-quality.png" alt="모델 구성별 answer_quality 비교" width="100%"/>
</picture>

| | |
|---|---|
| **Stack** | LangGraph · Chroma · FastAPI(SSE) · Docker → GHCR → EC2 |
| **Eval** | `answer_quality 0.912` · `citation_grounding 0.984` · `tool_recall 1.000` |
| **설계** | LangSmith로 단일/멀티 에이전트 3개 구조를 비교한 뒤 single 채택 |

검색 인프라를 총동원한 개선이 **+0.031**이었던 반면, 모델 교체 한 번이 **+0.128**로 4배 컸습니다.
반대로 1회 실행 측정으로는 개선과 노이즈를 구분할 수 없다는 것도 같이 배웠습니다.

<br/>

### 🔊 AI Docent Studio <sub>캡스톤디자인 · 2025.09 ~ 2025.12</sub>

사용자 맞춤형 **TTS 모델(VITS)** 제작. 도슨트 음성을 개인화하는 프로젝트로, **RISE 사업 체결**로 이어졌습니다.

`VITS` `PyTorch` `Speech Synthesis`

<br/>

### 🏋️ AI 헬스 자세 교정 어플리케이션 <sub>캡스톤디자인 · 2025.03 ~ 2025.06</sub>

**QLoRA** 기법으로 파인튜닝한 헬스케어 맞춤 챗봇. 운동 도메인에 특화된 응답을 생성하도록 경량 학습했습니다.

`QLoRA` `PEFT` `FastAPI`

<br/>

### 🧠 [miniGPT · 한국어 QA](https://github.com/HojuneLee0106/Chatbot)

GPT 구조를 처음부터 직접 구현해 한국어 QA 데이터로 학습.
`CausalSelfAttention`부터 학습 루프까지 라이브러리 없이 짜면서 트랜스포머 내부를 이해하는 게 목적이었습니다.

| | |
|---|---|
| **Config** | `block_size=1024` · `n_embd=512` · `n_head=8` · `n_layer=8` |
| **결과** | `val loss 3.022` (A100 80GB) |

<br/>

### 💬 [커뮤니티 서버](https://github.com/HojuneLee0106/Community_server)

FastAPI 게시판 API. Router / Controller / Model 계층 분리 + MySQL 연동,
Ollama(`gemma2`)로 글·댓글 자동 요약을 붙였습니다.

> 200줄짜리 `main.py` 하나를 계층별로 쪼개보고 나서야, 왜 남들이 파일을 나누는지 이해했습니다.

---

## 🛠 Tech Stack

**AI / ML**

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/>
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/CUDA-76B900?style=for-the-badge&logo=nvidia&logoColor=white"/>
</p>

**LLM / RAG**

<p>
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white"/>
  <img src="https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge&logo=langgraph&logoColor=white"/>
  <img src="https://img.shields.io/badge/LangSmith-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black"/>
  <img src="https://img.shields.io/badge/Chroma-FF6B6B?style=for-the-badge&logo=chromatic&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white"/>
</p>

**Backend / Infra**

<p>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white"/>
</p>

**Collaboration**

<p>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white"/>
  <img src="https://img.shields.io/badge/Confluence-172B4D?style=for-the-badge&logo=confluence&logoColor=white"/>
  <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white"/>
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white"/>
  <img src="https://img.shields.io/badge/Miro-050038?style=for-the-badge&logo=miro&logoColor=white"/>
</p>

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://streak-stats.demolab.com?user=HojuneLee0106&hide_border=true&ring=2a78d6&fire=2a78d6&currStreakLabel=2a78d6" alt="Streak"/>
</p>

---

## 🏅 Activities & Certification

### 🎓 LG Aimers 7기 · Data Intelligence <sub>2025.07.01 ~ 2025.08.25 수료</sub>


<details>
<summary>수료증 보기</summary>
<br/>
<img src="assets/lg-aimers-cert.png" alt="LG Aimers 7기 Data Intelligence 수료증" width="72%"/>
</details>

<br/>

### 🏈 숭실대학교 크루세이더스 (중앙 미식축구부)

- 회장 <sub>2023.10 ~ 2024.11</sub>
- 디펜스 캡틴 <sub>2022.06 ~ 2025.12</sub>
- 2025 서울 대학 미식축구 최강자전 **디비전 2 준우승**

<br/>

### 📜 Certification

- OPIc **IH** <sub>2026.03</sub>
- 정보처리기사 <sub>2026.07 취득 예정</sub>
- ADSP <sub>2026.08 취득 예정</sub>
---


