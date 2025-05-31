# CURL command 
```
curl -k -u "elastic:h34z3Ti8BA2M1Bh47Hf8pq8A" -X PUT "https://localhost:30920/_ilm/policy/waf-policy" \
  -H "Content-Type: application/json" \
  -d '{
    "policy": {
      "phases": {
        "hot": {
          "actions": {
            "rollover": {
              "max_age": "5m",
              "max_size": "10kb"
            }
          }
        },
        "delete": {
          "min_age": "1h",
          "actions": {
            "delete": {}
          }
        }
      }
    }
  }'
```
  
# Kibana dev tool
```
PUT _ilm/policy/waf-policy
{
  "policy": {
    "phases": {
      "hot": {
        "actions": {
          "rollover": {
            "max_age": "5m",
            "max_size": "10kb"
          }
        }
      },
      "delete": {
        "min_age": "1h",
        "actions": {
          "delete": {}
        }
      }
    }
  }
}
```

```
PUT _index_template/waf-logs-template
{
  "index_patterns": ["waf-logs-*"],
  "template": {
    "settings": {
      "number_of_shards": 2,
      "number_of_replicas": 1,
      "index.lifecycle.name": "waf-policy",
      "index.lifecycle.rollover_alias": "waf-logs"
    }
  }
}

PUT waf-logs-000001
{
  "aliases": {
    "waf-logs": {
      "is_write_index": true
    }
  }
}
```
