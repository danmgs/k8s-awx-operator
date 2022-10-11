
# Installer l'operator awx-operator, dans le namespace awx
cd "C:\Apps\k8s-training\k8s-awx-operator\awx-operator\helm"
# kubectl create namespace awx no need anymore with below command
helm install awx-operator --create-namespace -n awx .

# Voir les releases helm dans le namespace awx
helm list -n awx

# Montrer la CustomResource (CR) de type mariadb
kubectl get AWX -n awx

# Montrer les pods liés au setup de l'opérator
kubectl get po -n awx --watch

# Supprimer l'opérator
helm uninstall awx-operator -n awx

# Commandes complémentaires
kubectl get crd

kubectl delete crd awxbackups.awx.ansible.com
  customresourcedefinition.apiextensions.k8s.io "awxbackups.awx.ansible.com" deleted
kubectl delete crd awxrestores.awx.ansible.com
  customresourcedefinition.apiextensions.k8s.io "awxrestores.awx.ansible.com" deleted
kubectl delete crd awxs.awx.ansible.com
  customresourcedefinition.apiextensions.k8s.io "awxs.awx.ansible.com" deleted



kubectl get ClusterRole -n awx

kubectl delete clusterrole awx-operator-metrics-reader
  clusterrole.rbac.authorization.k8s.io "awx-operator-metrics-reader" deleted
kubectl delete clusterrole awx-operator-proxy-role
  clusterrole.rbac.authorization.k8s.io "awx-operator-proxy-role" deleted


kubectl get ClusterRoleBinding

kubectl delete ClusterRoleBinding awx-operator-proxy-rolebinding