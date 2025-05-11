# insert document

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-create>

DOC

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-create>

Let's create id = 1 document on my_index.

Request

```SHELL
curl -k --request PUT 'https://localhost:9200/my_index/_doc/1' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
    "title": "Document with ID 1",
    "content": "This one has a manually set ID."
}'
```

Response

```JSON
{
    "_index": "my_index",
    "_id": "1",
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 3,
        "successful": 3,
        "failed": 0
    },
    "_seq_no": 0,
    "_primary_term": 1
}
```
