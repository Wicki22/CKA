# Instruction

## Confirm that Nodes are Up

`kubectl get nodes`

## Create load balancer

```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.7/config/manifests/metallb-native.yaml

kubectl create -f yaml/loadbalancer.yaml
```

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

Copy the external IP of the load balancer and paste it into your browser to access the nginx web server homepage.

OR

curl to the load balancers external IP. For example, if the external IP is 192.168.1.240, use it.

`curl 192.168.1.240`

## Clean Up

`kubectl -f delete yaml`
