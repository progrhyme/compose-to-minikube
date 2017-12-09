# compose-to-minikube

This is a sample Rails application which is run by both
[docker-compose](https://docs.docker.com/compose/) and
[Kubernetes](https://kubernetes.io/).

# Run Application

## docker-compose

```sh
docker-compose up
docker-compose exec rails rake db:migrate
```

## Kubernetes

```sh
kubectl apply -f k8s-config.yaml
kubectl apply -f k8s-apps.yaml
kubectl get pods
kubectl exec -it app-XXXXXXXXX-XXXXX rake db:migrate # Specify your pod's name
```
