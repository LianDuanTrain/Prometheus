# Prometheus Alertmanager
## Topics
- What is Prometheus Alertmanager?
- Prometheus Alert  
- Alertmanager Components 
- Alertmanager Workflow 
- Hands on Demo Grouping,Inhibition,and Silences on Alertmanager   


## What is Prometheus Alertmanager?  
- Handles alerts sent by client applications such as the Prometheus server.   
- Takes care of deduplicating, grouping, routing, silencing , inhibition them to the correct receiver integration such as email, PagerDuty. 

## Prometheus Alert  
- Alert Rule 
  - http://localhost:9090/rules
  - <image src='./images/rules.png'  width="100%">  
-  Evaluation Parameters    
<image src='./images/alertRuleStatus2.png'  width="80%"> 
- Alert Status  
  - http://localhost:9090/alerts  
<image src='./images/alertRuleStatus1.png'  width="120%">  
 


## Alertmanager Concepts

- Grouping
  -  /rules/*-rules.yml
  - <image src='./images/5.png'  width="30%"> 
- Inhibition
  - alertmanager.yml   
  - <image src='./images/7.png'  width="20%"> 
- Silences
  - CMD   
  <image src='./images/8.png'  width="80%">  
  - WEB  
## Alertmanager Workflow

<image src='./images/alertmanager.png'  width="100%"> 


## Hands on Demo Grouping,Inhibition,and Silences on Alertmanager  
Based line YAML files are from   [Monitoring React App Spring Boot App and Redis with Prometheus ](https://youtu.be/6WbLRVpviO0)

- Grouping
- Inhibition
- Silences

## Summary   

- What is Prometheus Alertmanager?
- Prometheus Alert  
- Alertmanager Components 
- Alertmanager Workflow 
- Hands on Demo Grouping,Inhibition,and Silences on Alertmanager   


