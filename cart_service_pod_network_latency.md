# cart service pod network latency
## Description
- This experiment injects network latency to the cart service pod.
- The Probe checks Prometheus metrics Latency of cart service requests.
## Steps
### 1. Probe Settings
- probe type: `Prometheus Probe`
- name: `cart-service-pod-network-latency-probe`
- timeout: 3s
- interval: 3s
- prometheus endpoint: `http://my-otel-demo-prometheus-server.otel-demo:9090`
- prometheus query: `histogram_quantile(0.50, sum(rate(duration_milliseconds_bucket{service_name=\"cartservice\"}[5m])) by (le))`
- Data Comparison:
  - Type: Float
  - Criteria: `<`
  - Value: `10.0`
### 2. Make Experiment
### 3. Run Experiment