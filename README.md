# 📚 프로젝트 통합 README

이 저장소는 3가지 주요 AI 프로젝트를 포함하고 있습니다.

## 1\. 🤖 AI Chatbot Project (AI챗봇 프로젝트)

RAG(Retrieval-Augmented Generation) 기반의 AI 챗봇 프로젝트입니다.

### 📁 주요 파일

  * `아프간_AI_chatbot.ipynb`: LangGraph, LangChain을 사용하여 RAG 파이프라인과 대화 흐름을 정의하고 챗봇을 실행하는 메인 파일
  * `data_preprocessing.ipynb`: 챗봇의 지식 기반(Knowledge Base)을 구축하기 위해 원본 데이터를 전처리하고 MongoDB에 저장하는 과정 및 벡터 DB(Chroma)를 생성하는 파일

### ✨ 주요 기능

  * **RAG 기반 답변 생성:** 외부 지식 문서(아프간 관련 데이터로 추정)를 검색하여 답변의 정확도를 높입니다.
  * **LangGraph 기반 대화 흐름:** 복잡한 대화 로직 및 라우팅을 효율적으로 관리합니다.
  * **MongoDB 로깅:** 모든 대화 기록을 MongoDB에 저장하여 로그를 관리하고 분석할 수 있습니다.
  * **Upstage 통합:** Upstage의 SOLAR 모델 및 임베딩을 활용하도록 구성 가능합니다.

### 🚀 실행 방법

1.  **환경 설정:** `.env` 파일에 `UPSTAGE_API_KEY` 및 `MONGODB_URI`를 포함한 필수 환경 변수를 설정합니다.
2.  **데이터 전처리:** `data_preprocessing.ipynb` 파일을 실행하여 MongoDB에 데이터를 적재하고, 임베딩을 생성하여 Chroma DB를 구축합니다. **(주의: 임베딩 차원 문제 발생 시 기존 Chroma DB 폴더를 삭제 후 재실행해야 합니다.)**
3.  **챗봇 실행:** `아프간_AI_chatbot.ipynb` 파일을 실행하여 챗봇 서비스를 시작합니다.

-----

## 2\. 📝 AI 다이어리 글 변환

개인적인 글(다이어리 등)의 스타일이나 형식을 특정 컨셉에 맞춰 변환하는 AI 기반의 글쓰기 보조 프로젝트입니다.

### 📁 주요 파일

  * `AI다이어리_글변환.ipynb`: 사용자의 입력 텍스트를 분석하여 글 형식 스타일로 변환하는 LLM 파이프라인(LangChain/LangGraph 사용 추정)을 구현합니다.

### ✨ 주요 기능

  * **스타일 변환:** 입력된 글의 어조, 감성, 문체 등을 기존에 설정된 형식 기준대로 변경합니다.
  * **프롬프트 엔지니어링:** LLM을 활용하여 창의적이고 자연스러운 글 변환을 수행합니다.

### 🚀 실행 방법

  * `AI다이어리_글변환.ipynb` 파일을 열고, 노트북 내의 예시 셀에 사용자의 텍스트와 원하는 변환 스타일을 입력한 후 실행합니다.

-----

## 3\. 💬 댓글 담론화 및 LDA 분석

대규모 댓글 데이터를 수집 및 전처리하고, LDA(Latent Dirichlet Allocation) 토픽 모델링을 사용하여 댓글의 주요 담론(Topic)을 추출하고 시각화하는 프로젝트입니다.

### 📁 주요 파일

  * `댓글담론화 LDA.ipynb`:
      * YouTube 댓글 데이터 수집(크롤링 로직 포함 추정).
      * 텍스트 전처리 및 형태소 분석.
      * LDA 모델 학습 및 토픽 추출.
      * 토픽 모델의 적합성(Coherence, Perplexity) 평가 및 시각화.
  * `유튜브영상리스트.xlsx`: 크롤링 대상이 되는 YouTube 영상 URL 목록이 담긴 파일 (CSV 형태로 변환되어 사용됨).

### ✨ 주요 기능

  * **데이터 크롤링:** `유튜브영상리스트`에 기반하여 대량의 댓글 데이터를 수집합니다.
  * **토픽 모델링 (LDA):** 수집된 댓글 내에 내재된 주요 관심사나 논의 주제를 통계적으로 도출합니다.
  * **모델 평가:** 토픽 모델의 성능을 정량적으로 평가하여 최적의 토픽 개수를 결정합니다.
  * **시각화:** Coherence Score 및 Perplexity 시각화를 통해 분석 결과를 직관적으로 제시합니다.

### 🚀 실행 방법

1.  **데이터 준비:** `유튜브영상리스트.xlsx` (CSV 파일)이 올바른 경로에 있는지 확인합니다.
2.  **분석 실행:** `댓글담론화 LDA.ipynb` 파일을 순서대로 실행하여 데이터 수집부터 LDA 분석, 그리고 시각화까지 진행합니다.

-----

## ⚙️ 개발 환경 설정

이 프로젝트를 실행하기 위해 필요한 패키지들은 각 노트북 파일의 상단에 명시되어 있습니다. 일반적으로 다음 패키지들이 필요합니다.

```bash
pip install -U langchain langchain-upstage pymongo python-dotenv pandas pydantic scikit-learn
# LDA 분석을 위한 추가 패키지
pip install gensim pyLDAvis matplotlib
# 크롤링을 위한 추가 패키지
pip install selenium beautifulsoup4
```

### 🗝️ 환경 변수 (`.env`)

프로젝트를 실행하기 전에 다음 변수를 설정해야 합니다.

| 변수명 | 설명 | 예시 값 |
| :--- | :--- | :--- |
| `UPSTAGE_API_KEY` | Upstage API 사용을 위한 키 | `sk-upstage-xxxxxxxxxxxxxxxxxxxx` |
| `MONGODB_URI` | MongoDB 연결을 위한 URI | `mongodb://localhost:27017/` |
