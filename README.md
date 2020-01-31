# COMMANDES KUBECTL 
## POUR GENERER DES TEMPLATES DE YAML

### Créer un Pod
```
kubectl run toto-pod --image=nginx --restart=Never --labels=app=myapp --port=80 -o yaml --dry-run > my-pod.yaml
```
### Créer un Deployment 
#### Même que commande que pour le pod sauf sans le --restart=Never & ajouter --replicas=3
```
kubectl run toto-deploy --replicas=3 --image=nginx --labels=app=myapp --port=80 -o yaml --dry-run > my-deploy.yaml
```
#### Autre façon de créer un Deployment basique qui ne fonctionne pas avec les options replicas & port
```
kubectl create deployment nginx  --image=nginx:1.7.8  --dry-run -o yaml > deploy.yaml
```
### Exposer un Deployment de type ClusterIP
```
kubectl expose deployment toto-deployment --name=toto-service --port=30080 --target-port=80 --namespace=toto -o yaml --dry-run > my-service.yaml
```
### Exposer un Deployment de type NodePort
#### !!! Allez dans le yaml et modifier targetPort en nodePort !!!
```
kubectl expose deployment toto-deployment --name=toto-service --type=NodePort --port=30080 --namespace=toto -o yaml --dry-run > my-service.yaml
```


### Créer un Secret
#### !!! le mot generic est obligatoire !!!
#### A partir d'un ou plusieurs fichiers
```
kubectl create secret generic toto-secret --from-file=./username.txt --from-file=./password.txt
```
#### A partir d'un littéral
```
kubectl create secret generic toto-secret --from-literal=password=Kub3rn3t3sRul3s!
```
#### A partir d'un fichier de variables d'environnement
```
k create secret generic my-secret --from-env-file=env_file
```
### Créer un ConfigMap
#### !!! Comme le secret sauf sans le mot generic !!!
#### A partir d'un ou plusieurs fichiers
```
kubectl create configmap  toto-configmap --from-file=./username.txt --from-file=./password.txt
```
#### A partir d'un littéral
```
kubectl create configmap  toto-configmap --from-literal=password=Kub3rn3t3sRul3s!
```
### Créer un Job
#### !!!  !!!
```
kubectl run busybox --image=busybox --restart=OnFailure -- /bin/sh -c 'echo hello;sleep 30;echo world'
```
#### OU
```
kubectl create job my-job --image=busybox --dry-run -oyaml -- date 
```
### Créer un CronJob
```
kubectl run mycron --image=busybox --schedule="*/1 * * * *" --restart=OnFailure -o yaml --dry-run -- date
```


# RACCOURCIS POUR VIM

## Pour effacer une ligne
```
dd
```
## Pour annuler la dernière commande
```
u
```
## Pour voir les numéros de ligne
```
: set nu
```

# TIPS DE RECHERCHE SUR KUBERNETES.IO

## Pour les Cronjob: recherchez "cron expression"
