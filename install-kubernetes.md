## add namespace
```bash
kubectl create namespace monitoring
```

## install prometehus-community
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

## Untuk setup lengkap (Prometheus + Grafana + Alertmanager + node-exporter + kube-state-metrics)
```bash
helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring
```

## cek semua pod
```bash
kubectl get pods -n monitoring
```

## akses grafana, ambil password admin
```bash
kubectl get secret monitoring-grafana -n monitoring \
  -o jsonpath="{.data.admin-password}" | base64 --decode
``` 

## port forward
```bash 
kubectl port-forward svc/monitoring-grafana 3000:80 -n monitoring 
``` 

## akses
```bash 
http://localhost:3000
```
