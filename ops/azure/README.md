# Operations Chet Sheet

## Azure Commands

- Login
  - `az login`
- Set account context.
  - `az account set --subscription 1d8573de-6262-4e30-b665-a2ce4f6c9adf`
- Get credentials
  - `az aks get-credentials --resource-group hb-aks-westus-dev-001 --name hbaks`
- Start dashboard
  - `az aks browse --resource-group hb-aks-westus-dev-001 --name hbaks`
- Get public IP
  - `az network public-ip list --resource-group MC_hb-aks-westus-dev-001_hbaks_westus --query [0].ipAddress --output tsv`

## Kubernetes Commands

- Watch service
  - `kubectl get service nginx-svc --watch`