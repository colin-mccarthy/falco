bash sysdig.sh 

kind get clusters

kind export kubeconfig --name sysdig

alias k=kubectl


```
#!/bin/bash

#First we need to install the linux headers for the host - Ubuntu is assumed for the book
sudo apt install linux-headers-$(uname -r)

#Falco requires the kernel-headers of the OS to be present to create a falco-probe
#This will copy the kernel-headers on the Host into the worker node running in Docker
docker cp /usr/src cluster01-control-plane:/usr

```



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
```





## Links

https://github.com/falcosecurity/evolution/issues/4
