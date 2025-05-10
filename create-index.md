# Documentation

To read more about the create index API, visit the docs.

<https://www.elastic.co/docs/api/doc/elasticsearch/operation/operation-indices-create>

```
curl 
 --request PUT 'http://api.example.com/{index}' 
 --header "Authorization: $API_KEY" 
 --header "Content-Type: application/json" 
 --data '"{\n  \"settings\": {\n    \"number_of_shards\": 3,\n    \"number_of_replicas\": 2\n  }\n}"'

 ```