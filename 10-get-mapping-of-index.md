# get mapping

DOC

<https://www.elastic.co/docs/manage-data/data-store/mapping>

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-get-mapping-1>

UI

<http://localhost:5601/app/management/data/index_management/indices/index_details?indexName=my_index&tab=mappings>

DATA TYPE

<https://www.elastic.co/docs/reference/elasticsearch/mapping-reference/text>

Get data structure of "my_index"

```JSON

--data '{
    "title": "Document with ID 1",
    "content": "This one has a manually set ID."
}'

```

```SHELL
curl -k --request GET 'https://localhost:9200/my_index/_mapping' \
--header 'Authorization: ApiKey YOUR_API_KEY'
```

Response

```JSON
{
    "my_index": {
        "mappings": {
            "properties": {
                "content": {
                    "type": "text",
                    "fields": {
                        "keyword": {
                            "type": "keyword",
                            "ignore_above": 256
                        }
                    }
                },
                "title": {
                    "type": "text",
                    "fields": {
                        "keyword": {
                            "type": "keyword",
                            "ignore_above": 256
                        }
                    }
                }
            }
        }
    }
}
```
