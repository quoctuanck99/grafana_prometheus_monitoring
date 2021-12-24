# Install Guide
## **Summary** 
![Overview](https://www.devopsschool.com/blog/wp-content/uploads/2021/01/What-is-Prometheus-Architecutre-components1-740x414.png)
 <br/>
 In Prometheus architecture, with each machine that needs to be monitored we install the several exporters depend on what we want to monitor (Learn more at: https://prometheus.io/docs/instrumenting/exporters/) <br/>
 The exporters launch as an API service & Prometheus server pulls the metrics from exporters (described on the diagram). So to build a monitoring system with Prometheus, the first we need to run the exporters on each machines. 

## **Step by step**
### **1. Exporters**
For easy install, we run exporter as docker containers. Examples:<br/>

> **DCGM Exporter for NVIDIA GPU monitoring metrics**

```
sudo docker run -d --restart unless-stopped --gpus all -p 9400:9400 nvcr.io/nvidia/k8s/dcgm-exporter:2.3.1-2.6.1-ubuntu20.04
```
> **NVIDIA Exporter for NVIDIA GPU monitoring metrics**
```
sudo docker run -d --name nvidia_smi_exporter --restart unless-stopped --device /dev/nvidiactl:/dev/nvidiactl --device /dev/nvidia0:/dev/nvidia0 --device /dev/nvidia1:/dev/nvidia1 --device /dev/nvidia2:/dev/nvidia2 --device /dev/nvidia3:/dev/nvidia3 --device /dev/nvidia4:/dev/nvidia4 --device /dev/nvidia5:/dev/nvidia5 --device /dev/nvidia6:/dev/nvidia6 --device /dev/nvidia7:/dev/nvidia7 -v /usr/lib/x86_64-linux-gnu/libnvidia-ml.so:/usr/lib/x86_64
```
> **Node exporter for system monitoring metrics**
```
sudo docker run -d   --net="host"   --pid="host"   -v "/:/host:ro,rslave"   quay.io/prometheus/node-exporter:latest   --path.rootfs=/host
```
Each exporter service will exposed an API server 
### **2. Prometheus**
After installing the exporters. 
```

```
### 2. Alertmanager 
```

```