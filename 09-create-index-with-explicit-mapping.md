
# create index with explicit mapping

GUIDES

<https://www.elastic.co/docs/manage-data/data-store/mapping>

<https://www.elastic.co/docs/manage-data/data-store/mapping/dynamic-mapping>

<https://www.elastic.co/docs/manage-data/data-store/mapping/explicit-mapping>

<https://www.elastic.co/docs/reference/elasticsearch/mapping-reference>

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-create>

## create

Request

```SHELL

curl -k --request PUT 'https://localhost:9200/my_index_with_explicit_mapping' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
    "mappings": {
        "properties": {
            "book_price":    { "type": "float" },
            "contact_email":  { "type": "keyword"  },
            "book_name":   { "type": "text"  },
            "book_publish_date":   { "type": "date"  },
            "book_is_available":   { "type": "boolean"  }
        }
    },
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
    "index": "my_index_with_explicit_mapping"
}
```

## get index info

Request

```SHELL

curl -k --request GET 'https://localhost:9200/my_index_with_explicit_mapping' \
--header 'Authorization: ApiKey Tnk4eXY1WUJ0UFFpZ3FpcW9XX3U6eFludzd2VENrOUtnV1VvMXZWNFhYdw=='

```

Response

```JSON

{
    "my_index_with_explicit_mapping": {
        "aliases": {},
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
        },
        "settings": {
            "index": {
                "routing": {
                    "allocation": {
                        "include": {
                            "_tier_preference": "data_content"
                        }
                    }
                },
                "number_of_shards": "3",
                "provided_name": "my_index_with_explicit_mapping",
                "creation_date": "1746965521501",
                "number_of_replicas": "2",
                "uuid": "DmrYXEaNQtana0MNqQYeGw",
                "version": {
                    "created": "9009000"
                }
            }
        }
    }
}

```
