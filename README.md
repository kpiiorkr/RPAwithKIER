# 비즈니스 프로세스 혁신을 위한 RPA 기술 동향 및 지능형 자동화 프레임워크 연구

**A Study on RPA Technology Trends and Intelligent Automation Framework for Business Process Innovation**

강승원1, 김덕환2, 김종우3
Seung Won Kang, Deok Hwan Kim, Zong Woo Geem

1가천대학교 대학원 스마트시티융합학과 박사과정
E-mail: data@gachon.ac.kr

2한국에너지기술연구원 에너지AI·계산과학실 (Korea Institute of Energy Research, Energy AI & Computational Science Laboratory)
E-mail: thekan@kier.re.kr

3가천대학교 스마트시티학과 교수
E-mail: geem@gachon.ac.kr

---

## 요 약

디지털 전환(Digital Transformation) 가속화에 따라 반복적 업무를 소프트웨어 로봇이 자동 수행하는 RPA(Robotic Process Automation)가 기업 및 공공기관에서 핵심 자동화 기술로 부상하고 있다. 본 연구는 RPA의 이론적 배경과 아키텍처를 고찰하고, 공공기관의 실무 도입 전략과 최적화 방안을 제시하며, 한국에너지기술연구원(KIER)의 'E-리서치 큐레이터봇' 구현 사례를 통해 그 실용적 가치를 분석하였다. 동 시스템은 RPA 기반 정보 자동 수집과 생성형 AI를 결합하여 103명의 구독자에게 37일간 누적 3,118건의 맞춤형 연구동향 콘텐츠를 제공하였으며, 기존 수동 업무 대비 정보 수집 및 배포 소요 시간을 획기적으로 단축하는 효과를 거두었다. 아울러 하모니 서치(Harmony Search)와 같은 지능형 최적화 알고리즘을 RPA 자원 스케줄링에 접목하는 방안과, 대규모 언어모델(LLM)과의 융합을 통한 지능형 프로세스 자동화(IPA)로의 발전 방향을 논의하였다. 본 연구는 RPA 도입을 검토하는 연구자 및 실무자에게 실질적 가이드라인을 제공한다.

**키워드:** Robotic Process Automation, Harmony Search, Intelligent Process Automation

---

## Abstract

As digital transformation accelerates, Robotic Process Automation (RPA)—in which software robots execute repetitive, rule-based tasks autonomously—has emerged as a pivotal automation technology in enterprises and public institutions. This study reviews the theoretical foundations and architecture of RPA, proposes a strategic framework for practical deployment in public-sector organizations, and analyzes a real-world case from the Korea Institute of Energy Research (KIER): the 'E-Research Curator Bot.' By integrating RPA-driven data collection with a large language model (LLM)-based curation pipeline, the system delivered 3,118 personalized research-trend contents to 103 subscribers over a 37-day pilot period, substantially reducing the time researchers spent on manual information gathering and distribution. We further discuss how intelligent optimization algorithms such as Harmony Search can enhance RPA resource scheduling, and how deeper LLM integration can advance RPA toward Intelligent Process Automation (IPA). The findings offer practical guidelines for researchers and practitioners considering RPA adoption.

**Key Words:** Robotic Process Automation, Harmony Search, Intelligent Process Automation

---

## 1. 서  론

현대 비즈니스 환경은 디지털 전환(Digital Transformation, DX)의 가속화에 따라 운영 효율성 확보가 중요해지고 있다. 이러한 흐름 속에서 소프트웨어 로봇이 인간을 대신하여 반복적이고 정형화된 업무를 자동으로 수행하는 RPA(Robotic Process Automation)가 하이퍼오토메이션(Hyper-automation) 시대를 이끄는 핵심 기술로 주목받고 있다.

RPA는 별도의 시스템 연동 없이 사람이 사용하는 화면(GUI)을 그대로 조작하므로 기존 IT 인프라에 대한 침습성이 낮고 도입 기간이 짧다는 강점이 있다. 레거시 시스템이 혼재하는 기업 및 공공 연구기관 환경에서 RPA는 시스템 통합 없이도 빠른 자동화 효과를 거둘 수 있어 주목받고 있다.

최근에는 다양한 대규모 언어모델(LLM: Large Language Model)이 급속히 발전하면서 RPA의 인지 모듈로 LLM을 결합하는 시도가 활발해지고 있다. 이러한 RPA와 LLM의 융합은 룰 기반(Rule-based) 자동화의 한계를 넘어 비정형 데이터의 이해, 요약, 판단 기능을 RPA 워크플로우에 내재화하는 지능형 프로세스 자동화(IPA: Intelligent Process Automation)로의 전환을 가속화하고 있다.

본 연구는 다음의 세 가지 목적을 가진다. 첫째, RPA 기술의 이론적 배경과 아키텍처를 체계적으로 고찰한다. 둘째, 기업 및 공공기관이 RPA를 효과적으로 도입하기 위한 전략적 프레임워크를 제시한다. 셋째, 한국에너지기술연구원(KIER) 지식정보실의 'E-리서치 큐레이터봇' 실무 사례를 실증 데이터와 함께 분석하여 RPA와 생성형 AI 결합의 실질적 효과를 검증한다. 이를 통해 RPA 도입을 검토하는 연구자 및 실무자에게 구체적인 참고 가이드라인을 제공하고자 한다.

---

## 2. RPA 기술의 이론적 배경

### 2.1 RPA의 정의 및 진화 단계

RPA(Robotic Process Automation)는 사람이 컴퓨터에서 수행하는 정형화된 UI 조작(데이터 입력, 복사 및 붙여넣기, 보고서 생성, 시스템 간 데이터 이동 등)을 소프트웨어 로봇이 대신 수행하도록 하는 자동화 기술이다. 여기서 '로봇'이란 물리적 기계가 아닌 소프트웨어 에이전트(Software Agent)를 의미하며, 전통적 로봇공학(Robotics) 개념과는 구별된다.

RPA는 발전 양상에 따라 크게 세 단계로 구분된다.

- **RPA 1.0 (단순 자동화):** 단일 데스크톱 기반의 매크로 수준 자동화로, 사전에 정의된 스크립트에 따라 반복 작업을 수행한다. 처리량이 크지 않고 예외 처리 능력이 제한적이다.
- **RPA 2.0 (중앙 관리형 자동화):** 서버 기반 오케스트레이터(Orchestrator)를 통해 다수의 봇을 중앙에서 스케줄링 및 관리할 수 있게 되어, 대규모 업무 처리와 보안 관리가 가능해졌다. UiPath, Automation Anywhere, Blue Prism 등 상용 솔루션이 이 단계를 대표한다.
- **RPA 3.0 (지능형 프로세스 자동화, IPA):** OCR(광학 문자 인식), 자연어 처리(NLP), 머신러닝, 그리고 최근에는 LLM과 결합하여 비정형 데이터를 처리하고 예외 상황에서도 유연하게 대응하는 단계이다. 이 단계에서는 단순한 도구를 넘어 스스로 판단하고 학습하는 인지 자동화(Cognitive Automation) 개념이 실현된다.

### 2.2 RPA 아키텍처의 구성 요소

상용 RPA 플랫폼은 일반적으로 세 가지 핵심 컴포넌트로 구성된다. 표 1은 각 구성 요소의 역할과 기능을 요약한 것이다.

**표 1. RPA 아키텍처 핵심 구성 요소**

| 구성 요소 | 역 할 | 주요 기능 |
|---|---|---|
| Development Studio | 워크플로우 설계 도구 | 드래그 앤 드롭 기반 로우코드(Low-code) 환경에서 봇 시나리오 개발 |
| Execution Bot | 실행 에이전트 | 설계된 스크립트에 따라 UI 조작, API 호출, 데이터 처리 등 실제 업무 수행 |
| Management / Orchestrator | 중앙 제어 센터 | 봇 스케줄링, 자원 할당, 로그 및 모니터링, 보안 접근 제어 및 예외 처리 관리 |

### 2.3 RPA의 강점과 한계

RPA의 가장 큰 강점은 기존 시스템의 변경 없이도 빠른 자동화 효과를 낼 수 있다는 점이다. 특히 화면(UI) 수준에서 동작하기 때문에 내부 API나 데이터베이스 접근 권한 없이도 레거시 시스템을 자동화할 수 있어, 기존 IT 투자를 보호하면서 점진적으로 자동화를 확대할 수 있다.

반면 RPA는 화면 구조(UI)가 변경되면 봇이 오동작하는 취약성이 있으며, 구조화되지 않은 비정형 데이터 처리에는 근본적인 한계가 있다. 또한 봇 수가 늘어날수록 유지보수 복잡도가 급격히 증가하는 이른바 봇 스프롤(Bot Sprawl) 문제가 발생할 수 있는데, 이는 조직 내 개별 부서가 각자 봇을 개발하고 운영하면서 봇의 총 수가 통제 불가능하게 증가하고 중복, 충돌, 유지보수 부재 상태가 누적되는 현상을 말한다.

---

## 3. 지능형 RPA 도입 전략 및 최적화

### 3.1 자동화 대상 공정 선정 (Process Discovery)

성공적인 RPA 도입을 위한 첫 단계는 자동화 적합 업무를 올바르게 선정하는 것이다. 일반적으로 자동화 적합성은 처리량(Volume), 규칙 기반 정도(Rule-based), 표준화 수준(Standardization), 디지털 입력 비율(Digital Input)의 네 가지 기준으로 평가된다.

정보 수집 및 배포 업무는 이 네 가지 기준을 모두 충족하는 RPA 최적 적용 분야이다. 주기적으로 동일한 사이트를 방문해 특정 형식의 데이터를 수집하고, 사전 정의된 규칙에 따라 필터링 및 배포하는 프로세스는 RPA로 자동화하기에 이상적이다. 본 연구의 사례 대상인 KIER의 연구동향 수집 업무 역시 이와 같은 조건을 갖추고 있었다.

### 3.2 RPA 자원 스케줄링과 하모니 서치 최적화

복수의 봇이 운영되는 RPA 시스템에서는 봇의 작업 스케줄링과 자원 배분이 전체 처리 효율에 직결된다. 처리 요청이 특정 시간대에 집중되거나 봇이 비효율적으로 배정될 경우 전체 파이프라인의 지연과 자원 낭비가 발생할 수 있다.

하모니 서치(Harmony Search, HS) 알고리즘은 이러한 스케줄링 최적화 문제에 접목 가능한 계산지능 기반 최적화 기법이다. HS는 음악가들이 즉흥 연주를 통해 최고의 화음을 찾아가는 과정에서 영감을 받아 고안되었으며, 기존의 기울기(gradient) 기반 최적화 기법과 달리 연산이 거듭될수록 쌓아가는 경험 도함수(Experience Derivative)를 활용하여 해공간을 탐색한다. 이 특성은 미분이 불가능하거나 불연속인 목적함수에서도 안정적으로 동작한다는 강점으로 이어지며, 봇 배정 시간대와 자원 조합이 방대한 RPA 스케줄링 문제와 잘 부합한다.

HS 알고리즘의 핵심 파라미터는 하모니 메모리 고려율(HMCR: Harmony Memory Consideration Rate)과 음조 조정율(PAR: Pitch Adjustment Rate)이며, 이 두 파라미터의 적절한 설정이 수렴 속도와 해의 품질에 결정적 영향을 미친다. 선행 연구에서는 이 파라미터 설정을 자동화하는 Parameter-Setting-Free 기법도 개발된 바 있다. HS는 수자원 공학의 상수도 관망 최적설계, 수문모형 계수추정, 댐 연계운영 스케줄링, 전기공학의 마이크로그리드 운영비용 최소화, 무선센서네트워크 클러스터링, 컴퓨터공학의 CNN 하이퍼파라미터 결정 등 다양한 분야에서 기존 유전 알고리즘, 분지한계법 등 대비 우수한 결과를 보고한 바 있다.

RPA 자원 스케줄링 문제는 다수의 봇(연주자)이 한정된 서버 자원(악기)을 공유하며 업무(음악)를 처리하는 구조와 개념적으로 유사하다. HS의 음조 조정 과정, 즉 메모리 내 최적 해들을 참고하여 새로운 해를 생성하고 일정 확률로 인접 탐색을 수행하는 절차는 봇 배정 경우의 수가 방대한 조합 최적화 공간에서 효율적인 탐색을 가능케 한다. 다만 RPA 스케줄링에의 적용은 본 연구에서 개념적 가능성을 제시하는 수준이며, 구체적인 정량 실증은 향후 연구 과제로 남긴다.

### 3.3 변화 관리와 거버넌스

RPA 도입의 기술적 성공만큼 중요한 것이 조직적 변화 관리와 거버넌스 체계 수립이다. RPA 도입 초기에는 담당자 저항, 봇 관리 인력 미확보, 보안 및 감사 정책 부재 등이 주요 실패 원인으로 꼽힌다. 따라서 RPA 도입 시에는 전담 CoE(Center of Excellence) 조직 구성, 저작권 및 데이터 보안 법무 검토, 사용자 교육 등의 제반 여건을 먼저 갖추는 것이 권장된다.

---

## 4. 사례 연구: KIER 'E-리서치 큐레이터봇'

### 4.1 시스템 구축 배경

한국에너지기술연구원(KIER)은 에너지 분야 연구자들이 방대한 연구동향 정보를 효율적으로 습득할 수 있는 시스템 구축 필요성을 인식하였다. 매일 쏟아지는 막대한 양의 논문, 보고서, 뉴스를 기존 방식으로 수집하고 이해하는 데는 현실적 한계가 있었으며, 정보 출처별 구독 서비스를 개별 신청하고 각각의 메일을 확인하고 영문 자료를 직접 번역하는 비효율성이 연구 생산성을 저해하고 있었다. 이에 KIER 지식정보실은 NST 디지털전환 아이디어 공모 사업의 일환으로, RPA와 생성형 AI를 결합한 자동화 정보 큐레이션 시스템을 기획하였다.

### 4.2 시스템 아키텍처 및 구현

E-리서치 큐레이터봇은 구독자 정보수집 파트와 콘텐츠 수집 및 메일링 파트의 두 축으로 설계되었다. 그림 1은 전체 시스템의 데이터 흐름을 나타낸다.

> **[그림 1]** E-리서치 큐레이터봇 시스템 아키텍처
> 외부 정보 소스(9종) → RPA 수집 → AI 큐레이션(필터링 및 요약) → DB → 메일 자동 발송

구독자 정보수집 파트는 연구자가 관심 키워드와 수신 주기를 설정할 수 있는 외부용 및 내부용 웹페이지로 구성된다. Cloudflare의 분산 CDN(Content Delivery Network) 기반 Edge Computing을 활용하여 자체 서버 부하 없이 고가용성을 확보하였으며, 구독자 관심사는 OpenAI 임베딩 API를 통해 벡터화되어 RPA 서버에서 개인화 필터링에 활용된다.

콘텐츠 수집 및 메일링 파트는 MS Power Automate for Desktop이 예약 시간에 자동 실행되어 9종의 정보 소스로부터 데이터를 수집한다. 정보 소스는 BigKinds(국내 뉴스, API), SCOPUS(학술논문, API), KERC, KEEI, KDB, PV Magazine, ARPAE, Hydrogen Fuel News, SNE Research(보고서 및 아티클, Web Scraping)로 구성된다. 수집된 데이터는 신규성 판단, 도메인 관련성 필터링, 중복성 필터링, 개인 맞춤형 필터링의 4단계 구조를 거쳐 정제된다.

AI 큐레이션은 두 가지 방식으로 구현된다. 관련성 필터링 단계에서는 구독자 관심사와 수집 정보를 각각 임베딩 벡터로 변환한 후 Cosine Similarity를 계산하여 관련성 높은 콘텐츠를 선별한다. 텍스트 생성 단계에서는 OpenAI의 생성형 AI API를 통해 수집된 정보의 요약문과 구독자 맞춤형 메일 본문을 생성한다. 이와 같이 임베딩 기반 유사도 검색과 생성형 AI를 결합함으로써 단순 키워드 매칭을 넘어 의미론적 관련성 판단이 가능해졌다.

### 4.3 법무 검토 및 저작권 대응

외부 정보를 자동 수집하여 배포하는 시스템에서 저작권 문제는 핵심 리스크 요인이다. KIER은 전문 법무법인을 통해 수집 대상 정보 출처에 대한 법무 검토를 실시하였으며, 그 결과 로봇 사용을 명시적으로 금지하는 IEA, IRENA, 외교부 등의 출처를 서비스 대상에서 제외하였다. 최종 운영 대상으로 선정된 출처들에 대해서는 공식 API 활용(BigKinds, SCOPUS), 명시적 금지 규정 부재 확인(KERC, KDB 등), 직접 링크 방식의 저작권 준수 방안을 적용하였다.

또한 수집된 원문 내용은 RAM에서 일시적으로만 처리하고 영구 저장하지 않으며, 구독자에게는 제목, 날짜, URL, 요약문만을 제공하고 원저작자에 대한 귀속 고지를 반드시 포함함으로써 법적 위험을 최소화하였다.

### 4.4 시범 운영 성과

시스템은 2025년 2월부터 설계를 시작하여 총 6개월의 개발 기간을 거쳐, 2025년 10월 16일부터 11월 21일까지 37일간 시범 운영되었다. 표 2는 시범 운영의 주요 정량적 성과를 정리한 것이다.

**표 2. 시범 운영 주요 성과 요약**

| 지 표 | 내 용 | 수 치 |
|---|---|---|
| 시범운영 기간 | 2025.10.16~2025.11.21 | 37일 |
| 구독자 수 | 대내외 홍보를 통해 모집 | 103명 |
| 제공 콘텐츠 수 | 맞춤형 콘텐츠 누적 제공 | 3,118건 |
| 정보 소스 종류 | 뉴스, 논문, 보고서, 아티클 | 9종 |
| 사업 예산 | RPA 서버, 웹서버, 외주, 법무 등 | 약 2,000만원 |
| 잠재적 기대효과 | 연간 시간 절감 환산 인건비 | 약 250배 이상 |

시범 운영 기간 중 구독자 수는 홍보 활동에 따라 지속 증가하였으며, 내외부 구독자 의견 수렴을 통해 중복성 필터링 임계값 조정, UI 개선, 정보 출처 확대 등의 후속 개선 방향을 도출하였다. 시스템의 잠재적 기대효과는 에너지기술연구원 연구 및 기술직 877명(연구기술직 476명, 비정규연구직 401명, 2024년 10월 기준)을 대상으로 현행 주당 8시간에서 4시간으로의 정보 수집 시간 절감을 가정할 때, 연간 약 53억 8,800만원(877명 x 4시간/주 40시간/주 x 61,440천원)의 생산성 향상에 해당하며, 이는 투입 예산(약 2,000만원) 대비 250배 이상의 잠재적 효과이다.

---

## 5. 지능형 자동화로의 전이와 미래 전망

### 5.1 LLM과 RPA의 융합 가능성

현재의 RPA는 사전 정의된 규칙 내에서 정형 데이터를 처리하는 데 강점이 있지만, 비정형 문서의 맥락 이해와 예외적 상황에서의 판단에는 근본적 한계가 있다. ChatGPT, DeepSeek, Gemini, Llama 등 최신 LLM을 RPA 워크플로우의 인지 모듈로 통합하면 다음과 같은 고도화가 가능하다.

- **비정형 문서 처리:** 수집된 논문이나 보고서의 핵심 내용을 자동으로 요약하고 주제 관련성을 의미론적으로 평가하는 기능을 RPA 파이프라인 내에 내재화할 수 있다.
- **의사결정 지원:** 텍스트 데이터의 중요도 판단, 이상 징후 감지 등을 통해 기존 규칙 기반 분기 처리를 AI 기반 판단으로 고도화할 수 있다.
- **자연어 기반 봇 구성:** 사용자가 자연어로 업무 요건을 기술하면 LLM이 이를 해석하여 RPA 워크플로우를 자동으로 생성하는 생성형 자동화(Generative Automation)가 실현되고 있다.

본 연구의 KIER 사례는 RPA와 LLM의 결합이 실제 운영 환경에서 작동함을 보여주는 구체적 사례이다. 특히 사내 전용 LLM(Private LLM)을 기반으로 한 툴 호출 기반 RAG(Retrieval-Augmented Generation) 시스템은 기업 내 데이터 거버넌스와 응답 신뢰성을 동시에 확보하는 구현 방식으로 주목받고 있다.

표 3은 기존 규칙 기반 RPA와 LLM 결합형 IPA의 주요 특성을 비교한 것이다.

**표 3. 기존 RPA와 LLM 결합형 IPA 비교**

| 구 분 | 기존 RPA (Rule-based) | LLM 결합 IPA (Reasoning-based) |
|---|---|---|
| 처리 데이터 | 정형 데이터 위주 | 정형 및 비정형 데이터 |
| 예외 처리 | 사전 정의 규칙 한정 | 맥락 이해 기반 유연 대응 |
| 설정 방식 | 스크립트 개발 필요 | 자연어 지시 가능 |
| 도입 난이도 | 낮음~중간 | 중간~높음 |
| 운영 비용 | 상대적으로 낮음 | AI API 비용 추가 발생 |
| 대표 사례 | 본 연구 KIER 사례 | AI 에이전트 기반 업무 자동화 |

### 5.2 자율형 AI 에이전트로의 진화

미래의 RPA는 단순한 스크립트 실행 도구를 넘어, 사용자의 자연어 지시를 스스로 해석하고 실시간으로 업무 프로세스를 생성 및 실행하는 에이전트형 시스템으로 발전할 것으로 전망된다. 최근 주요 AI 기업들이 출시한 에이전트 플랫폼은 복잡한 멀티스텝 태스크를 자율적으로 계획하고 실행하는 능력을 빠르게 고도화하고 있다.

이는 RPA가 단순한 도구(Tool)를 넘어 인간과 협업하는 파트너 수준으로 진화함을 의미한다. 다만 이 과정에서 AI 에이전트의 할루시네이션(Hallucination), 보안 취약점, 데이터 거버넌스 등의 새로운 리스크에 대한 체계적 대응 방안 마련이 병행되어야 한다.

---

## 6. 결  론

본 연구는 비즈니스 프로세스 혁신을 위한 RPA 기술의 이론적 배경과 실무 도입 전략을 고찰하고, KIER E-리서치 큐레이터봇의 실증 사례를 통해 RPA와 생성형 AI의 결합이 조직의 정보 관리 효율성을 어떻게 혁신하는지 분석하였다.

사례 연구 결과, RPA 기반 정보 자동 수집과 LLM 기반 큐레이션을 결합한 시스템은 37일간의 시범 운영에서 103명의 구독자에게 3,118건의 맞춤형 연구동향 콘텐츠를 안정적으로 제공하였다. 이는 단순한 업무 자동화를 넘어 연구자들이 고부가가치 핵심 업무에 집중할 수 있도록 지원하는 지식 인프라로서의 가능성을 실증한 것이다.

아울러 하모니 서치 알고리즘과 같은 지능형 최적화 기법을 RPA 자원 스케줄링에 접목함으로써 시스템 처리 효율을 추가로 향상시킬 수 있는 가능성을 논의하였으며, LLM과의 심층 결합을 통한 지능형 프로세스 자동화(IPA)로의 발전 방향을 제시하였다.

본 연구가 RPA 도입을 검토하는 연구자 및 실무자들에게 실질적인 가이드라인이 되기를 기대하며, 향후 연구에서는 하모니 서치 기반 RPA 스케줄링 최적화 모델의 정량적 실증과 LLM 결합 시스템의 보안 및 거버넌스 프레임워크에 대한 보다 깊은 탐구가 이루어지기를 제안한다.

---

## 사  사
※ KIER E-리서치 큐레이터봇은 2024년 출연(연) 연구행정혁신 아이디어 공모전에서 선정되어, 2025년 국가과학기술연구회의 지원으로 개발된 결과입니다.
The KIER E-Research Curatorbot was selected in the '2024 Research Administration Innovation Idea Contest' and was subsequently developed in 2025 with support from the National Research Council of Science and Technology (NST).

---

## 참 고 문 헌

[1] M. Lacity and L. Willcocks, "Robotic Process Automation at Telefónica O2," MIS Quarterly Executive, vol. 15, no. 1, 2016.

[2] Z. W. Geem, J. H. Kim, and G. V. Loganathan, "A New Heuristic Optimization Algorithm: Harmony Search," Simulation, vol. 76, no. 2, pp. 60-68, Feb. 2001.

[3] Z. W. Geem, "Music-Inspired Harmony Search Algorithm and Its Experience-Based Derivative," New Physics: Sae Mulli, vol. 67, no. 5, pp. 608-614, May 2017.

[4] Z. W. Geem, "Parameter Estimation of the Nonlinear Muskingum Model Using Parameter-Setting-Free Harmony Search," Journal of Hydrologic Engineering, ASCE, vol. 16, no. 8, pp. 684-688, Aug. 2011.

[5] Z. W. Geem, K. Gnawali, K. H. Han, and K. T. Yum, "Review on Harmony Search Algorithm Applied to Water Resources Engineering," J. Korean Inst. Intell. Syst., vol. 30, no. 4, pp. 284-289, Aug. 2020.

[6] Z. W. Geem, "Review on Theory and Applications of Harmony Search Algorithm based on Korea Citation Index," J. Korean Inst. Intell. Syst., vol. 32, no. 3, pp. 244-253, June 2022.

[7] 한국에너지기술연구원, "리서치 트렌드 큐레이터봇 구현 결과 보고서," NST 디지털전환 아이디어 개발, 2025년 11월.

[8] S. E. Kim and Z. W. Geem, "Case Study: Tool-Calling RAG with Private LLM in Multi-Tenant Enterprise Environment," J. Korean Inst. Intell. Syst., vol. 36, no. 1, pp. 42-48, Feb. 2026.
