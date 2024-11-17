# Instruction

## Confirm that Nodes are Up

`kubectl get nodes`

## Create new replicasets

`kubectl create -f yaml/replicaset.yml`

## Confirm the all pods in the replicaset are running

`kubectl get pod`

## Create a Load Balancer Service

`kubectl create -f yaml/service.yml`

OR

```zsh
kubectl expose replicaset nginx-replicaset-1 --port=80 \
        --name=load-balancer --type=LoadBalancer
```

## Confirm that the load balancer service has been created

`kubectl get service`

Copy the dns name of the load balancer and paste it into your browser to access the nginx web server homepage.

## Clean Up

`kubectl -f delete yaml`
