# curl2log

Print a JSON formated output of curl

## help

```
Measure download with curl
syntax: curl2log <regular curl parameters like urls, headers, credentials, ...>
```

## example

Measure download statistics from google.de (JSON-Output is prettifed)

```
./curl2log http://google.de
{
  "curl": {
    "content_type": "text/html; charset=UTF-8",
    "filename_effective": "/dev/null",
    "ftp_entry_path": "",
    "http_code": "301",
    "http_connect": "000",
    "local_ip": "192.168.123.12",
    "local_port": 48008,
    "num_connects": 1,
    "num_redirects": 0,
    "redirect_url": "http://www.google.de/",
    "remote_ip": "216.58.213.3",
    "remote_port": 80,
    "size_download": 218,
    "size_header": 320,
    "size_request": 73,
    "size_upload": 0,
    "speed_download": 1481.000,
    "speed_upload": 0.000,
    "ssl_verify_result": 0,
    "time_appconnect": 0.000,
    "time_connect": 0.102,
    "time_namelookup": 0.061,
    "time_pretransfer": 0.102,
    "time_redirect": 0.000,
    "time_starttransfer": 0.147,
    "time_total": 0.147,
    "url_effective": "http://google.de/",
    "timestamp": "2021-06-05T20:48:54+02:00"
  }, 
  "type": "curl2log" 
}
```

## Usage with Elasticsearch

The mapping for the index is in _curl2log.json_. For further details see [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/explicit-mapping.html).

Example for creating an index *my-index*:
```
curl -XPUT http://elasticsearch:9200/my-index -d @curl2log.json
```
