# Setup Kibana

Please refer [elastic-search.md](./elastic-search.md) if you haven't done it! We need elastic operator for the installation.

I have drafted [kibana.yaml](./kibana.yaml). By following previous learn steps, I prefer install it under namespace elastic-system. The comand is as below:
```
kubectl apply -f kibana.yaml -n elastic-system
```

To verify it with below command:
```
kubectl get kibana -n elastic-system
NAME         HEALTH   NODES   VERSION   AGE
kibana-chinsiang-testing   green    1       8.12.2    26s
```
Note: It took some time turn from red to green

## Observation

There are some resources created in the namespace: elastic-system.

A pod is running, below command to find it:

> kubectl get pod --selector='kibana.k8s.elastic.co/name=kibana-chinsiang-testing' -n elastic-system

A service is created named **kibana-chinsiang-testing-kb-http**, below command to find it:

> kubectl get service --selector='kibana.k8s.elastic.co/name=kibana-chinsiang-testing' -n elastic-system

It is running on port **5601**

```
kubectl get service kibana-chinsiang-testing-kb-http -n elastic-system
NAME                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
kibana-chinsiang-testing-kb-http   ClusterIP   10.98.186.17   <none>        5601/TCP   7m18s
```
## Port forward

In order access it by our browser, run port forward:

> kubectl port-forward service/kibana-chinsiang-testing-kb-http 5601 -n elastic-system

Open browser then access https://127.0.0.1:5601/login?next=%2F

Tips: Don't worry of the **password**, actually it has been created and stored in secret. In my case run below command to obtain it:

```
kubectl get secret chinsiang-testing-es-elastic-user -o go-template='{{.data.elastic | base64decode}}' -n elastic-system
```

A default user is **elastic**, you can login it with the password you obtained from secret. 
