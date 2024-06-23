# clickhouse-cluster
Clickhouse Clusters running on Kubernetes

[clickhouse Operator](https://www.propeldata.com/blog/clickhouse-operator)

helm repo add clickhouse-operator 


Edit metrics-server deployment descriptor and add the following to the 

### Metrics Server 
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```
### Add the following 

```
    -’--kubelet-insecure-tls’
    -’--kubelet-preferred-address-types=InternalIP’

containers:

        - name: metrics-server
          image: registry.k8s.io/metrics-server/metrics-server:v0.7.1
          args:
            - '--kubelet-insecure-tls'
            - '--kubelet-preferred-address-types=InternalIP'
```

  
