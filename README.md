# Install K8S Node 

# Install Plugin 

# Setup NFS Server and NFS StorageClass

# Install Prometheus Operator Stack 

### add Versistent Volume to Prometheus Pod 
```yaml
apiVersion: monitoring.coreos.com/v1
kind: Prometheus
metadata:
  labels:
    app.kubernetes.io/component: prometheus
    app.kubernetes.io/instance: k8s
    app.kubernetes.io/name: prometheus
    app.kubernetes.io/part-of: kube-prometheus
    app.kubernetes.io/version: 3.2.1
  name: k8s
  namespace: monitoring
spec:
  retention: 30d  
  storage:
    volumeClaimTemplate:
      spec:
        storageClassName: nfs-storageclass
        resources:
          requests:
            storage: 200Gi 
```
