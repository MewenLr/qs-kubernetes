## - Kubernetes -


#### Kubectl command
```sh
kubectl create -f <my-file.yml>

kubectl set image <deployment-version>/<deployment-name> <spec-containers-name>=gcr.io/<project-id>/<registry-name>:<commit-id>
```

#### Cluster deployment
```sh
# if helm not installed locally

  curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > install-helm.sh

  chmod u+x install-helm.sh

  ./install-helm.sh

kubectl -n kube-system create serviceaccount tiller

kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller

helm init --service-account tiller

kubectl get pods --namespace kube-system

helm install --name nginx-ingress stable/nginx-ingress --set controller.publishService.enabled=true

kubectl get services -o wide -w nginx-ingress-controller

kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.14.1/cert-manager.crds.yaml

kubectl create namespace cert-manager

helm repo add jetstack https://charts.jetstack.io

helm install --name cert-manager --version v0.14.1 --namespace cert-manager jetstack/cert-manager

kubectl create -f <prod-issuer-file.yml>

# -> link cluster to domain name and update DNS

kubectl create -f <ingress-file.yml>

kubectl describe certificate <my-site-tls>

# if certificate pending for too long

kubectl get challenges --all-namespaces

kubectl describe challenge <tls-host-secretName>
```
