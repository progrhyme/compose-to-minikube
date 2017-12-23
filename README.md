# compose-to-minikube

This is a sample Rails application which is run by both
[docker-compose](https://docs.docker.com/compose/) and
[Kubernetes](https://kubernetes.io/).

# Prerequisites

- [Docker](https://www.docker.com/)
- Kubernetes cluster. [Minikube](https://github.com/kubernetes/minikube) is handy for this sample.
- [kubectl](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-options/)
- Optional: [kompose](http://kompose.io)

# Prepare Local Registry

Use https://hub.docker.com/_/registry/ like following command:

```sh
docker run -d -p 5000:5000 \
  -v ~/.dockerregistry:/var/lib/registry \
  --restart always \
  --name registry \
  registry:2
```

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

### (2) By kompose

```sh
kompose up
kubectl get pods
kubectl exec -it rails-XXXXXXXXX-XXXXX rake db:migrate # Specify your pod's name
```

# See Also

- [Docker ComposeからMinikube + Komposeに移行してみよう - Qiita](https://qiita.com/progrhyme/items/116948c9fef37f3e995b)

# License

The MIT License (MIT)
