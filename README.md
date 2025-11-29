# Full-end-to-end-DevOps-monitoring-workflow ##

Scenario

You have a web application running in EKS, with Istio sidecars. You want to:

Monitor CPU usage of your app pods.

Trigger an alert if CPU exceeds 80% for 5 minutes.

Notify via SNS.

Automatically scale the deployment using a Lambda function.