# installation

<https://www.elastic.co/docs/deploy-manage/deploy/self-managed/install-elasticsearch-docker-compose>

## Docker Compose Files

create a folder and put files below

```SHELL

mkdir elk

```

<https://github.com/elastic/elasticsearch/blob/main/docs/reference/setup/install/docker/docker-compose.yml>

<https://github.com/elastic/elasticsearch/blob/main/docs/reference/setup/install/docker/.env>

## Updates on files


### .env

ELASTIC_PASSWORD=123456

KIBANA_PASSWORD=123456

STACK_VERSION=9.0.0

## start stop

```SHELL
docker-compose up -d  # start
```

```SHELL
docker-compose down  # temporary-down
```

```SHELL
docker-compose down -v  # To delete the network, containers, and volumes when you stop the cluster
```

## check endpoints

<http://localhost:5601> (Kibana)
<http://localhost:9200> (Elasticsearch)

Request

```SHELL
curl -k -u elastic:123456 https://localhost:9200
```

Reponse

```JSON
{
  "name" : "es01",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "kkJTf9fqR2Ska_jRYbGvTQ",
  "version" : {
    "number" : "9.0.0",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "112859b85d50de2a7e63f73c8fc70b99eea24291",
    "build_date" : "2025-04-08T15:13:46.049795831Z",
    "build_snapshot" : false,
    "lucene_version" : "10.1.0",
    "minimum_wire_compatibility_version" : "8.18.0",
    "minimum_index_compatibility_version" : "8.0.0"
  },
  "tagline" : "You Know, for Search"
}
```