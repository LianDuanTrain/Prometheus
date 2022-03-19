# Install Prometheus, Alertmanager, Grafana, and Pure Java App using Docker Compose 
## Topics
- Demo ENV Detail 
- Target Version
- System Overview
- Use Docker Compose to Install Prometheus, Alertmanager, Grafana, and Pure Java App 
- Verify Services   
- Test Alert Email

## Demo ENV Detail  
- OS version - Oracle Linux Server release 8.4   
  -`cat /etc/oracle-release`
- Docker Version - 20.10.6  
  -`docker -v`   
- Docker Compose Version - 1.27.4
  - `docker-compose version`  
  - https://docs.docker.com/compose/compose-file/

## Target Versions
- Prometheus: v2.33.5
- Alertmanager: v0.23.0
- Grafana: 8.4.3
  
## System Overview 
<image src="system.gif" >

## Use Docker Compose to Install Prometheus, Alertmanager, Grafana, and Pure Java App 
- File Structure 
 ``` 
  - prometheus
    - config
      - rules
        -  java-app-rules.yml
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

```
version: '3.8'
services:
# prometheus service
  prometheus:
   # Run Container as root user
    user: root
    image: prom/prometheus:v2.33.5
    container_name: prometheus
    hostname: localhost
    restart: always
    ports:
      - '9090:9090'
   # Mount config file from local to Container
    volumes:
      - './prometheus/config:/config'
      - './prometheus/data/prometheus:/prometheus/data'
   # Container start CMD to load config file   
    command:
      - '--config.file=/config/prometheus.yml'
      - '--web.enable-lifecycle'
    networks:
            - prometheus
  alertmanager:
    # Run Container as root user
    user: root
    image: prom/alertmanager:v0.23.0
    container_name: alertmanager
    hostname: localhost
    restart: always
    ports:
      - '9093:9093'
   # Mount config file from local to Container  
    volumes:
      - './prometheus/config:/config'
      - './prometheus/data/alertmanager:/alertmanager/data'
   # Container start CMD to load config file   
    command:
      - '--config.file=/config/alertmanager.yml'
    networks:
      - prometheus
  grafana:
     # Run Container as root user
    user: root
    image: grafana/grafana:8.4.3
    container_name: grafana
    hostname: localhost
    restart: always
    ports:
      - '3000:3000'
   # Mount config file from local to Container     
    volumes:
      - './grafana/config/grafana.ini:/etc/grafana/grafana.ini'
      - './grafana/data/grafana:/var/lib/grafana'
    networks:
      - prometheus
  log-generator-jmx-exporter:
    restart: always
    environment:
      - 'JAVA_OPTS=-javaagent:/jmx_prometheus_javaagent-0.16.1.jar=9999:/config.yaml'
    ports:
      - '9999:9999'
    image: 'lianduantraining/log-generator-jmx-exporter:v1'
    networks:
      - prometheus
networks:
  prometheus:
    name: prometheus           

```  

- `docker-compose up -d`  



## Verify Services  
- Prometheus
  - http://localhost:9090/targets
  - http://localhost:9090/rules
- Alertmanager  
  - http://localhost:9093
- Grafana
  - http://localhost:3000
  - admin/admin

## Test Alert Email
- Stop Docker Container: log-generator-jmx-exporter
- Verify 
  - http://localhost:9090/targets
  - http://localhost:9090/rules
- Check Email


## Summary  
- Demo ENV Detail 
- Target Versions   
- Use Docker Compose to Install Prometheus, Alertmanager, Grafana, and External Java App 
- Verify Services   
- Test Alert Email   