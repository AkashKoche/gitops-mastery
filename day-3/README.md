# Install Argo Rollouts

    kubectl create namespace argo-rollouts

    kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

# Install Kubectl Plugin for Visualization

    curl -LO https://github.com/argoproj/argo-rollouts/releases/latest/download/kubectl-argo-rollouts-linux-amd64

    chmod +x ./kubectl-argo-rollouts-linux-amd64

    sudo mv ./kubectl-argo-rollouts-linux-amd64 /usr/local/bin/kubectl-argo-rollouts

# Verify

    kubectl get all -n argo-rollouts

    kubectl argo rollouts version

# Trigger a Canary Update

    Change image version Edit rollout-canary.yaml file nginx:1.25-alpine to nginx:1.26-alpine

    Commit and Push to Git

# Manage Rollout (Watch & Promote)

    kubectl argo rollouts get rollout nginx-canary-demo --watch

# Use Rollouts Dashboard

    kubectl argo rollouts dashboard

# Abort a Failed Canary

    git revert HEAD

    git push origin main

# Alternatively

    kubectl argo rollouts abort rollout nginx-canary-demo
