# Start Cluster

    minikube start --driver=virtualbox

# Create a Namespace for ArgoCD

    kubectl create namespace argocd

# Install ArgoCD

    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Wait for Pods to be Ready

    kubectl get pods -n argocd --watch

# Access ArgoCD UI

    kubectl port-forward svc/argocd-server -n argocd 808:443

    https://localhost:8080

# Retrieve Admin Password

    kubectl -n argocd get secret argo-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

    Username: admin
    Password: *****
