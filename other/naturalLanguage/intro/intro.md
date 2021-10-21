## 자연어 처리란?

---

자연어(`natural language`)란 우리가 일상 생활에서 사용되는 언어를 의미한다. 그렇다면 자연어 처리란(`natural language processing`)이란 자연어의 의미를 분석하여 컴퓨터가 처리할 수 있도록 하는 일을 의미한다.

즉 머신러닝을 사용하여 텍스트와 데이터를 처리하고 해석한다는 갓이다.

이러한 NLP(Natural Language Processing)은 Google Cloud에서 설명하길 고객 감정, 영수증 및 인보이스 이해, 문서 분석, 콘탠츠 분류등에 쓰인다고 한다.

## NLP 처리 프로세스

---

간단하게 살펴보면 아래와 같다.

> 1. 텍스트 전처리(`Text Preprocessing`)
>    > 전처리 작업, 토큰화 작업 등 텍스트 정규화 작업을 수행하는 것이 텍스트 전처리 단계이다.

> 2. 피처 벡터화(`Feature Vectorization`)
>    > 전처리된 텍스트에서 피처를 추출하고 여기에 벡터 값을 할당한다. 이러한 기법 중 대표적인 것은 `BOW(Bag of words)`와 `Word2Vec`가 있다.

> 3. 머신러닝 모델링
>    > 피처 벡터화된 데이터에 대하여 모델을 수립하고 학습/예츨을 하는 단계이다.

## 참고자료

---

> https://wikidocs.net/21667

> https://cloud.google.com/learn/what-is-natural-language-processing?hl=ko

> https://bkshin.tistory.com/entry/NLP-1-%EC%9E%90%EC%97%B0%EC%96%B4-%EC%B2%98%EB%A6%ACNatural-Language-Processing%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
