
###########################################################################
# Use "monitoring" namespace in order to deploy monitoring resources for your cluster
# If it does not exist, prior executing helm, you need to create namespace
###########################################################################

kubectl create namespace monitoring

helm upgrade --install --namespace monitoring monitoring-node-exporter ./charts/node-exporter


helm upgrade --install --namespace monitoring monitoring-kube-state-metrics ./charts/kube-state-metrics


helm upgrade --install --namespace monitoring monitoring-prometheus ./charts/prometheus


##########################
# Uninstalling 
##########################

helm uninstall monitoring-node-exporter --namespace monitoring
helm uninstall monitoring-prometheus --namespace monitoring
helm uninstall monitoring-kube-state-metrics --namespace monitoring


##########################
#Deleting namespaces 
##########################

kubectl delete namespace monitoring