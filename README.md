# Full-end-to-end-DevOps-monitoring-workflow ##

Scenario

You have a web application running in EKS, with Istio sidecars. You want to:

Monitor CPU usage of your app pods.

Trigger an alert if CPU exceeds 80% for 5 minutes.

Notify via SNS.

Automatically scale the deployment using a Lambda function.

Step 1: PromQL Query for Istio 4xx Requests

Istio exposes metrics via Prometheus. To count 4xx responses for your app:

sum(rate(istio_requests_total{
  destination_workload="my-web-app", 
  response_code=~"4.."
}[5m])) by (destination_workload)


rate(...[5m]) → calculates requests per second over 5 minutes.

destination_workload="my-web-app" → filter for your app.

response_code=~"4.." → matches all 4xx HTTP status codes.

sum(...) by (destination_workload) → aggregate per service.

✅ This query gives you the number of 4xx requests per second for your app.