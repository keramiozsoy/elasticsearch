# get document

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-get>

UI

<http://localhost:5601/app/management/data/index_management>

## get document with id

Find id=1 the document

Request

```SHELL
curl -k --request GET 'https://localhost:9200/my_index/_doc/1' \
--header 'Authorization: ApiKey S0dVNXZKWUJwWFFabkhSWVREd0k6RU1KVExIZkxwY2JvS1RDMnFaa0RBdw=='
```

Response

```JSON
{
    "_index": "my_index",
    "_id": "1",
    "_version": 1,
    "_seq_no": 0,
    "_primary_term": 1,
    "found": true,
    "_source": {
        "title": "Document with ID 1",
        "content": "This one has a manually set ID."
    }
}
```