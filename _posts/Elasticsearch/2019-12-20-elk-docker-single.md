---
title: "docker-compose 로 Elastic Cliuster 구성"
categories:
  - Elasticsearch
tags:
  - es
  - Docker
  - Compose
---

도커가 설치되어 있다는 전제하에 설명하겠습니다.

## 이미지 받기
docker pull 으로 엘라스틱서치 이미지를 받아준다.

```
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.5.1
```

## 도커로 싱클노드 클러스터 실행하기
9200 포트와 9300 포트를 각각 바인딩 해주고 설정을 single-node로 변경하고 받은 이미지를 실행한다.
```
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.5.1
```

## 도커 컴포즈로 멀티노드 클러스터 실행하기
*docker-compose.yml* 파일을 작성해준다.
```
version: '2.2'
services:
  es01:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.5.1
    container_name: es01
    environment:
      - node.name=es01  # 노드이름
      - cluster.name=es-docker-cluster # 클러스터이름
      - discovery.seed_hosts=es02,es03 # 호스트 탐색범위
      - cluster.initial_master_nodes=es01,es02,es03 # 초기 마스터노드
      - bootstrap.memory_lock=true # 메모리 스왑을 하지 않음
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m" # 메모리 설정
    # ES는 파일디스크립터와 핸들러를 사용하기 때문에 제한 해제가 필요
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data01:/usr/share/elasticsearch/data # 볼륨 마운트
    ports:
      - 9200:9200 # 포트 정보
    networks:
      - elastic # 네트워크 설정
  es02:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.5.1
    container_name: es02
    environment:
      - node.name=es02
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es03
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data02:/usr/share/elasticsearch/data
    networks:
      - elastic
  es03:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.5.1
    container_name: es03
    environment:
      - node.name=es03
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es02
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data03:/usr/share/elasticsearch/data
    networks:
      - elastic

volumes:
  data01:
    driver: local
  data02:
    driver: local
  data03:
    driver: local

networks:
  elastic:
    driver: bridge
```

도커 컴포즈 파일이 있는 곳에서 다음과 같이 실행한다. 도커엔진은 메모리 4G이상을 필요로 하니 스펙을 확인하고 실행하자.
```
docker-compose up
```
-d 옵션을 주어 (detached mode) 흔히 말하는 백그라운드 모드로 실행시킬 수 있다.
```
docker-compose up -d
```

실행이 잘 되었는지 아래 명령어로 확인하자
```
curl -X GET "localhost:9200/_cat/nodes?v&pretty"
```

혹은 로그를 살펴보자
```
docker logs [container name]
```


public docs : https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html  
Disable swapping:https://www.elastic.co/guide/en/elasticsearch/reference/master/setup-configuration-memory.html  
Setting the heap size:https://www.elastic.co/guide/en/elasticsearch/reference/master/heap-size.html  
File Descriptors:https://www.elastic.co/guide/en/elasticsearch/reference/master/file-descriptors.html  
