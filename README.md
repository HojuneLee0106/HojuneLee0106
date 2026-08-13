<h1 align="center">이호준 &nbsp;|&nbsp; Hojune Lee</h1>

<p align="center">
  <b>AI/ML Engineer</b><br/>
  NLP &nbsp;·&nbsp; RAG &nbsp;·&nbsp; LLM Agent &nbsp;·&nbsp; Model Evaluation
</p>

<p align="center">
  <a href="mailto:hojune0106@naver.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
  </a>
  <img src="https://komarev.com/ghpvc/?username=HojuneLee0106&style=for-the-badge&color=0A66C2&label=PROFILE+VIEWS" alt="Profile views"/>
</p>

---

## 👋 About Me

> **"만들었다"보다 "정말 나아졌는지 쟀다"를 더 중요하게 생각합니다.**

NLP 프로젝트를 중심으로 STT 성능 개선, TTS 모델 제작, RAG·에이전트 시스템까지 다뤄왔습니다.
한 줄을 고친 뒤 지표가 0.03 올랐을 때 그게 개선인지 측정 노이즈인지 구분하려고,
같은 문항을 3회씩 반복 측정하는 평가 파이프라인부터 만드는 편입니다.

- 🎓 **숭실대학교 소프트웨어학부** (2020.03 ~ 2026.02)
- 🚀 **카카오테크 부트캠프 AI 실무개발 4기** (2026.05 ~ )
- 🎖️ 해병대 1263기 병장 만기전역 (2020.10 ~ 2022.04)
- 🔬 관심 분야 — RAG Architecture, Agent Systems, LLM Fine-tuning, Evaluation

---

## 💼 Experience

### AItheNutrigene · AI/ML 인턴 <sub>2024.12 ~ 2025.02</sub>

**SK Shieldus STT 성능 개선 프로젝트** (약 12주)

N-gram Language Modeling과 Neural Rescoring을 적용해 상용 STT 모델의 인식 오류를 줄였습니다.

| 지표 | Before | After | 개선 |
|---|---|---|---|
| **WER** (단어 오류율) | 18.64% | **14.11%** | ▼ 4.53%p |
| **CER** (문자 오류율) | 6.83% | **5.57%** | ▼ 1.26%p |

`Python` `NVIDIA NeMo` `KenLM`

---

## 🚀 Projects

### ⚖️ [생활법률 RAG 챗봇](https://github.com/HojuneLee0106/online_law) <sub>KTB</sub>

법조문 · 대법원 판례 · 생활법령을 근거로 답하는 법률 Q&A 어시스턴트.
답변의 조문 번호와 사건번호를 **원문에서 그대로 가져와** 인용합니다.

| | |
|---|---|
| **Stack** | LangGraph · Chroma · FastAPI(SSE) · Docker → GHCR → EC2 |
| **Data** | 법조문 5,390청크 · 판례 3,138건(29,820청크) · 생활법령 21,610청크 |
| **Eval** | `answer_quality 0.912` · `citation_grounding 0.984` · `tool_recall 1.000` |
| **설계** | LangSmith로 단일/멀티 에이전트 3개 구조를 비교 후 single 채택 |

가장 큰 교훈은 검색 인프라를 총동원한 개선(+0.031)보다 **모델 교체 한 번(+0.128)이 4배 컸다**는 것,
그리고 **1회 실행 측정으로는 개선과 노이즈를 구분할 수 없다**는 것이었습니다.

<br/>

### 📄 [카카오 약관 QA 시스템](https://github.com/HojuneLee0106/Performance_Improvement_Contest) <sub>KTB 성능 개선 대회 최우수상</sub>

카카오 약관 4종에서 질문에 해당하는 조항을 찾아 **답변과 근거 조항을 함께** 반환하는 RAG.
Google Colab T4 한 대, 외부 API 없이 동작합니다.

| | |
|---|---|
| **성과** | KTB 4기 AI 성능 개선 대회 · 13팀 · **예선 87.138 / 100** |
| **세부** | 검색 MRR `1.0000` · 키팩트 F1 `0.6638` · LLM 판정 `94.450` |
| **검증** | 공개 10문항 검색 recall 12/12 · precision 12/12 |

<br/>

### 🔊 AI Docent Studio <sub>캡스톤디자인 · 2025.09 ~ 2025.12</sub>

사용자 맞춤형 **TTS 모델(VITS)** 제작. 도슨트 음성을 개인화하는 프로젝트로, **RISE 사업 체결**로 이어졌습니다.

`VITS` `PyTorch` `Speech Synthesis`

<br/>

### 🏋️ AI 헬스 자세 교정 어플리케이션 <sub>캡스톤디자인 · 2025.03 ~ 2025.06</sub>

**LoRA** 기법으로 파인튜닝한 헬스케어 맞춤 챗봇. 운동 도메인에 특화된 응답을 생성하도록 경량 학습했습니다.

`LoRA` `PEFT` `FastAPI`

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
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=HojuneLee0106&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&title_color=0A66C2&icon_color=0A66C2" alt="GitHub stats"/>
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=HojuneLee0106&layout=compact&hide=jupyter%20notebook,html&hide_border=true&title_color=0A66C2" alt="Top languages"/>
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=HojuneLee0106&hide_border=true&ring=0A66C2&fire=0A66C2&currStreakLabel=0A66C2" alt="Streak"/>
</p>

---

## 🏅 Activities & Certification

**LG Aimers 7기** <sub>2025.07 ~ 2025.08</sub>
강의 수료 및 곤지암 리조트 매출 분석 해커톤 참가. `LSTM` `RandomForest` 기반 수요 예측 모델 제작.

**숭실대학교 크루세이더스** (중앙 미식축구부)
- 회장 <sub>2023.10 ~ 2024.11</sub> — 부원 70여 명 인솔
- 디펜스 캡틴 <sub>2022.06 ~ 2025.12</sub>
- 2025 서울 대학 미식축구 최강자전 **디비전 2 준우승**

**Certification**
- OPIc **IH** <sub>2026.03</sub>
- 정보처리기사 <sub>2026.07 취득 예정</sub>

---

<p align="center">
  <sub>지금은 RAG 검색이 "있는 조문을 못 찾는" 문제를 파고 있습니다.</sub>
</p>
