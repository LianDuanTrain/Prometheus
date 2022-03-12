# How to Add Dashboard into Grafana?
## Topics  
- What is Grafana?   
- Environmental Requirements
- Add Dashboard into Grafana   
- Fix miss match JVM Metrics in Dashboard  
  
## <img src='Grafana.png' width="3%"> What is Grafana?         

Grafana is a multi-platform open source analytics and interactive visualization web application.   
### Basic Components
- Data source   
   <image src="sidemenu-datasource-7-5.png" width="10%">
- Query editor   
  <image src="prometheus_query_editor.gif" width="50%">
- Panel   
  <image src="panel-editor-8-0.png" width="50%">
- Row  
  <image src="row.png" width="50%">
- Dashboard   
  <image src="dashboard.png" width="50%">

## Environmental Requirements 
- [Install Docker on Oracle Linux 8](https://youtu.be/403H_L8UOKk)  
- [Install Minikube on Oracle Linux 8](https://youtu.be/NHYryUAwDpI)
- [Install Helm 3 on Oracle Linux 8](https://youtu.be/k6q92VGfmVQ)
- [How to Add JAVA OPTS in Docker? | Java App Docker Image | Configure JAVA_OPTS in JAVA Docker Image](https://youtu.be/kAKtfh0u4xg)   
  -'docker run -e JAVA_OPTS='-javaagent:/jmx_prometheus_javaagent-0.16.1.jar=9999:/config.yaml'  --rm -d -p 9999:9999  lianduantraining/log-generator-jmx-exporter:v1' 
- [Use Helm 3 to Install Prometheus Stack on Minikube in 10 Mins](https://youtu.be/wfxu053rbbI)  
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update 
helm install lian-training prometheus-community/kube-prometheus-stack --namespace=prometheus --create-namespace --wait --version 33.0.0' 
helm list -n prometheus   
```
- [Use Prometheus Monitor External Java App JVM](https://youtu.be/zhW39VC_1C4)
```
helm install lian-training prometheus-community/kube-prometheus-stack --namespace=prometheus --create-namespace --wait --version 33.0.0   
kubectl get prometheus -n prometheus  
kubectl get prometheus -n prometheus lian-training-kube-prometh-prometheus -o yaml  
kubectl create -f  external-java-app-service-monitor.yaml  
```



## Add Dashboard into Grafana   
- Dashboard Resource
  - https://grafana.com/grafana/dashboards/
  - https://play.grafana.org/
- Port Forward  
```
Prometheus UI    
kubectl port-forward service/prometheus-operated  9090 --namespace=prometheus 
Prometheus Grafana   
kubectl port-forward deployment/lian-training-grafana 3000 --namespace=prometheus
```   

- Download JVM Dashboard JSON File
  - https://grafana.com/grafana/dashboards/8563
  - https://github.com/LianDuanTrain/Prometheus/blob/main/1-3%20How%20to%20Add%20Dashboard%20into%20Grafana/MD/Dashboard_JSON/jvm_dashboard.json
- Login to Grafana
  - URL:localhost:3000
  - admin/prom-operator
- Import Dashboard JSON File
   - Create => Import 
 
## Fix miss match JVM Metrics in Dashboard   
- No data render on some Panels because Dashboard metrics miss match Target metrics
- Get correct Target metrics, and change metrics in panels.

## Summary   
- Grafana   
- Environmental Requirements  
- Add Dashboard into Grafana     
- Fix miss match JVM Metrics in Dashboard       





<h7>
Icons are from https://www.pngaaa.com/ and https://grafana.com/
</h7>
