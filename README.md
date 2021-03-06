# NLP-study
### [성별분류](성별분류/GenderClassification.ipynb)  
**nltk** 는 파이썬으로 작성한 자연어 처리 도구 모음으로 텍스트에서 단어 빈도, 어휘 다양도 같은 정보를 쉽게 찾을 수 있다. 
이미 알려진 사실인 **여성은 a,e,i로 끝나고 남성은 k,o,r,s,t 끝날 가능성이 크다** 라는 사실을 이용하여 분류를 진행한다.  
나이브 베이즈 분류(Naive Bayes Classification)은 주로 텍스트 분류에 사용된다. 대표적으로 스팸 메일을 필터링하는 데 사용되고 있다.
그 예로 이메일에 들어 있는 단어들 w1,...,wn 이용해 스팸일 확률을 측정한다. 학습 데이터에 없는 단어가 나와도 smoothing 기법을 통해 분류가 가능하다.(빈도 + 1)
또한 log를 이용하여 구분이 어려운 작은 값도 분류가 가능하다.  
분류 결과 0.7 이상의 정확도를 보이고 임의로 가져온 name_test도 0.76 이상의 정확도를 보인다. 마지막 알파벳으로 성별 구분은 약 70% 정확도를 보인다고 할 수 있다.

<h6> 참고자료 : https://anpigon.github.io/blog/busy/@anpigon/3/


### [KoNLPy01](KoNLPy01.ipynb)  
**KoNLPy** 는 오픈소스 소프트웨어이다. 한국어 텍스트를 이용하여 기초적인 NLP 작업을 수행하는데 사용된다. 교착어는 실질 형태소인 어근에 형식 형태소인 접사가 결합되어 문장 내에서 단어를 파생시키거나 문법적 관계를 나타내는 특징을 가진다. 한국어는 교착어 이므로 문법요소와 의미요소의 단어를 구분해야한다.  
KoNLPy에는 품사 태깅 패키지를 제공한다. **Kkma, Komoran, Hannanum, Okt**를 이용하여 형태소 분석을 진행해보자.

<h6> 참고자료 : https://konlpy-ko.readthedocs.io/ko/latest/morph/ https://mr-doosun.tistory.com/22?category=731142
  
  ### [KoNLPy02](KoNLPy02.ipynb)  
단어에 정수 인덱스를 부여하는 [정수 인코딩] 한국어는 토큰화에 따로 불용처 처리가 크게 필요하지 않다. 형태소 분석을 통해 분리가 가능하기 때문이다. 하지만 필요없는 명사나 형용사를 제거하고 싶을 때도 있다. 이때 직접 불용어 리스트를 정의한 후 적용이 가능하다. 인터넷, SNS가 일상속에 깊게 침투하면서 마주치게 되는 욕설, 비방 등의 언어적 폭력은 통제하기 굉장히 어렵다.  
게임을 예로 들면, 화려한 그래픽, 재밌는 스토리들은 게임이 소비자들에게 주는 첫인상이라고 생각한다. 좋은 첫인상을 가지고 게임을 플레이하는 유저들은 게임 속에서 마주치게 되는 욕설, 비방은 좋았던 첫인상을 무너지게 만드는 요소이다. 유저들의 건강한 게임 문화를 위해서는 채팅 제한, 사용자 제한은 반드시 필요한 방안이라고 생각한다.  
불용어 리스트를 이용하여 기존 탐지 모델 필터링에 도움이 될 수 있다고 생각한다. 

<h6> 참고자료 : https://mr-doosun.tistory.com/25?category=731142

  ### [KoNLPy03](KoNLPy03.ipynb)  
문장의 긍정, 부정을 예측해보자. 학습 문장을 (token,형태소,긍정/부정) 형태로 정제 후 새로운 문장의 긍정/부정 판단을 한다.  
인간의 감정은 굉장히 다양하다. 많은 감정을 모두 예측하기 전에  긍정/부정 두 가지로 표현해본다. **뉴스기사 긍정,부정 판단 프로젝트** 가장 유명하다. 고양이와 수업에 관한 소규모 데이터로 분류를 진행했다. 이후에 유명한 뉴스 제목으로 분류도 진행할 예정이다.

<h6> 참고자료 : https://pinkwink.kr/1025

  ### [BERT(Bidirectional Encoder Represetations from Transformers)]  
구글이 공개한 인공지능 언어모델 버트 공부(논문 분석 및 구현까지)  
BERT는 Transformer라는 모델에 기반한다. input Text를 받아 기본적으로 Attention 메커니즘을 통해, 인코딩, 디코딩하는 방식의 모델이다. 특이하게 Convolution, Recurrence도 사용하지 않는다. 따라서, LSTM+RNN 처럼 각 단위 워드 벡터가 시간의 연속성을 기억하고 있을 필요는 없다. 단어들의 상대적인 위치를 알아야 하기 때문에 Position encoding 단계가 추가되어 있다. 즉, 문장 내의 단어의 위치 벡터 값을 워드 임베딩 벡터에 추가해주는 거다. BERT는 Transformer 모델 중 인코더만 쓰는 형태이다. 이미 방대한 양의 Corpus(정보)를 이미 트레이닝 시킨 언어 처리 모델이다. 따라서 추가적으로 GPU, TPU를 사용하여 직접 돌릴 필요가 없다.( + 버트는 한 개 문장으로 적용부를 구성할 수 있고, 질의응답 같은 text pair로 구성할 수 있다. )  
BERT는  두 가지 unsupervised task로 학습시킨 모델로, 첫번째 태스크는 Masked LM이다. 의도적으로 입력값의 특정 퍼센트의 랜덤 단어를 왜곡하는 기법으로 **80:10:10 = mask 매스킹:다른단어 치환:그대로 두기** 구성된다. 두번째 태스크는 Next Sentence Prediction(NSP)이다. 문장과 문장 간의 관계에 대한 부분으로 학습을 할 때 대량 Courpus에서 문장들을 이어 붙여 다음에 이어지는 문장인지, 아닌지를 판단한다. 

**네이버 영화리뷰 감정분석**  
 가장 베이직한 예제인 네이버 영화리뷰 감정분석을 BERT를 사용하여 해결한다. Hugging Face의 PyTorch BERT를 사용하였으며 아래 참고자료를 정리하고 이해하여 작성하였다. BERT의 입력 형태인 [CLS], [SEP] 문장으로 바꾸어 주고 encoding 후 모델에 입력하였다. Colab의 GPU 1 로 학습하였는데 시간이 꽤 오래 걸려 중간에 학습이 멈추는 현상이 이루어졌다.....(다시 업로드 예정)
 
 
<h6> 참고자료 : https://arxiv.org/abs/1810.04805 https://paul-hyun.github.io/bert-01/ https://brunch.co.kr/@yj5wqu/23 https://moondol-ai.tistory.com/241
<h6> 참고자료(네이버 영화 리뷰) : https://colab.research.google.com/drive/1tIf0Ugdqg4qT7gcxia3tL7und64Rv1dP#scrollTo=muU2kS2GCh4y http://yonghee.io/bert_binary_classification_naver/  </h6>
  
  
  
### 개체명 인식(Named Entitiy Recognition)
NER이란 Named Entity를 Regognition하는 즉, 인식하는 작업을 말한다. 처음에는 NE는 문자열 내에서 기관명, 인물, 장소 뿐만 아니라 화페, 시간, 퍼센티지 표현까지 포괄하는 의미로 등장했다. 또한 명사라고도 정의하기도 했다.  
논문 [A Survey on Deep Learning for Named Entity Recognition](https://arxiv.org/abs/1812.09449)에서는 NER을 아래와 같이 정의한다.  
문자열 안에서 NE의 위치를 알아내고, 사전정의한 카테고리에 따라 알맞게 분류하는 작업(즉, 문자열을 입력으로 받아 단어별로 해당되는 태그를 내뱉게 하는 multi-class 분류 작업으로 성격을 정의할 수 있다.)  
단어를 분류하는 작업으로 간단하게 말할 수 있고, NE를 두 가지의 유형으로 나눠볼 수 있다. 첫 번째는 generic NEs이다. 인물이나 장소의 명칭이 해당한다. 두 번째는 domain-specific NEs이다. 단백질, 효소, 유전자 등 전문 분야의 용어가 이에 해당한다.  

 <h6> 참고자료 : https://wikidocs.net/30682 https://stellarway.tistory.com/29
  
### [잠재 의미 분석 LSA(Latent Semantic Analysis)](LSA.ipynb) 
sklearn에서 제공하는 Twenty Newsgroup 데이터를 사용하여 잠재 의미 분석을 해보자.  
사용 데이터 : 20개의 다른 주제를 가진 뉴스그룹 데이터  
기본적으로 TF-IDF는 단어의 빈도 수를 이용한 수치화 방법이기 때문에 단어의 의미를 고려하지 못한다는 단점이 있다. 이를 위한 대안으로 나온 방법은 잠재된 의미를 끌어내는 방법인 잠재 의미 분석이다.  
n개의 문서를 m개의 단어로 표현된 입력 데이터 행렬 A를 SVD한 후 사용자가 임의로 정한 k를 이용하여 dim을 조정한다. A_k 행렬을 이용하여 문장 분석 

 <h6> 참고자료 : https://bkshin.tistory.com/entry/NLP-9-%EC%BD%94%EC%82%AC%EC%9D%B8-%EC%9C%A0%EC%82%AC%EB%8F%84%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-%EC%98%81%ED%99%94-%EC%B6%94%EC%B2%9C-%EC%8B%9C%EC%8A%A4%ED%85%9C https://wikidocs.net/24949
