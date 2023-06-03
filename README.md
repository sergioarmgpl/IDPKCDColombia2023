# IDPKCDColombia2023
1. Create a Firewall rule to open the firewall to access your cluster

2. Set the project and region:
```
gcloud config set compute/zone us-central1-a
gcloud config set project cs-nonprod
```

3. Create your cluster:
```
gcloud container clusters create kcd-colombia --num-nodes=1 --tags=allin,allout --machine-type=n1-standard-2 --no-enable-network-policy
```

4. Install ArgoCD:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

5. Install ArgoCD CLI:
```
brew install argocd
```

6. Access ArgoCD installation:
kubectl port-forward svc/argocd-server -n argocd 8080:443

Open http://localhost:8080 in your browser

argocd admin initial-password -n argocd

7. Update the password using the UI

8. Create namespace for your Kubernetes deployments
kubectl create namespace development 

9. Create an ArgoCD Project
kubectl apply -f projects/
