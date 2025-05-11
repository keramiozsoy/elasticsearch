# query documents of index

GUIDE

<https://www.elastic.co/docs/reference/query-languages/query-dsl/query-dsl-match-all-query>

API

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-search-2>


I would like to see all documents under the index.

Request

```SHELL

curl -k --request GET 'https://localhost:9200/my_index/_search' \
--header 'Authorization: ApiKey YOUR_API_KEY' \
--header 'Content-Type: application/json' \
--data '{
  "query": {
    "match_all": {}
  }
}'
```

Response

```JSON
{
    "took": 10,
    "timed_out": false,
    "_shards": {
        "total": 3,
        "successful": 3,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": {
            "value": 2,
            "relation": "eq"
        },
        "max_score": 1.0,
        "hits": [
            {
                "_index": "my_index",
                "_id": "Oi9Zv5YBtPQigqiqRm9G",
                "_score": 1.0,
                "_source": {
                    "title": "Document with random id",
                    "content": "Document random content"
                }
            },
            {
                "_index": "my_index",
                "_id": "1",
                "_score": 1.0,
                "_source": {
                    "title": "Document with ID 1",
                    "content": "This one has a manually set ID."
                }
            }
        ]
    }
}
```

Information about the response

## Top-Level Fields

took: 10
Time in milliseconds that Elasticsearch took to process the request (not including network time).

timed_out: false
Indicates whether the query timed out. false means it completed in time.

## _shards

Information about how the query was distributed across the shards of the index.
total: 3
Number of shards the query was executed on (your index is spread over 3 shards).

successful: 3
All 3 shards responded successfully.

skipped: 0
No shards were skipped.

failed: 0
No shard queries failed.

## hits

This section contains the search results.

value: 2
Total number of documents matching your query (in this case, 2).

relation: "eq"
"eq" means the value is an exact count. If it were "gte" (greater than or equal), it would mean “at least X hits” (usually when you request a partial count).

max_score: 1.0
The highest score among all matched documents (used for ranking relevance in full-text search)
