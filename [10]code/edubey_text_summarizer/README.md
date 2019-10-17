# Folder Description
------

[edubey/text_summarizer 깃헙](https://github.com/edubey/text-summarizer)을 참고하여 test 하기 위한 폴더입니다. 

해당 알고리즘의 설명은 다음의 [Medium 자료](https://towardsdatascience.com/understand-text-summarization-and-create-your-own-summarizer-in-python-b26a9f09fc70
)를 참고하여 작성, 수정했습니다.


## 모델 특징
----------

#### 1. Single Document & Extractive Method
 
    한 문서내에서 등장하는 문자으들을 대상으로 문장 유사도를 측정한다. 
    
    다른 문장들과 유사도가 높은 상위 N개의 문장을 추출(Extract)해서 문서를 대표하는 문장으로 제시한다.


#### 2.TextRank algorithm

   Graph-based ranking algorithm for NLP. Extractive Summarization의 대표적인 모델. 
   

> <b>특징</b>
    
 - <b> unsupervised learning 접근 방식</b>

    별도의 training data가 필요하지 않고,  target text를 바로 적용 가능하다. 
    
    single document의 문장들의 matrix를 구성해서 각 문장안에 들어가는 단어들을 이용한 vector를 형성한다. 
    
    핵심 문장을 선택하기 위해서는 문장 간 유사도를 기반으로 sentence similarity graph를 만듦.
    
    그 뒤 각각 그래프에 PageRank를 학습해서 각 마디 (단어 혹은 문장)의 랭킹을 계산.
    
    전체 문장에 대해서 다른 문장들과 유사도가 가장 높은 문장을 사용자 지정 Top-N개 선정하여 요약 결과로 제시한다.
    
    
  
- <b>문장 유사도 측정 방식 (cosine similarity)</b>

    두 개의 non-zero vector들 간의 내적 공간에 대해서 cosine 각도를 계산해서 유사도를 측정하는 방식

    참조 : [cosine similarity wiki]( https://ko.wikipedia.org/wiki/%EC%BD%94%EC%82%AC%EC%9D%B8_%EC%9C%A0%EC%82%AC%EB%8F%84 )

    
    
    

## Code Flow
----------------

> <b> Input article → split into sentences → remove stop words → build a similarity matrix → generate rank based on matrix → pick top N sentences for summary.</b>
