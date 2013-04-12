# check-es-tree

This is a simple check script for the monitoring tools Bloonix or Nagios.

As example you want to check the following tree until "name":"test1000":

    {
        "hits" : {
            "total" : 168506,
            "max_score" : 1.0,
            "hits" : [ {
                "_index" : "myindex",
                "_type" : "mytype",
                "_id" : "1",
                "_score" : 1.0, "_source" : {"name":"test1000"}
            }]
        }
    }

    check-es-tree -H 192.168.10.100:9200 \
        -p myindex/_search \
        -r 'hits.hits.0._source.name=test\d+'

