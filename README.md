# curl2log

Print a JSON formated output of curl

## help

```
syntax: curl2log <regular curl parameters like urls, headers, credentials, ...>
```

## example

Measure download statistics from google.de (JSON-Output is prettifed)

```
./curl2log http://google.de
{
    "timestamp": "2021-06-05T23:36:14+02:00",
    "curl": "{"url_effective":"http://google.de/","method":"GET","http_code":301,"response_code":301,"num_headers":9,"http_connect":0,"time_total":0.071452,"time_namelookup":0.001736,"time_connect":0.030073,"time_appconnect":0.000000,"time_pretransfer":0.030156,"time_starttransfer":0.071283,"size_header":308,"size_request":73,"size_download":218,"size_upload":0,"speed_download":3070,"speed_upload":0,"content_type":"text/html; charset=UTF-8","num_connects":1,"time_redirect":0.000000,"num_redirects":0,"redirect_url":"http://www.google.de/","ssl_verify_result":0,"proxy_ssl_verify_result":0,"filename_effective":"/dev/null","remote_ip":"2a00:1450:400e:80c::2003","remote_port":80,"local_ip":"::1","local_port":55792,"http_version":"1.1","scheme":"HTTP","curl_version":"libcurl/7.74.0 OpenSSL/1.1.1k zlib/1.2.11 brotli/1.0.9 libidn2/2.3.0 libpsl/0.21.0 (+libidn2/2.3.0) libssh2/1.9.0 nghttp2/1.43.0 librtmp/2.3"}
}
```

## Usage with Elasticsearch

The mapping for the index is in _curl2log.json_. For further details see [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/explicit-mapping.html).

Example for creating an index *my-index* with the mapping:
```
curl -XPUT \
  -H 'Content-Type: application/json' \
  http://elasticsearch:9200/my-index \
  -d @curl2log.json
```
