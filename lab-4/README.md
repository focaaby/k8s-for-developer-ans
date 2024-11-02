# ConfigMap, Secret

## ConfigMap

1. 建立 ConfigMap `nginx-conf`。

```
$ kubectl apply -f ./nginx-cm.yaml
configmap/nginx-conf created
```

2. 修改 lab-2 [nginx-deployment](../lab-2/nginx-deployment.yaml)，增加 volume 掛載上一步驟所建立 ConfigMap `nginx-conf`，並透過 `kubectl apply` 更新 Deployment。

3. 更新 ConfigMap `nginx-conf`，，並透過 `kubectl apply` 更新 ConfigMap。

```
        listen       80;
        listen  [::]:80;
```

4. 檢視 Nginx 是否生效，為什麼？

## Secret


1. 使用 kubectl 命令建立 secret `backend-user`。

```
$ kubectl create secret generic backend-user --from-literal=backend-username='backend-admin'
```

2. 用 kubectl 進入至 Pod
<!-- TODO: 刪除 nginx-deployment-with-secret.yaml，現場說明增加  -->
```
$ kubectl exec -it nginx-deployment-5b55bc6455-g6tcm -- bash
```

3. 使用 `env` 印出環境變數 `$SECRET_USERNAME`，或使用 echo 印出環境變數 `$SECRET_USERNAME`

```
root@nginx-deployment-5b55bc6455-g6tcm:/# env | grep "SECRET_USERNAME"
SECRET_USERNAME=backend-admin

root@nginx-deployment-5b55bc6455-g6tcm:/# echo $SECRET_USERNAME
backend-admin
```

* 問題：環境變數到底誰該負責？DevOps/SRE 或是 developer？
