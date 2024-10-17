# Elastic Search

Get Elastic Search working with local Docker Desktop by following this [guidance](https://www.elastic.co/downloads/elastic-cloud-kubernetes):

1. Install ECK (Elastic Cloud on Kubernetes) with below command:
```
kubectl create -f https://download.elastic.co/downloads/eck/2.11.1/crds.yaml
kubectl apply -f https://download.elastic.co/downloads/eck/2.11.1/operator.yaml
```
Above 2 commands created a namespace **elastic-system**, there are a statefulset, service and pod running in the namespace:
```
kubectl get all -n elastic-system
NAME                     READY   STATUS    RESTARTS   AGE
pod/elastic-operator-0   1/1     Running   0          34s

NAME                             TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
service/elastic-webhook-server   ClusterIP   10.107.48.61   <none>        443/TCP   34s

NAME                                READY   AGE
statefulset.apps/elastic-operator   1/1     34s
```

2. Follow this [guidance](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-elasticsearch.html) then obtain an Elastic Search running instance.

2.1 Drafted [elastic-search.yaml](k8s/elastic-search.yaml), then run below command:
```
kubectl apply -f elastic-search.yaml -n elastic-system
```
Note: You can create a new namespace **<namespace>** isolate created resource


3. Verify Elastic Search,

3.1 Verify running pod
```
kubectl get pods --selector='elasticsearch.k8s.elastic.co/cluster-name=chinsiang-testing' -n elastic-system
```

3.2 Verify service
```
kubectl get service chinsiang-testing-es-http -n elastic-system
```

Please refer [kibana.md](kibana.md), Elastic Search does not coming UI by default. Kibana offers us an UI.
