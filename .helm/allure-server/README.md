Allure-Server Kubernetes Helm Chart
---

Helm chart to deploy Allure Server to Kubernetes.

### Download and install Helm

[ install helm](https://helm.sh/docs/intro/install/)
### Download chart directory

[allure-server chart](../allure-server)

### Required commands for internal Postgres Server use (*if postgresql.enabled: true*)

- `helm dependency update`  
  Update the chart dependencies in order to bitnami/postgresql chart be also deployed

### Deploy commands

- `cd <path_to_project>/.helm/allure-server`  
  Go to chart directory
- `helm install allure-server . -n allure-production`  
  Install chart

### Access Allure-Server

- Access via:
  ```
  export POD_NAME=$(kubectl get pods --namespace allure-production -l "app.kubernetes.io/name=allure-server,app.kubernetes.io/instance=allure" -o jsonpath="{.items[0].metadata.name}")
  
  kubectl port-forward --namespace allure-production service/allure-server-service 8080:8080
  
  # Access http://127.0.0.1:8080 on your browser
  ```
- Or access via `ingress.host` (*if ingress.enabled: true*)