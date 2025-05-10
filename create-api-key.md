# create api key

<https://www.elastic.co/docs/api/doc/elasticsearch/authentication>

We would like top use ApiKey instead of username:password

You can genereate from browser or terminal.

## Browser

Open management section and generate api key

<http://localhost:5601/app/management/security/api_keys>


## Terminal

Open terminal.

Request

```SHELL
curl -k -u elastic:123456 -X POST https://localhost:9200/_security/api_key \
  -H "Content-Type: application/json" \
  -d '{
    "name": "my-api-key",
    "expiration": "1d",  // optional: expires in 1 day
    "role_descriptors": {
      "custom": {
        "cluster": ["all"],
        "index": [
          {
            "names": ["*"],
            "privileges": ["read", "write"]
          }
        ]
      }
    }
  }'

```

Response

```SHELL
{
    "id": "JGV0u5YBpXQZnHRYWDxh",
    "name": "my-api-key",
    "expiration": 1746988086389,
    "api_key": "lhqUWj2tapsIE-PUeF3x1g",
    "encoded": "SkdWMHU1WUJwWFFabkhSWVdEeGg6bGhxVVdqMnRhcHNJRS1QVWVGM3gxZw=="
}
```

We can use encoded field for ApiKey.

Request

```SHELL
curl -k --request GET 'https://localhost:9200/_health_report' --header 'Authorization: ApiKey SkdWMHU1WUJwWFFabkhSWVdEeGg6bGhxVVdqMnRhcHNJRS1QVWVGM3gxZw=='
```

Response

```JSON

{
    "status": "green",
    "cluster_name": "docker-cluster",
    "indicators": {
        "master_is_stable": {
            "status": "green",
            "symptom": "The cluster has a stable master node",
            "details": {
                "current_master": {
                    "node_id": "Yfk4ZbNES3mIUNAtiT9oRA",
                    "name": "es02"
                },
                "recent_masters": [
                    {
                        "node_id": "Yfk4ZbNES3mIUNAtiT9oRA",
                        "name": "es02"
                    }
                ]
            }
        },
        "repository_integrity": {
            "status": "green",
            "symptom": "No snapshot repositories configured."
        },
        "disk": {
            "status": "green",
            "symptom": "The cluster has enough available disk space.",
            "details": {
                "indices_with_readonly_block": 0,
                "nodes_with_enough_disk_space": 3,
                "nodes_with_unknown_disk_status": 0,
                "nodes_over_high_watermark": 0,
                "nodes_over_flood_stage_watermark": 0
            }
        },
        "shards_capacity": {
            "status": "green",
            "symptom": "The cluster has enough room to add new shards.",
            "details": {
                "data": {
                    "max_shards_in_cluster": 3000
                },
                "frozen": {
                    "max_shards_in_cluster": 9000
                }
            }
        },
        "file_settings": {
            "status": "green",
            "symptom": "No file-based setting changes have occurred"
        },
        "shards_availability": {
            "status": "green",
            "symptom": "This cluster has all shards available.",
            "details": {
                "initializing_replicas": 0,
                "creating_primaries": 0,
                "restarting_replicas": 0,
                "unassigned_primaries": 0,
                "started_replicas": 35,
                "creating_replicas": 0,
                "initializing_primaries": 0,
                "restarting_primaries": 0,
                "started_primaries": 35,
                "unassigned_replicas": 0
            }
        },
        "data_stream_lifecycle": {
            "status": "green",
            "symptom": "Data streams are executing their lifecycles without issues",
            "details": {
                "stagnating_backing_indices_count": 0,
                "total_backing_indices_in_error": 0
            }
        },
        "slm": {
            "status": "green",
            "symptom": "No Snapshot Lifecycle Management policies configured",
            "details": {
                "slm_status": "RUNNING",
                "policies": 0
            }
        },
        "ilm": {
            "status": "green",
            "symptom": "Index Lifecycle Management is running",
            "details": {
                "policies": 56,
                "stagnating_indices": 0,
                "ilm_status": "RUNNING"
            }
        }
    }
}
```
