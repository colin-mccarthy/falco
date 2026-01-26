bash sysdig.sh 

kind get clusters

kind export kubeconfig --name sysdig

alias k=kubectl

k get pods -n sysdig 

` helm repo add falcosecurity https://falcosecurity.github.io/charts

helm repo update `
