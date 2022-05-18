### elasticsearch.yml

#### Elasticsearch 를 구성 하기 위한 기본 설정

- cluster.name, node.name 은 클러스터와 노드를 잘 운영하기 위해 반드시 설정
- 설정 하지 않을 경우 cluster.name 은 "elasticsearch"로 지정이 되고 node.name 은 hostname 으로 설정됨

- cluster.name : 모든 노드와 클러스터 이름이 공유 되었을 때 연결 가능
- node.name : 노드의 용도와 목적을 이해하기 위한 사람이 읽을 수 있는 식별자로 작성

각 노드의 역할이 있음 node 의 roles

node.roles 로 설정한다.

- master(m): 클러스터의 상태를 변경, 상태 전파, 전역상태
- data(d): 문서의 색인 및 저장, 검색, 분석 (핵심 일꾼)
- data_content(s): 색인과 검색 요청이 많은 경우
- data_hot(h): 색인에 대한 요청이 많으며 자주 검색 요청을 하게 되는 경우 (time series 데이터), logs, metrics
- data_warm(w): time series 데이터를 유지 하고 있는 노드로 업데이트가 거의 없으며 드물게 요청 하는 경우
- data_cold(c): time series 데이터를 유지 하고 있는 노드로 업데이트가 되지 않고 거의 요청을 하지 않는 데이터 보유
- data_frozen(f): time series 데이터로 요청도 업데이트도 없는 경우
- ingest(i) : 색인 하기 전에 전처리하는 노드 (master 와 data 같이 사용하지 말것 부하 때문에)
- ml(l)(머신러닝): xpack 에서 제공하는 머신러닝 기능
- remote_cluster_client(r): 원격으로 구성된 cluster 에 연결 하여 원격 client 노드 역할을 수행
- transform(t): 색인된 데이터로 부터 데이터에 대한 pivot 이나 latest 정보를 별도 데이터로 변환해서 transform index 로 저장
    - 예를들어 일간 데이터를 재분석 해서 위클리로 저장
- voting_only(v): 마스터 노드를 선출 하기 위한 전용 노드
    - **master 노드 여야 voting_only 노드가 될 수 있음** (마스터 선출하는데 사용하지만 선출은 되지 않음)
    - node.roles: [master, voting_only]

coordinating node (node.roles: []) 아무런 노드 설정하지 않을 경우 주어지는 역할
이 coordinating node 는 주로 search request 용도로 사용하거나 bulk indexing request 용도로 사용 합니다.

역할별로 data tier 개념인 느낌 tier 별로 hardware 스펙을 동일하게 하라는 의미

이러한 역할 정의는 shard allocation awareness 에서 사용됨

```
index.routing,allocation.include._tier
_tier
Match nodes by the node's data tier role

```

ES 에서 잦은 문제

- disk full 로 인한 오류

공간이 꽉차기 전에 워터 마크 오류를 먼저 띄움
90 프로 까지만 색인이 되기 떄문에 색인이 안되면 disk 의심

path.data 는 다중으로 설정 가능

```
path: 
  data:
    ~/mnt/es_1
    ~/mnt/es_2
    ~/mnt/es_3
```

### Cluster 구성시 네트워크 상의 노드들에 노출 시키기 위한 설정

- network.host 설정
    - 인스턴스에 부여된 IP 주소를 작성

- Docker 로 클러스터 구성시 network.publish_host 설정
    - Single node 구성시 : network.host: "0.0.0.0" 으로 구성

### Cluster 환경 구성 시 묶어야 하는 노드들을 발견 하기 위한 설정

discovery.type

- cluster.initial_master_nodes 와 함꼐 사용 X
- 이 설정이 등록 되어 있으면 single-node 라는 값으로 지정이 되고 단일 노드 구성이 이루어짐

discovery.seed_hosts

- Clustering 을 위한 노드 목록 작성
- 이전 unicast 설정과 유사



