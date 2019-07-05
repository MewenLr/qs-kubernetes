## - Gcloud -

```sh
gcloud auth login / auth revoke

gcloud config list

gcloud projects list

gcloud config set project <project-id>

gcloud builds submit -t gcr.io/<project-id>/<registry-name>:<commit-nb> <path-to-docker>

gcloud container clusters create <cluster-name> --zone=us-central1-f --machine-type=n1-standard-1 --num-nodes=1

gcloud container clusters get-credentials <cluster-name> --zone=us-central1-f --project <project-id>

gcloud compute disks create --zone=us-central1-f --size=200GB <disk-name>

gcloud compute instances detach-disk <instance-name> --disk=<disk-name> --zone=us-central1-f
```

Proceed to Kubernetes deployment
