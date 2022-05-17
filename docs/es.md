### elasticsearch

- Lucene 이라는 검색 라이브러리를 기반으로 만들어진 검색 엔진
- Elastic Stack: Elasticsearch 를 중심으로 한 다양한 Stack, Logstash, Kibana, Beats
- 자체 질의문: Queryds, KQL 이 있음

#### DBMS 와 비슷한 개념

| DBMS                 | Elasticsearch                |
|----------------------|------------------------------|
| DBMS HA 구성           | Cluster                      |
| DBMS Instance        | Node                         |
| Table                | Index                        |
| Partition            | Shard / Routing              |
| Row                  | Document                     |
| Column               | Field                        |
| Row of columnar data | Serialized JSON document     |
| Join                 | Nested or Parent / Child     |
| SQL (DML)            | QueryDSL                     |
| Index                | _Analyzed                    |
| Primary Key          | _id                          |
| Configuration        | elasticsearch.yml & Settings |
| Schema               | Mappings                     |

### Elasticsearch 구성방법

- Single Node
- Cluster

### ES docker single node 설치

```
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.15.0
docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" --name elasticsearch7 docker.elastic.co/elasticsearch/elasticsearch:7.15.0
```

### Elasticsearch 설정확인

```
docker exec -i -t elasticsearch7 cat /usr/share/elasticsearch/config/elasticsearch.yml
```

### elasticsearch.yml 설정 템플릿

```
cluster.name:
node.name:
node.roles:
node.attr.size:
bootstrap.memory_lock: true
path.data:
path.logs:

discovery.seed_hosts:
discovery.type: 
cluster.initial_master_nodes:
cluster.routing.allocation.awareness.attributes: size

network.host:
http.port:
http.compression: true
http.compression_level: 3
http.cors.enabled: false
http.cors.allow-origin: /https?:\/\/127\.0\.0\.1(:[0-9]+)?/
transport.port:
transport.compress: false

gateway.expected_data_nodes:
gateway.recover_after_data_nodes:
action.auto_create_index: true
action.destructive_requires_name: true
xpack.security.enabled: false
xpack.monitoring.enabled: false
xpack.ml.enabled: false
```

