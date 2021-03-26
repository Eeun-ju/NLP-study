# NLP-study
### [성별분류]('성별분류/GenderClassification.ipynb')  
**nltk** 는 파이썬으로 작성한 자연어 처리 도구 모음으로 텍스트에서 단어 빈도, 어휘 다양도 같은 정보를 쉽게 찾을 수 있다. 
이미 알려진 사실인 **여성은 a,e,i로 끝나고 남성은 k,o,r,s,t 끝날 가능성이 크다** 라는 사실을 이용하여 분류를 진행한다.  
나이브 베이즈 분류(Naive Bayes Classification)은 주로 텍스트 분류에 사용된다. 대표적으로 스팸 메일을 필터링하는 데 사용되고 있다.
그 예로 이메일에 들어 있는 단어들 w1,...,wn 이용해 스팸일 확률을 측정한다. 학습 데이터에 없는 단어가 나와도 smoothing 기법을 통해 분류가 가능하다.(빈도 + 1)
또한 log를 이용하여 구분이 어려운 작은 값도 분류가 가능하다.  
분류 결과 0.7 이상의 정확도를 보이고 임의로 가져온 name_test도 0.76 이상의 정확도를 보인다. 마지막 알파벳으로 성별 구분은 약 70% 정확도를 보인다고 할 수 있다.

<h6> 참고자료 : https://anpigon.github.io/blog/busy/@anpigon/3/


### [KoNLPy01]('KoNLPy01.ipynb')  
**KoNLPy** 는 오픈소스 소프트웨어이다. 한국어 텍스트를 이용하여 기초적인 NLP 작업을 수행하는데 사용된다. 교착어는 실질 형태소인 어근에 형식 형태소인 접사가 결합되어 문장 내에서 단어를 파생시키거나 문법적 관계를 나타내는 특징을 가진다. 한국어는 교착어 이므로 문법요소와 의미요소의 단어를 구분해야한다.  
KoNLPy에는 품사 태깅 패키지를 제공한다. **Kkma, Komoran, Hannanum, Okt**를 이용하여 형태소 분석을 진행해보자.

<h6> 참고자료 : https://konlpy-ko.readthedocs.io/ko/latest/morph/ https://mr-doosun.tistory.com/22?category=731142
