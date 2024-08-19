# shipping service pod cpu hog
## Description
- This experiment injects cpu hog to the shipping service pod.
- The Probe checks Prometheus metrics Latency of shipping service requests.
## Steps
### 1. Probe Settings
- probe type: `Prometheus Probe`
- name: `shipping-service-pod-cpu-hog-probe`
- timeout: 3s
- interval: 3s
- attempt: 3
- prometheus endpoint: `http://otel-demo-prometheus-server.otel-demo:9090`
- prometheus query: `histogram_quantile(0.99, sum(rate(duration_milliseconds_bucket{service_name=\"shippingservice\"}[5m])) by (le)) / 1000`
- Data Comparison:
  - Type: Float
  - Criteria: `<`
  - Value: `3.0`
### 2. Make Experiment
1. New Experimnet
2. Complete Overview
3. Start off by Upload YML(shipping-service-pod-cpu-hog.yml)
### 3. Run Experiment
1. Click on the `Run` button
2. Check Experiment Status and Logs
3. Check the Resilience Score
4. Check shipping service Spanmetrics Metrics using Grafana