# Step 1: Deploy via the ArgoCD UI

    https://localhost:8080

    + CREATE APPLICATION

    Application Name: my-first-app-ui
    Project: default
    SYNC POLICY: Manual
    SOURCE -> Respository URL: https://github.com/AkashKoche/gitops-mastery.git
    SOURCE -> Revision: main
    SOURCE -> Path: day-2
    DESTINATION -> Cluster URL: https://kubernetes.default.svc
    DESTINATION -> Namespace: default
    "CREATE"
    "SYNC"
    "SYNCHRONIZE"
    Syncing to Healthy

# Step 2: Verify the Deployment in Kubernetes

    kubectl get pods.svc -n default

# Step 3: Install ArgoCD CLI and Deploy

    Complete ArgoCD CLI Installation

    argocd login localhost:8080 --insecure --username admin --password <argo-cd-password>

    kubectl apply -f app-cli.yaml -n argocd

    argocd app get my-first-app

# Step 4 Configure Auto-Sync and Self-Healing

    Goto my-first-app-ui
    "APP DETAILS" -> "SYNC POLICY" -> "ENABLE AUTO-SNYC"
    "Prune Resources" and "Self-Heal"
    Change State, Edit nginx-deployment.yaml , Change replicas: 2 to replicas: 3
    Commit and Push
    Watch ArgoCD UI

# Step 5 Simulate and Resolve Configuration Drift

    kubectl scale deployment nginx-deployment --replicas=1 -n argocd
