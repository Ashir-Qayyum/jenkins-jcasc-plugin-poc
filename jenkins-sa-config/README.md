After installing jenkins in the cluster, I<br>
applied ClusterRoleBinding to jenkins service account<br>
such that it can perform the Helm deployment

I applied it in the cluster with:<br>
> kubectl apply -f jenkins-admin-crb.yaml