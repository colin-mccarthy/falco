
## Setup

kind export kubeconfig --name sysdig

alias k=kubectl



bash sysdig.sh 

kind get clusters




## linux headers


```
#!/bin/bash

#First we need to install the linux headers for the host - Ubuntu is assumed for the book
sudo apt install linux-headers-$(uname -r)

#Falco requires the kernel-headers of the OS to be present to create a falco-probe
#This will copy the kernel-headers on the Host into the worker node running in Docker
docker cp /usr/src cluster01-control-plane:/usr

```


## install falco

``` 
helm repo add falcosecurity https://falcosecurity.github.io/charts

helm repo update
 ```

```
helm install falco falcosecurity/falco \
    --create-namespace \
    --namespace falco \
    --set driver.kind=ebpf
```

```
k get pods -n falco -o wide

kubectl wait pods --for=condition=Ready --all -n falco

```

```
helm upgrade --namespace falco falco falcosecurity/falco -f falco_custom_rules_cm.yaml --set falcosidekick.enabled=true --set falcosidekick.webui.enabled=true
```

```
kubectl -n falco get svc
```

```
kubectl -n falco port-forward svc/falco-falcosidekick-ui 2802
```


## Links

https://github.com/falcosecurity/evolution/issues/4

https://falco.org/docs/getting-started/falco-kubernetes-quickstart/
