# KUBECTL COMMANDS

## Create Pod
```
kubectl run nginx1 --image=nginx --restart=Never --labels=app=myapp --port=80 -o yaml --dry-run > my-pod.yaml
```
## Create Deployment 
### Même que commande que pour le pod sauf sans le --restart=Never & ajouter --replicas=3
```
kubectl run nginx1 --replicas=3 --image=nginx --labels=app=myapp --port=80 -o yaml --dry-run > my-pod.yaml
```
## Expose Deployment ClusterIP
```
kubectl expose deployment pizza-deployment --name=pizza-service --port=30080 --target-port=80 --namespace=pizza
```
## Expose Deployment NodePort
### Allez dans le yaml et modifier targetPort en nodePort
```
kubectl expose deployment pizza-deployment --name=pizza-service --type=NodePort --port=30080 --namespace=pizza > service.yaml
```


## Create Secret
### A partir d'un ou de plusieurs fichiers
```
kubectl create secret generic <secretName> --from-file=./username.txt --from-file=./password.txt
```
### A partir d'un littéral
```
kubectl create secret generic <secretName> --from-literal=password=Kub3rn3t3sRul3s!
```
# VIM SHORTCUTS

## Pour effacer une ligne
```
dd
```
## Pour annuler l'effacement d'une ligne
```
u
```
