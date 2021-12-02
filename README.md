Open Kibana DevConsole http://localhost:5602/app/dev_tools#/console

## Create index ##
```
PUT autocomplete
{
  "mappings": {
    "properties": {
      "message": {
        "type": "completion"
      }
    }
  }
}
```

## Start reindex english vocabulary ##
```
POST _reindex
{
  "source": {
    "index": "english_words"
  },
  "dest": {
    "index": "autocomplete"
  }
}
```

## Start search words by key "machematikal" (2 mistakes were made) ##
```
GET autocomplete/_search?pretty
{
  "suggest": {
    "word-suggest": {
      "prefix": "machematikal",
      "completion": {
        "field": "message",
        "fuzzy": {
          "fuzziness": 3,
          "min_length": 7
        }
      }
    }
  },
  "fields": [
    "message",         
    {
      "field": "@timestamp",
      "format": "epoch_millis" 
    }
  ],
  "_source": false
}
```

## Response ##
```
{
  "took" : 2,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 0,
      "relation" : "eq"
    },
    "max_score" : null,
    "hits" : [ ]
  },
  "suggest" : {
    "word-suggest" : [
      {
        "text" : "machematikal",
        "offset" : 0,
        "length" : 12,
        "options" : [
          {
            "text" : "mathematical",
            "_index" : "autocomplete",
            "_type" : "_doc",
            "_id" : "v8U4eX0BcFJFXqBQ6UoM",
            "_score" : 2.0,
            "fields" : {
              "@timestamp" : [
                "1638416311961"
              ],
              "message" : [
                "mathematical"
              ]
            }
          },
          {
            "text" : "mathematically",
            "_index" : "autocomplete",
            "_type" : "_doc",
            "_id" : "wMU4eX0BcFJFXqBQ6UoM",
            "_score" : 2.0,
            "fields" : {
              "@timestamp" : [
                "1638416311961"
              ],
              "message" : [
                "mathematically"
              ]
            }
          },
          {
            "text" : "mathematicals",
            "_index" : "autocomplete",
            "_type" : "_doc",
            "_id" : "wcU4eX0BcFJFXqBQ6UoM",
            "_score" : 2.0,
            "fields" : {
              "@timestamp" : [
                "1638416311961"
              ],
              "message" : [
                "mathematicals"
              ]
            }
          }
        ]
      }
    ]
  }
}
```

## Start search words by key "autocompletess" (3 mistakes were made) ##
```
GET autocomplete/_search?pretty
{
  "suggest": {
    "word-suggest": {
      "prefix": "autocompletess",
      "completion": {
        "field": "message",
        "fuzzy": {
          "fuzziness": 3,
          "min_length": 7
        }
      }
    }
  },
  "fields": [
    "message",         
    {
      "field": "@timestamp",
      "format": "epoch_millis" 
    }
  ],
  "_source": false
}
```
## Response ##
```
{
  "took" : 2,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 0,
      "relation" : "eq"
    },
    "max_score" : null,
    "hits" : [ ]
  },
  "suggest" : {
    "word-suggest" : [
      {
        "text" : "autocompletess",
        "offset" : 0,
        "length" : 14,
        "options" : [
          {
            "text" : "autocomplexes",
            "_index" : "autocomplete",
            "_type" : "_doc",
            "_id" : "u8I4eX0BcFJFXqBQWuTH",
            "_score" : 10.0,
            "fields" : {
              "@timestamp" : [
                "1638416275241"
              ],
              "message" : [
                "autocomplexes"
              ]
            }
          }
        ]
      }
    ]
  }
}
```

## Start search words by key "machem" (1 mistakes were made and less than 7 characters) ##
```
GET autocomplete/_search?pretty
{
  "suggest": {
    "word-suggest": {
      "prefix": "machem",
      "completion": {
        "field": "message",
        "fuzzy": {
          "fuzziness": 3,
          "min_length": 7
        }
      }
    }
  },
  "fields": [
    "message",         
    {
      "field": "@timestamp",
      "format": "epoch_millis" 
    }
  ],
  "_source": false
}
```

## Response ##
```
{
  "took" : 0,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 0,
      "relation" : "eq"
    },
    "max_score" : null,
    "hits" : [ ]
  },
  "suggest" : {
    "word-suggest" : [
      {
        "text" : "machem",
        "offset" : 0,
        "length" : 6,
        "options" : [ ]
      }
    ]
  }
}
```
