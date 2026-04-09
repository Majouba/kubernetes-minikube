# TP Kubernetes - Minikube

## Objectif
Déploiement d'une application Java sur un cluster Kubernetes local avec Minikube. Le code source a été modifié pour afficher un message personnalisé.

## Mon image Docker Hub
L'image finale de mon application est disponible ici : `majouba/myservice:4`

## Commandes principales utilisées

### 1. Création et publication de l'image Docker
`docker build -t myservice .`
`docker tag myservice majouba/myservice:4`
`docker login`
`docker push majouba/myservice:4`

### 2. Déploiement sur Kubernetes (Minikube)
`kubectl create deployment myservice --image=majouba/myservice:4`

### 3. Exposition du service
`kubectl expose deployment myservice --type=NodePort --port=8080`
`minikube service myservice --url`

### 4. Utilisation des fichiers YAML
Application de la configuration via les fichiers fournis :
`kubectl apply -f myservice-deployment.yml`
`kubectl apply -f myservice-loadbalancing-service.yml`

### 5. Configuration de l'Ingress
Activation de l'Ingress et application des règles de routage :
`minikube addons enable ingress`
`kubectl apply -f ingress.yml`
Accès configuré via le fichier hosts sur `http://myservice.info/`