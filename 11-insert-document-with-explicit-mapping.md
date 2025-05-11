# insert document with explicit mapping

# get index mappping

Request 

```SHELL
curl -k --request GET 'https://localhost:9200/my_index_with_explicit_mapping/_mapping' \
--header 'Authorization: ApiKey YOUR_API_KEY'
```

Response 

```JSON
{
    "my_index_with_explicit_mapping": {
        "mappings": {
            "properties": {
                "book_is_available": {
                    "type": "boolean"
                },
                "book_name": {
                    "type": "text"
                },
                "book_price": {
                    "type": "float"
                },
                "book_publish_date": {
                    "type": "date"
                },
                "contact_email": {
                    "type": "keyword"
                }
            }
        }
    }
}
```

# insert document with expilicit mapping

Request

```SHELL
curl -k --request PUT 'https://localhost:9200/my_index_with_explicit_mapping/_doc/1' \
--header 'Authorization: ApiKey Tnk4eXY1WUJ0UFFpZ3FpcW9XX3U6eFludzd2VENrOUtnV1VvMXZWNFhYdw==' \
--header 'Content-Type: application/json' \
--data '{
    "book_is_available": true,
    "book_name": "Good Book",
    "book_price": 16.99,
    "book_publish_date": "2025-01-01"
}'
```

Response

```JSON
{
    "_index": "my_index_with_explicit_mapping",
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
