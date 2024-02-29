## Deploy to Kyma

Download the kubeconfig from your Kyma instance via the menu behind the account Icon in the upper right corner. Save it in _~/.kube/kubeconfig-kyma.yml_. Then run:

`export KUBECONFIG=~/.kube/kubeconfig-kyma.yml`

Please note that the token in the kubeconfig is [only valid for 8 hours](https://kyma-project.io/docs/components/security#details-iam-kubeconfig-service). So you might have to redo the download whenever you want to run the commands again.

To keep this project separate from your other deployments I would suggest to create a namespace:

`kubectl create namespace inbucket`

Deploy the configuration:

`kubectl -n inbucket apply -f kyma/deployment.yaml`

Update the container:

`kubectl -n inbucket rollout restart deployment/inbucket`

If you want to delete the deployment, then run:

`kubectl -n inbucket delete -f kyma/deployment.yaml`
