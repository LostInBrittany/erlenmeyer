# Erlenmeyer: Time Series query translator

Erlenmeyer is a Go Proxy used to parse multiple Open Source TimeSeries DataBase query (OpenTSDB, PromQL, Prometheus-remote_read, InfluxQL and Graphite) . Then they are translated into WarpScript to produce native [Warp 10](https://warp10.io/) queries.

![Erlenmeyer: Time Series query translator](./assets/logo.png)

You can test and run locally erlenemeyer following those [building steps](./doc/BUILDING.md).

## Supported protocols

| Name       | State   | Documentation |
| ---------- | ------- | ------------- |
| Warp10     | Native  | [doc](https://warp10.io/doc/reference) |
| PromQL     | Near full | [doc](./doc/promql.md) |
| Prometheus - Remote-read | Near full | [doc](./doc/remote_read.md) |
| OpenTSDB   | Near full | [doc](./doc/openTSDB.md) |
| Graphite   | Partial | [doc](./doc/graphite.md) |
| InfluxQL   | New | [doc](./doc/influxql.md) |

## Motivation

At [OVHcloud](https://github.com/ovh), a lot of Metrics users were used to a previous TSDB experience with which they felt confortable and efficient. The goal of Erlenmeyer was to leverage their existing habits, while converging on the Metrics Time Series platform. Hence we decided to welcome customers adding more and more protocols from several Open Source Time Series DB. Under the hood, the Warp10 platform offers the powerful WarpScript query language which was a great help on this process, by just implementing all the query layers as a transpilation step. The best part of it, is now you can have: the same backend, the same data and some Grafana Dashboard written in PromQL when others are using OpenTSDB!

## Status

Erlenmeyer is used in production.

## Contributing

Instructions on how to contribute to Erlenmeyer are available on the [Contributing](./CONTRIBUTING.md) page.

## Metrics

Erlenmeyer exposes metrics about his usage:

| name                               | labels                  | type    | description                           |
| ---------------------------------- | ----------------------- | ------- | ------------------------------------- |
| erlenmeyer_exec_request            | app, token_id, protocol | counter | Warp execution count                  |
| erlenmeyer_exec_fetched_datapoints | app, token_id, protocol | counter | Number of datapoints fetched          |
| erlenmeyer_exec_ops                | app, token_id, protocol | counter | Number of WarpScript operations       |
| erlenmeyer_exec_error_request      | app, token_id, protocol | counter | Warp 10 error by user application     |
| erlenmeyer_http_request            |                         | counter | Number of http request handled        |
| erlenmeyer_http_error_request      |                         | counter | Number of http request in error       |
| erlenmeyer_http_status_code        | status                  | counter | Counter per requests status code      |
| erlenmeyer_http_response_time      | path                    | counter | Requests response time in nanoseconds |
| erlenmeyer_protocol_request        | protocol                | counter | Requests by protocol                  |
| erlenmeyer_protocol_error_request  | protocol, status        | counter | Requests error by protocol and status |
| erlenmeyer_graphite_function       | function                | counter | Function used by user of graphite     |
| erlenmeyer_influxdb_request        | function                | counter | Number of requests handled            |
| erlenmeyer_influxdb_errors         | function                | counter | Number of requests in errors          |
| erlenmeyer_influxdb_warning        | function                | counter | Number of errored client requests     |
| erlenmeyer_opentsdb_request        | function                | counter | Number of requests handled            |
| erlenmeyer_opentsdb_errors         | function                | counter | Number of requests in errors          |
| erlenmeyer_opentsdb_warning        | function                | counter | Number of errored client requests     |
| erlenmeyer_promql_request          | function                | counter | Number of requests handled            |
| erlenmeyer_promql_request          | function                | counter | Number of requests handled            |

## Licence

Erlenmeyer is released under a [3-BSD clause license](./LICENSE).

## Get in touch

- Gitter: [metrics](https://gitter.im/ovh/metrics)
