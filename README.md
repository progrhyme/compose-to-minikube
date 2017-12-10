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

### (1) By manual configuration

```sh
kubectl apply -f k8s-config.yaml
kubectl apply -f k8s-apps.yaml
kubectl get pods
kubectl exec -it app-XXXXXXXXX-XXXXX rake db:migrate # Specify your pod's name
```

### (2) By [kompose](http://kompose.io)

```sh
kompose up
kubectl get pods
kubectl exec -it rails-XXXXXXXXX-XXXXX rake db:migrate # Specify your pod's name
```
