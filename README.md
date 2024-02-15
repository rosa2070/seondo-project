# :pushpin: KoreanSearch
>빅데이터 기반 한글 언어처리 검색 솔루션
>https://go-quality.dev(데모링크)

</br>

## 1. 제작 기간 & 참여 인원
- 2023년 7월 10일 ~ 8월 11일
- 팀 프로젝트(5명)

</br>

## 2. 사용 기술 (버전 명시하기)
#### `Back-end`
  - Django
  - Docker
#### `Front-end`
  - Bootstrap

</br>

## 3. ERD 설계 (DB 테이블 설계)


## 4. 핵심 기능
이 서비스의 핵심 기능은 한국어 텍스트 데이터를 활용한 검색 솔루션 기능입니다.  
세부적인 기능은 검색 후 유사도순으로 요약된 기사 출력, 연관 검색어 출력, 출력된 기사에 대한 긍/부정 출력 이렇게 3가지입니다. 이를 각각 문서유사도와 본문요약 모델, 연관어 추천 모델, 감성분석 모델을 활용해 구현하였습니다.
<details>
<summary><b>핵심 기능 설명 펼치기</b></summary>
<div markdown="1">

### 4.1. 유사도순으로 요약된 기사 출력 
- 인천서구 입력 시 
![summary](https://github.com/rosa2070/seondo-project/assets/46918839/0eb14256-c095-462b-bd19-650a0e755c9c)
- **요약 모델** : KoBART :pushpin: [코드 확인](koBART텍스트요약.ipynb)

### 4.2. 연관 검색어 출력
![associate](https://github.com/rosa2070/seondo-project/assets/46918839/a85ed3e3-af60-449c-914a-233c4ddcd63c)
- **연관어 추출 모델** : FastText :pushpin: [코드 확인](fasttext연관어추출.ipynb)

### 4.3. 각 기사에 대한 긍/부정 출력
![emotion](https://github.com/rosa2070/seondo-project/assets/46918839/9dc9fbfb-1fe0-4035-aa0c-d96566a8bc10)

### 4.4 빠른 웹 구현을 위해 저장 모델 불러오기
- hugging face에 있는 KoBART로 구현된 본문요약 모델 저장 후 불러오기
- :pushpin: [코드 확인](hugging_face_모델_미리_저장.ipynb) 



</div>
</details>

</br>


## 5. 핵심 트러블 슈팅
### 5.1. 연관어 추출 모델 변경
- 처음에 연관어 추출 모델로 TF-IDF를 사용하려고 했습니다. TF-IDF의 경우 모델의 입력값으로 문서의 집합, 즉 뉴스 본문 데이터 전체가 들어가야 합니다.
- 하지만 검색어 솔루션을 구현하기 위해서는 검색어를 입력값으로 받아 연관어를 추출해야 했기에 TF-IDF가 맞지 않는 모델이라고 판단하고 FastText 모델을 변경했습니다.
- **모델 변경 전** : TF-IDF :pushpin: [코드 확인](tf-idf연관어추출.ipynb)
- **모델 변경 후** : FastText :pushpin: [코드 확인](fasttext연관어추출.ipynb)




