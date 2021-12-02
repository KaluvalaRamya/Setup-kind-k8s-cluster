<!-- Headings -->
# **SETUP KIND-K8S CLUSTER**
## **Setup a 3 Node cluster(1 Master & 2 Workers).**

### **Step-1 : Creating a Virtual Machine**
<!-- UL -->
* Login to your GCP Account.
* Launch VM.

### **Step-2 : Connect to Instance**
* Now you are connected to Ubuntu VM through SSH and use sudo while executing commands.

### **Step-3 : Install kubectl**
<!-- Blockquote -->
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```
### **Step-4 : Installing kind From Release Binaries on Linux**
```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/bin/kind
```

### **Step-5 : Install Docker**
```
sudo apt-get update
sudo apt-get install docker.io
```
### **Step-6 : create Multi-node cluster (1master&2workernodes)**

* we need to create  config file(kind-config.yaml) with following content for creating 3 node cluster.
```
# three node (two workers) cluster config
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```
* Create cluster by using below command
```
kind create cluster --config kind-config.yaml
```
### **Step-7 : To see the list of nodes**
```
kind get nodes
```
### **Step-8 : To see the list of docker containers**
```
docker ps -a
```
---
You can refer [this page](https://kind.sigs.k8s.io/docs/user/quick-start) for kind-k8s.
---