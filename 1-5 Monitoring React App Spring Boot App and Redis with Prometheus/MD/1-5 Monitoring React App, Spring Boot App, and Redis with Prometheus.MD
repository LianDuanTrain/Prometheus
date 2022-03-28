# Monitoring React App, Spring Boot App, and Redis with Prometheus | Monitoring Microservices
## Topics
- Environment Detail  
- Demo System 
- Use Docker Compose to Install React App, Spring Boot App, Redis, Exporters, Prometheus, Alertmanager, and Grafana 
- Verify Demo System   
- Test Prometheus Monitoring

## Environment Detail  
- OS version - Oracle Linux Server release 8.4   
  -`cat /etc/oracle-release`
- Docker Version - 20.10.6  
  -`docker -v`   
- Docker Compose Version - 1.27.4
  - `docker-compose version`  
  - https://docs.docker.com/compose/compose-file/  

## Demo System 
### Docker Image
#### App
- <image src='React-icon.png'  width="3%">  React App 
  - Image: lianduantraining/react-app:v3
  - Port：8080
- <image src='springBoot-removebg-preview.png' width="3%">  Spring Boot App
  - Image: lianduantraining/springbootdemo:v6
  - Port：9999
- <image src='redis.png' width="3%">  Redis
  - Image: redis:6.2-alpine
  - Port：6379
#### Exporter
- React App Exporter   
  - Image: nginx/nginx-prometheus-exporter:0.10.0
  - Port: 9113 
- Redis Exporter   
  - Image: oliver006/redis_exporter:v1.37.0
  - Port: 9121  
#### Prometheus Stack 
- <image src='prometheus.png' width="3%">  Prometheus
  - Image: prom/prometheus:v2.33.5
  - Port: 9090
- <image src='prometheus.png' width="3%">  Alertmanager
  - Image: prom/alertmanager:v0.23.0
  - Port: 9093
- <image src='Grafana.png' width="3%">  Grafana
  - Image: grafana/grafana:8.4.3
  - Port: 3000

### Monitoring Data Flow  
<image src="system.jpg" >

## Use Docker Compose to Install React App, Spring Boot App, Redis,Exporters, Prometheus, Alertmanager, and Grafana

- File Structure 
 ``` 
  - prometheus
    - config
      - rules
        - exporter-rule.yml
        - application-rules.yml
      - alertmanager.yml
      - prometheus.yml
    - data
  - grafana
    - config
      - grafana.ini
    - data
  - docker-compose.yml
```  
- docker-compose.yml ([Multi Stage Microservice Build](https://youtu.be/xdpyOwDsXQI) and [Dockerfile File](https://github.com/LianDuanTrain/DoctorEnglishVersion/blob/master/4/Dockerfiles/v5/Dockerfile))  

- `docker-compose up -d`    

## Verify Demo System   
- App  
  - http://localhost:8080 
- Prometheus
  - http://localhost:9090/targets
  - http://localhost:9090/rules
- Alertmanager  
  - http://localhost:9093
- Prometheus Metrics
   - Nginx Prometheus Exporter 
     - http://localhost:9113
   - Spring Boot App 
     - http://localhost:9999/actuator/prometheus
   - Redis exporter
     - http://localhost:9121


## Test Prometheus Monitoring           
- Stop App Container
  - React App
  - Spring Boot App
  - Redis 
  - Check Email

- Stop Exporter
  - React App Exporter
  - Redis Exporter 
  - Check Email   

## Summary   
- Environment Detail  
- Demo System 
- Use Docker Compose to Install React App, Spring Boot App, Redis,Prometheus, Alertmanager, and Grafana 
- Verify Demo System   
- Test Prometheus Monitoring




