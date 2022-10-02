https://operatorhub.io/


helm upgrade --namespace awx --install --force awx-operator-instance .

kubectl get po -n awx --watch

kubectl get secret awx-operator-instance-admin-password -n awx -o json
kubectl get secret awx-operator-instance-admin-password -n awx -o json "{.data.password }" | base64 --decode

kubectl delete AWX awx-demo

