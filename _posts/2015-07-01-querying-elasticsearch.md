---
title: "ElasticSearch: Querying"
layout: post
category: usage
permalink: /usage/elasticsearch_querying.html
---

ElasticSearch currently supports only simple Lucene style queries (like Kibana
but without the aggregation).

Full blown JSON based ElasticSearch queries (including aggregations) will be
added later.

## Simple query example:

- Query the index named "twitter"
- Filter by "user:kimchy"
- Return the fields: "@timestamp", "tweet" and "user"
- Return up to 15 results
- Sort by @timestamp ascending

```json
{
    "index" : "twitter",
    "query" : "user:kimchy",
    "fields" : ["@timestamp", "tweet", "user"],
    "size" : 15,
    "sort" : "@timestamp:asc"
}
```

## Simple query on a logstash ElasticSearch instance:

- Query the index named "logstash-2015.04.*" (in this case its all of April 2015)
- Filter by type:events AND eventName:UserUpgrade AND channel:selfserve
- Return fields: "@timestamp", "userId", "channel", "utm_source", "utm_medium", "utm_campaign", "utm_content"
- Return up to 250 results
- Sort by @timestamp ascending

```json
{
    "index" : "logstash-2015.04.*",
    "query" : "type:events AND eventName:UserUpgrade AND channel:selfserve",
    "fields" : ["@timestamp", "userId", "channel", "utm_source", "utm_medium", "utm_campaign", "utm_content"],
    "size" : 250,
    "sort" : "@timestamp:asc"
}
```