# object field type

Doc

<https://www.elastic.co/docs/reference/elasticsearch/mapping-reference/object>

<https://www.elastic.co/docs/reference/elasticsearch/rest-apis/retrieve-selected-fields#source-filtering>

<https://www.elastic.co/docs/reference/elasticsearch/mapping-reference/mapping-source-field>

In Elasticsearch, dot notation is used to represent hierarchical relationships.

Request

```SHELL
curl -k --request POST 'https://localhost:9200/my_index_object_field_type/_doc' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
  "region": "US",
  "manager": {
    "age":     30,
    "name": {
      "first": "John",
      "last":  "Smith"
    }
  }
}'
```

Response

```JSON
{
    "_index": "my_index_object_field_type",
    "_id": "VfdWxZYBGrKd7xr1PMat",
    "_version": 1,
    "result": "created",
    "_shards": {
        "total": 2,
        "successful": 2,
        "failed": 0
    },
    "_seq_no": 0,
    "_primary_term": 1
}
```

Elasticsearch stores and refers to these fields using dot notation.

This keeps the structure simple and flat which makes it easier to search and find things.

```JSON
{
  "region":             "US",
  "manager.age":        30,
  "manager.name.first": "John",
  "manager.name.last":  "Smith"
}

```

Let's query first name and age.

Request

```SHELL

curl -k --request GET 'https://localhost:9200/my_index_object_field_type/_search' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
  "_source": ["manager.age", "manager.name.first"],
  "query": {
    "match_all": {}
  }
}'

```


Response

```JSON

{
    "took": 4,
    "timed_out": false,
    "_shards": {
        "total": 1,
        "successful": 1,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": {
            "value": 1,
            "relation": "eq"
        },
        "max_score": 1.0,
        "hits": [
            {
                "_index": "my_index_object_field_type",
                "_id": "WPezxZYBGrKd7xr1acb4",
                "_score": 1.0,
                "_source": {
                    "manager": {
                        "age": 30,
                        "name": {
                            "first": "John"
                        }
                    }
                }
            }
        ]
    }
}