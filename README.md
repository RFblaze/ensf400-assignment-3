Firstly, start minikube:
```
minikube start
```

Then start the nginx

```bash
kubectl apply -f nginx-configmap.yaml
```

```bash
kubectl apply -f nginx-ingress.yaml
```

```bash
kubectl apply -f nginx-svc.yaml
```

```bash
kubectl apply -f nginx-dep.yaml
```

Now start up app1

```bash
kubectl apply -f app-1-ingress.yaml
```

```bash
kubectl apply -f app-1-svc.yaml
```

```bash
kubectl apply -f app-1-dep.yaml
```

Now start up app2

```bash
kubectl apply -f app-2-ingress.yaml
```

```bash
kubectl apply -f app-2-svc.yaml
```

```bash
kubectl apply -f app-2-dep.yaml
```

Find out minikube cluster ip
```bash
minikube ip
```

Then take the ip and test the apps
