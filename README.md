# curl2log

Measure a downloadwith curl and print statistics in JSON.

## help

```
Measure download with curl
syntax: curl2log URL [URL [...]]

        URL  Download location
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
    "url_effective": "http://google.de/" 
    }, 
  "type": "curl2log" 
}
```

## Usage with Elasticsearch

Install dynamic template _curl2log.json_ into Elasticsearch (https://www.elastic.co/guide/en/elasticsearch/reference/current/dynamic-templates.html) and put data into _curl2log_-Index.
