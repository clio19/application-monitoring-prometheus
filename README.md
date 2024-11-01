﻿# application-monitoring-prometheus
## Create k8s namespace
-  kubectl create namespace monitoring 

##  Get helm repo
-  helm repo add prometheus-community <https://prometheus-community.github.io/helm-charts>
-  helm search repo prometheus-community
- helm install  prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
- kubectl --namespace monitoring get pods -l "release=prometheus"
- kubectl get pods -n monitoring
- kubectl get svc -n monitoring
- kubectl port-forward -n monitoring svc/prometheus-operated 9090:9090
- kubectl get secret -n monitoring prometheus-grafana -o jsonpath="{.data.admin-password}" | base64 --decode; echo
- kubectl port-forward -n monitoring svc/prometheus-grafana  3000:80
## apply configuration from files
- kubectl apply -f .
- kubectl get svc -n monitoring
## For fast api app 
-kubectl port-forward -n monitoring svc/fastapi-app  8000:8000
- <http://localhost:8000/metrics
- kubectl get  prometheus -n monitoring -o yaml
