# recommendation service pod memory hog
## Description
- This experiment injects memory hog to the cart service pod.
- The Probe checks Prometheus metrics Latency of cart service requests.
## Steps
### 1. Probe Settings
- probe type: `Prometheus Probe`
- name: `rcmd-service-pod-memory-hog-probe`
- timeout: 3s
- interval: 3s
- attempt: 3
- prometheus endpoint: `http://otel-demo-prometheus-server.otel-demo:9090`
- prometheus query: `process_runtime_cpython_memory_bytes{type="rss", job="opentelemetry-demo/recommendationservice"}`
- Data Comparison:
  - Type: Float
  - Criteria: `<`
  - Value: `100.0`
### 2. Make Experiment
1. New Experimnet
2. Complete Overview
3. Start off by Upload YML(rcmd-service-pod-memory-hog.yml)
### 3. Run Experiment
1. Click on the `Run` button
2. Check Experiment Status and Logs
3. Check the Resilience Score
4. Check shipping service Spanmetrics Metrics using Grafana