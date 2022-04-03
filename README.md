# Argo CD
## What is ArgoCD?
- In simple terms, ArgoCD is a continuous deployment tool that allows us to automatically deploy the latest version of an application once code has been merged to the master branch. 
- Greenstand currently does continuous deployment using Github workflows. By using ArgoCD, it simplifies each Github workflow and kubernetes configurations do not need to be stored in Github to deploy.
## Deploying ArgoCD
- Pre-requisites: kustomize and access to kubernetes clusters
- Ensure the proper kubernetes context is set
- Inside the root of one of the environment folders such as `development`, deploy the sealed secrets inside the `resources` folder. Run `kubectl -n argocd apply -f resources/`
- Inside the root of one of the environment folders such as `development`, run `kubectl -n argocd apply -k .`
## ArgoCD Configuration
- ArgoCD has been configured to:
  - use Github SSO to allow users to login using their Github account 
  - notify slack once a deployment is triggered
- The credentials for these configurations can be found in each environment folder such as `development/resources` and need to be deployed before deploying the server and its components
## ArgoCD Access
- ArgoCD is fronted by ambassador so it can be accessed through the ambassador URL. For the dev instance, it can be accessed at http://dev-k8s.treetracker.org/argocd
