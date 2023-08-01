# Deploy HashiCorp Vault Helm Chart through Openshift GitOps
## Prerequisites
- Openshift Container Platform 4.y
- Openshift Gitops Operator installed
- ArgoCD CLI tool installed

## Procedure
First of all, be sure that the ArgoCD Controller Service Account got the same permissions as the Cluster Admin role: \
`oc adm policy add-cluster-role-to-user -z openshift-gitops-argocd-application-controller cluster-admin`

Now, let's create a new project where we want to deploy the Hashicorp Vault application: \
`oc new-project hashi-vault`

Apply the following label to the project: \
`oc label namespaces hashi-vault argocd.argoproj.io/managed-by=openshift-gitops`

Then, let's deploy the manifests: \
`oc apply -f sealed-secrets.yaml`
