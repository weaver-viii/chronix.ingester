# chronix.ingester

The Chronix Ingester batches up sample data from various sources and
stores it as chunks in Chronix. Currently, only [Prometheus](https://prometheus.io/)
is supported.

## Building

Building requires [Go](https://golang.org/dl/) 1.7 or newer, as well as a
working [`GOPATH` setup](https://golang.org/doc/code.html).

To build the ingester:

```
go build
```

## Running

Example:

```
./chronix.ingester -chronix-url=http://my-solr-host:8983/solr/chronix -max-chunk-age=30m
```

To show all flags:

```
./chronix.ingester -h
Usage of ./chronix.ingester:
  -chronix-url string
    	The URL of the Chronix endpoint. (default "http://localhost:8983/solr/chronix")
  -listen-addr string
    	The address to listen on. (default ":8080")
  -log.format value
    	Set the log target and format. Example: "logger:syslog?appname=bob&local=7" or "logger:stdout?json=true" (default "logger:stderr")
  -log.level value
    	Only log messages with the given severity or above. Valid levels: [debug, info, warn, error, fatal] (default "info")
  -max-chunk-age duration
    	The maximum age of a chunk before it is closed and persisted. (default 1h0m0s)
```

## Testing

To run tests:

```
go test ./...
```
