# Operte Azure Kubernetes Cluster

- Set account context.
  - `az account set --subscription 1d8573de-6262-4e30-b665-a2ce4f6c9adf`
- Get credentials
  - `az aks get-credentials --resource-group hb-aks-westus-dev-001 --name hbaks`
- Start dashboard
  - `az aks browse --resource-group hb-aks-westus-dev-001 --name hbaks`