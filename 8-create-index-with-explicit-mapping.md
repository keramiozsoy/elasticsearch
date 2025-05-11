
# create index with explicit mapping

GUIDES

<https://www.elastic.co/docs/manage-data/data-store/mapping>

<https://www.elastic.co/docs/manage-data/data-store/mapping/dynamic-mapping>

<https://www.elastic.co/docs/manage-data/data-store/mapping/explicit-mapping>

<https://www.elastic.co/docs/reference/elasticsearch/mapping-reference>

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-create>


```SHELL

curl -k --request PUT 'https://localhost:9200/my_index_with_explicit_mapping' \
--header 'Authorization: ApiKey Tnk4eXY1WUJ0UFFpZ3FpcW9XX3U6eFludzd2VENrOUtnV1VvMXZWNFhYdw==' \
--header 'Content-Type: application/json' \
--data '{
    "mappings": {
        "properties": {
            "age":    { "type": "integer" },
            "email":  { "type": "keyword"  },
            "name":   { "type": "text"  }
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



## Get Index Info


```SHELL

curl -k --request GET 'https://localhost:9200/my_index_with_explicit_mapping' \
--header 'Authorization: ApiKey Tnk4eXY1WUJ0UFFpZ3FpcW9XX3U6eFludzd2VENrOUtnV1VvMXZWNFhYdw=='

```

```JSON
{
    "my_index_with_explicit_mapping": {
        "aliases": {},
        "mappings": {
            "properties": {
                "age": {
                    "type": "integer"
                },
                "email": {
                    "type": "keyword"
                },
                "name": {
                    "type": "text"
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
                "creation_date": "1746964522597",
                "number_of_replicas": "2",
                "uuid": "JYArE63KQYeATaqp3HKUdA",
                "version": {
                    "created": "9009000"
                }
            }
        }
    }
}

```

