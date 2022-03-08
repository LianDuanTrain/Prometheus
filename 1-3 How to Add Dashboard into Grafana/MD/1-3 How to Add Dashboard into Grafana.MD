# How to Add Dashboard into Grafana?
## Topics  
- What is Grafana?   
- Environmental Requirements
- Add Dashboard into Grafana   
- Rematch JVM Metrics and Verify Dashboard  
  
## <img src='Grafana.png' width="3%"> What is Grafana?         

Grafana is a multi-platform open source analytics and interactive visualization web application. 
- Data source 
- Query editors
- Panels
- Rows
- Dashboards


## Environmental Requirements 
- [Install Minikube on Oracle Linux 8](https://youtu.be/NHYryUAwDpI)
- [Install Docker on Oracle Linux 8](https://youtu.be/403H_L8UOKk)  
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
  - https://grafana.com/docs/grafana/latest/getting-started/getting-started/
  
- Download Dashboard JSON File
  - https://grafana.com/grafana/dashboards/8563
- Import Dashboard JSON File
   - https://grafana.com/docs/grafana/latest/dashboards/export-import/
 
## Rematch JVM Metrics and Verify Dashboard  

## Summary   
- Grafana   
- Environmental Requirements  
- Add Dashboard into Grafana     
- Rematch JVM Metrics and Verify Dashboard    


<h7>
ICONs are from https://www.pngaaa.com/  
</h7>
