bash sysdig.sh 

kind get clusters

kind export kubeconfig --name sysdig

alias k=kubectl

k get pods -n sysdig 

