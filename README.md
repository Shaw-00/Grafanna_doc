# Grafana_doc

## Tasks done in grafana for Project Hero
-------------------------------------------------
- Installed Prometheus and Grafana on my local machine.
- Setup Prometheus to fetch data from another machine.
- Added Time series Charts and Bar Gaugge in order to view the metrics.

### Bar Graph for Gateway API Request Duration
This graph was built for finding the sum of gateway_api_requests_duration_seconds_bucket where gateway_api_requests_duration_seconds_bucket contains labels le(less than equal to) such that le !=+INF,GATEWAY_httpMethod is equal to GET GATEWAY_apiType is equal to global variable ($apiType) that supports three API Types (customer-api, admin-api, wokrer-api).
The query used for above graph was-
```
sum by(le) (gateway_api_requests_duration_seconds_bucket{le!="'+Inf'", GATEWAY_httpMethod="GET", GATEWAY_apiType="$apiType"})
```
The graph was formatted in HeatMap format.

### Graph for Gateway ApiType
This graph was built for finding the sum of rate of total gateway api requests  where gatewayApiType is equal to global variable ($apiType) that supports three API Types (customer-api, admin-api, wokrer-api) at a particular rate interval.
The query used for above graph was-
```
sum(rate(gateway_api_requests_total{GATEWAY_apiType="$apiType"}[$__rate_interval]))
```
The graph was formatted in TimeSeries format.

### Graph for Gateway Methods
This graph was built for finding the sum of rate of total gateway api requests where gatewayApiType is equal to global variable ($apiType) that supports three API Types (customer-api, admin-api, wokrer-api) at a particular rate interval.
The query used for above graph was-
```
sum(rate(gateway_api_requests_total{GATEWAY_apiType="$apiType"}[$__rate_interval]))
```
The graph was formatted in TimeSeries format.

### Graph for Gateway Routes
This graph was built for finding the sum of rate of total gateway api requests where gatewayApiType is equal to global variable ($apiType) that supports three API Types (customer-api, admin-api, wokrer-api) at a particular rate interval.
The query used for above graph was-
```
sum(rate(gateway_api_requests_total{GATEWAY_apiType="$apiType"}[$__rate_interval]))
```
The graph was formatted in TimeSeries format.

### Built-in Functions used in order to create these Graphs are-
- __rate_interval (It is the recommended interval to use in the rate and increase functions.)
- rate (calculates the per-second average rate of increase of the time series in the range vector)
- sum (used for finding sum of a metric)
- sum by (used for finding sum of metric that has time series)
