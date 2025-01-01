# GNN(Masked Language Model)을 활용한 테마 분산투자 (Done)
---

## 목차 (Table of Contents)

1. [프로젝트 소개 (Introduction)](#프로젝트-소개-introduction)  
2. [분석 개요 (Overview)](#분석-개요-overview)  
3. [프로젝트 구조 (Project-Structure)](#프로젝트-구조-project-structure)  


---

## 프로젝트 소개 (Introduction)

- **목적**: 실제 금융 투자에 적합한 감성분석 
- **선행 연구의 한계**:
  - 현재 금융 문서의 감성분석은 투자자들이 원하는 긍,부정이라고 보기 어렵다.
    
  예를 들어 " '삼성전자'의 주가가 10% 상승했다" 라는 문장은 높은 강도로 긍정이 나온다. 하지만 이러한 정보는 투자에 도움이 되지 않는다. 이와 같은 문제를 해결 할 수 있을까?
- **가설**:
  - A기업과 관련된 문서에서 A기업명을 전부 MASK 씌우고 해당 훈련된 모델이 해당 MASK를 잘 맞춘다면 문서는 A기업과 밀접하게 연관되어 있을 것이다. 

이 저장소를 활용하면 공통적으로 발생하는 데이터 분석 단계를 보다 효율적으로 수행할 수 있습니다.

---

## 분석 개요 (Overview)
###  1. 데이터 분류 (Data Classification)


- **데이터 전처리**: 결측치 처리, 이상치 탐지, 스케일링 등  
- **데이터 탐색(EDA)**: 통계 요약, 분포 분석, 상관분석, 시각화  
- **모델 학습 및 예측**: 머신러닝/딥러닝 기법을 사용한 분류, 회귀 등  
- **결과 정리**: 분석 결과를 Notebook 형태로 체계적으로 정리  

---

## 프로젝트 Flow (Project structure)

## 프로세스 개요

1. **네이버 애널리스트 리포트 크롤링**  
   - 인터넷 상의 애널리스트 보고서를 수집하는 단계

2. **텍스트 변환**  
   - 수집한 데이터를 텍스트 형태로 전처리(HTML 태그 제거, 인코딩 통일 등)

3. **언어모델 감성분석**  
   - 전처리된 텍스트 데이터를 LLM 기반 감성분석 모델에 입력해 긍정·부정 스코어를 산출

4. **Factor Modeling (FF-3 모델 확장)**  
   - 기존 Fama-French 3 Factor 모델에 감성 점수를 추가 팩터로 활용

5. **Black-Litterman 모델 구축**  
   - Factor 모델의 예측값과 p-value를 기반으로 투자자의 견해(뷰)와 불확실성을 반영하여 최적화 포트폴리오 구성

6. **모델 성과 확인**  
   - Backtest, 성과지표(Sharpe, MDD 등)로 결과 평가
   ![최종 성능](./images/performance.png)


---

```mermaid
flowchart LR
    A([네이버 애널리스트 리포트<br>크롤링]) --> B([텍스트 전처리])
    B --> C([언어모델<br>감성분석])
    C --> D([감성 점수 + FF-3 모델<br>Factor Modeling])
    D --> E([Black-Litterman 모델 구축])
    E --> F([성과 평가<br>및 결과 확인])



