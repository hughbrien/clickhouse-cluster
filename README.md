# clickhouse-cluster
Clickhouse Clusters running on Kubernetes

[clickhouse Operator](https://www.propeldata.com/blog/clickhouse-operator)

helm repo add clickhouse-operator 


Edit metrics-server deployment descriptor and add the following to the 


### Add the following 

```

    -’--kubelet-insecure-tls’
    -’--kubelet-preferred-address-types=InternalIP’

containers:

        - name: metrics-server
          image: registry.k8s.io/metrics-server/metrics-server:v0.7.1
          args:
            - '--cert-dir=/tmp'
            - '--secure-port=10250'
            - '--kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname'
            - '--kubelet-use-node-status-port'
            - '--metric-resolution=15s'
            - '--kubelet-insecure-tls'
            - '--kubelet-preferred-address-types=InternalIP'
```

  
