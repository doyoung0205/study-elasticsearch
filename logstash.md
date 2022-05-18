### Logstash

- 다양한 소스 데이터를 가공해서 Elasticsearch 로 적재하는 도구
- 다양한 input, Filter, Output 의 Pipeline 구조를 가짐
    - 이벤트 데이터에 대한 스트림을 필터할 수 있는 다양한 Codec(json, csv) 사용 가능
- Logstash는 자원을 무겁게 사용하기 때문에 Agent로 사용하기보다 데이터를 받아 정제/가공 후 적재하는 Ingestor 역할로 활용하는 게 좋음
