Download helm installation scripts:
$curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
provide permission
$sudo chmod 700 get_helm.sh
Execute script to install
$sudo ./get_helm.sh 
$helm version --client(to get helm version)
---

Create a namespace to deploy your prometheus stack
$kubectl create ns prometheus
$kubectl get ns
$kubectl config set-context --current --namespace=prometheus
$helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
$helm repo add stable https://kubernetes-charts.storage.googleapis.com/
$helm repo update
$helm install prometheus prometheus-community/kube-prometheus-stack


$kubectl get servicemonitor
$kubectl get svc 
#locate prometheus-grafana and prometheus-kube-prometheus-prometheus
$kubectl edit svc prometheus-grafana
(change service type from ClusterIP to LoadBalancer)

$kubectl edit svc prometheus-kube-prometheus-prometheus
(change service type from ClusterIP to LoadBalancer)

$kubectl get svc 
Get the LoadBalancer and access grafana on port 80 
Access prometheus on port 9090
---

How to Create a Kubernetes Monitoring Dashboard?
For creating a dashboard to monitor the cluster:
Click the '+' button on the left panel and select ‘Import’.
Enter 12740 dashboard id under Grafana.com Dashboard.
Click ‘Load’.
Select ‘Prometheus’ as the endpoint under prometheus data sources drop down.
Click ‘Import’.
---

How to create other dashboards:

How to Create Kubernetes Cluster Monitoring Dashboard?
For creating a dashboard to monitor the cluster:
Click the '+' button on the left panel and select ‘Import’.
Enter 3119 dashboard id under Grafana.com Dashboard.
Click ‘Load’.
Select ‘Prometheus’ as the endpoint under prometheus data sources drop down.
Click ‘Import’.
This will show monitoring dashboard for all cluster nodes
---

Create POD Monitoring Dashboard
For creating a dashboard to monitor the cluster:
Click the '+' button on the left panel and select ‘Import’.
Enter 6417 dashboard id under Grafana.com Dashboard.
Click ‘Load’.
Select ‘Prometheus’ as the endpoint under prometheus data sources drop down.
Click ‘Import’
---

============
You can also deploy nginx in that namespace.
$kubectl create ns prometheus
$kubectl get ns
$kubectl run nginx --image=nginx --namespace=prometheus
Also deploy etechapp this is the yaml --> https://github.com/etechDevops/etech-legacy-appv1
Footer
© 2022 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
