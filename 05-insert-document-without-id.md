# insert document without id

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-create>

DOC

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-create>

Let's create a document without id on "my_index"

Request

```SHELL
curl -k --request POST 'https://localhost:9200/my_index/_doc' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
    "title": "Document with random id",
    "content": "Document random content"
}'
```

Response

```JSON
{
    "_index": "my_index",
    "_id": "Oi9Zv5YBtPQigqiqRm9G",
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 3,
        "successful": 3,
        "failed": 0
    },
    "_seq_no": 1,
    "_primary_term": 1
}%
```