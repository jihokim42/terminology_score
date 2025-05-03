# terminology_score
## 🎯 Project Topic

- IT 전문 용어 자동 추출 및 점수화
    - TF-IDF + 명사 N-gram 기반 키워드 후보군 생성
    - Score Penalty를 통한 일반 단어 필터링

---

## 🗂️ Data

- **코퍼스**
    - yozm IT 문서 크롤링 (약 3000개의 문서)
- **전처리**
    - Okt 형태소 분석을 이용한 명사 토큰화
    - 불용어 제거 및 정규화 (소문자화, 특수문자 제거)
    - Subtractive Filtering으로 일상어 차집합 처리

---

## ⚙️ Process

1. **형태소 분석**
    - KoNLPy의 Okt로 문서를 명사 단위로 분해
2. **N-gram 후보 생성**
    - 명사 1–3-gram 조합으로 용어 후보 집합 구성
3. **TF-IDF 계산**
    - 문서별 용어 가중치 산출
4. **Score Penalty 적용**
    - 전체 문서 빈도 기반 페널티 로직으로 일반 단어 점수 저감
5. **불필요 후보 제거**
    - Subtractive Filtering 기법으로 약어·일상어 제거
6. **최종 추출**
    - 점수 상위 N개 용어 후보를 최종 리스트로 선정

---

## 🛠️ 사용 기술

- **언어처리**: Python, KoNLPy (Okt)
- **키워드 추출**: Scikit-learn TF-IDF, N-gram 처리, 커스텀 페널티 로직
- **정의 생성** : RAG
- **평가 지표**: Precision@K, Recall@K, F1-score (수동 검수 병행)
