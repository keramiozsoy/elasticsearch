# create an index

GUIDES

<https://www.elastic.co/docs/reference/elasticsearch/index-settings/index-modules#index-number-of-shards>

<https://www.elastic.co/docs/reference/elasticsearch/index-settings/index-modules#index-number-of-shards>

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-create>

UI

<http://localhost:5601/app/management/data/index_management/indices>

An index seems like a table on database.

An index is collection of documents that share similar characteristics.

To read more about the create index API, visit the docs.

## Shards

Elasticsearch divides the data in an index into multiple shards. Each shard is a self-contained index that Elasticsearch can distribute across multiple nodes in a cluster. Shards are managed automatically but configured when creating the index.

number_of_shards  ->  how many pieces the data is split into

## Replicas

For fault tolerance and high availability, an index can have replica shards, which are copies of the primary shards.

number_of_replicas -> how many copies of the data, if one data is loss, system can continue to response. It provides resiliance and durability

Let's create index named "my_index"

Request

```SHELL
curl -k --request PUT 'https://localhost:9200/my_index' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
    "settings": {
        "number_of_shards": 3,
        "number_of_replicas": 2
    }
}'
```

Response

```JSON
{
    "acknowledged": true,
    "shards_acknowledged": true,
    "index": "my_index"
}
```



## delete index

Request

```SHELL

curl -k --request DELETE 'https://localhost:9200/my_index' \
--header 'Authorization: ApiKey YOUR_API_KEY'

```

Response 

```JSON

{"acknowledged":true}

```
