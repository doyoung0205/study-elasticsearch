# study-elasticsearch


#### elasticsearch 에게 Lucene 이란

오픈소스 기반의 검색 라이브러리

https://Lucene.apache.org

Lucene - es 와 동일함
- 인덱스 
- 문서 
- 필드 (용어의 집함)
- 용어 


(index writer -> document writer -> segment merger)
(diretory -> index writer -> analyzer -> documents -> fields)

역색인 파일 (Inverted Index Structure)

= 용어에 대해서 문서를 나열하는 구조


용어가 얼마나 자주 나오는지 용어에 대한 문서
Text 를 분섭함. es + arirang + kibana or postman _ analyze 

[arirang analyzer plugin for elasticsearch.](https://github.com/HowookJeong/elasticsearch-analysis-arirang/tree/7.17.0)


[Index File Format](https://lucene.apache.org/core/9_1_0/core/org/apache/lucene/codecs/lucene91/package-summary.html#package.description)


index writer 는 index file 들을 생성
- index file 은 수정이 불가능함
- 항상 색인할 때 신규로 생성

indexwriter -> create segment File -> document writing -> commit
indexwriter -> create segment File -> document writing -> commit
indexwriter -> create segment File -> document writing -> commit


-> segment Merger -> merge Completed -> deleted ord segment File



index Search 

indexSerach 는  index reader 이용해서 검색 수행을 함.

하나의 index 에는 Segment 별로 N 개의 LeafReader 가 존재한다.

query -> index searcher -> index reader -> leaf reader context: leaf reader

--

형태소 분석
- 입력 받은 문자열에서 검색 가능한 정보 구조로 분석 및 분해 하는 과정

Analyzer 
- Tokenizer
- charFilter

input text -> char filter -> filterd text -> tokenizer -> tokens -> tokenfilter -> filtered Tokens -> output tokens

token filter 는 순서가 중요하다 (대소문자, 동의어 관련)


문자열 분석하면 offsets 정보와 posistion 가 나옴


- 루씬을 이용해서 검색 Application 이나 검색 Engine 을 만들 수 있다.
- 루씬을 이용해서 다양한 Text 분석 Applicaiton 을 만들 수 있습니다.
- index, segments 파일은 불변 
- 루씬의 핵심 클래스는 IndexWriter, IndexSearcher(indexReader), Analyzer 이다.



