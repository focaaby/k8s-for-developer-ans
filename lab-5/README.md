# Cluster Autoscaler

## demo

### CA trigger Scale up

1. Scale down nodes.
```
eksctl scale ng --cluster demo ng-768b171c --nodes=2 --nodes-max=8 --profile=user-admin
```

2. Add resource request in the lab-2 deployment, and set replica count to 20.
3. Observe CA logs

```
kubectl -n kube-system logs cluster-autoscaler-6cf6469978-hlhf7
```


### CA trigger Scale down

- Set replica count to 5.


## Ref

- https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/FAQ.md