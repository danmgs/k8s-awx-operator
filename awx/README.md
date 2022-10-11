https://operatorhub.io/


# Installer une instance de awx à partir de awx-operator (pré-requis), dans le namespace awx
cd "C:\Apps\k8s-training\k8s-awx-operator\awx\helm"
helm install awx-operator-instance --namespace awx .

# Voir les releases helm dans le namespace awx
helm list -n awx

# Observer les pod dans le namespace awx
kubectl get po -n awx --watch

# Supprimer l'instance qu'on a appelé "awx" qui est de type AWX
# kubectl delete <CR_type> <releaseName>
kubectl delete AWX awx-operator-instance

# Supprimer l'instance de l'opérator
helm uninstall awx-operator-instance -n awx

# Montrer les secrets

kubectl get secret awx-operator-instance-admin-password -n awx -o json
kubectl get secret awx-operator-instance-admin-password -n awx -o json "{.data.password }" | base64 --decode

# Voir les endpoints des services
kubectl get endpoints -n awx

# modifier le yaml et upgrader le helm chart à la version++
 helm upgrade awx-operator-instance --namespace awx .


# Commandes diverses
kubectl get po awx-operator-instance-76c8c9b5ff-8bqns -n awx -o yaml
kubectl describe po awx-operator-instance-76c8c9b5ff-8bqns -n awx

kubectl describe po awx-operator-instance-76c8c9b5ff-bkjl2 -n awx | grep -i ip
kubectl get endpoints -n awx

kubectl  describe svc awx-operator-instance-service -n awx
kubectl get svc awx-operator-instance-service -n awx -o yaml

kubectl get events

# Liens utiles

https://github.com/kubernetes/kubernetes/issues/107170

https://stackoverflow.com/questions/52199737/minikube-default-cpu-memory