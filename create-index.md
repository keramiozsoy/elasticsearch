# Documentation

To read more about the create index API, visit the docs.

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-create>

Let's create index named "my_index"


number_of_shards  ->  how many pieces the data is split into
number_of_replicas -> how many copies of the data
Request

```SHELL
curl -k --request PUT 'https://localhost:9200/my_index' \
--header 'Authorization: ApiKey S0dVNXZKWUJwWFFabkhSWVREd0k6RU1KVExIZkxwY2JvS1RDMnFaa0RBdw==' \
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