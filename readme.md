## Commands
$ gcloud auth login / auth revoke
$ gcloud config list
$ gcloud projects list
$ gcloud config set project <project-id>

$ gcloud builds submit -t gcr.io/<project-id>/<registry-name>:<commit-nb> <path-to-docker>

$ gcloud container clusters create <cluster-name> --zone=us-central1-f --machine-type=n1-standard-1 --num-nodes=1
$ gcloud container clusters get-credentials <cluster-name> --zone=us-central1-f --project <project-id>

$ gcloud compute disks create --zone=us-central1-f --size=200GB <disk-name>
$ gcloud compute instances detach-disk <instance-name> --disk=<disk-name> --zone=us-central1-f

$ kubectl create -f <my-file.yaml>

$ kubectl set image <deployment-version>/<deployment-name> <spec-containers-name>=gcr.io/<project-id>/<registry-name>:<commit-id>


## Kubernetes SSL
(cf. https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nginx-ingress-with-cert-manager-on-digitalocean-kubernetes)

$ kubectl create -f <mysite-app.yml>
$ kubectl create -f <mysite-server.yml>

$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.24.1/deploy/mandatory.yaml
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.24.1/deploy/provider/cloud-generic.yaml

$ kubectl get svc --namespace=ingress-nginx

(if helm not installed locally)
  $ curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > install-helm.sh
  $ chmod u+x install-helm.sh
  $ ./install-helm.sh
(endif)

$ kubectl -n kube-system create serviceaccount tiller
$ kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
$ helm init --service-account tiller
$ kubectl get pods --namespace kube-system

$ kubectl apply -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.8/deploy/manifests/00-crds.yaml
$ kubectl label namespace kube-system certmanager.k8s.io/disable-validation="true"
$ helm repo add jetstack https://charts.jetstack.io
$ helm install --name cert-manager --namespace kube-system jetstack/cert-manager --version v0.8.0

$ kubectl create -f prod-issuer.yaml
$ kubectl apply -f ingress.yaml
$ kubectl describe certificate letsencrypt-prod

check ssl on website !
