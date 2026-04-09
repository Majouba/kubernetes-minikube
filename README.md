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