Firstly, start minikube:
```
minikube start
```
Secondly, enable ingress add-on
```
minikube addons enable ingress
```

Then start the nginx

```bash
kubectl apply -f nginx-svc.yaml
```

```bash
kubectl apply -f nginx-configmap.yaml
```

```bash
kubectl apply -f nginx-ingress.yaml
```

```bash
kubectl apply -f nginx-dep.yaml
```

Now start up app1

```bash
kubectl apply -f app-1-svc.yaml
```

```bash
kubectl apply -f app-1-ingress.yaml
```

```bash
kubectl apply -f app-1-dep.yaml
```

Now start up app2

```bash
kubectl apply -f app-2-svc.yaml
```

```bash
kubectl apply -f app-2-ingress.yaml
```

```bash
kubectl apply -f app-2-dep.yaml
```

Find out minikube cluster ip
```bash
minikube ip
```

Then take the ip and test the apps
```
$ curl http://192.168.49.2/
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

```
$ curl http://192.168.49.2/app-1
<html>
<head><title>502 Bad Gateway</title></head>
<body>
<center><h1>502 Bad Gateway</h1></center>
<hr><center>nginx</center>
</body>
</html>
```

```
$ curl http://192.168.49.2/app-2
<html>
<head><title>502 Bad Gateway</title></head>
<body>
<center><h1>502 Bad Gateway</h1></center>
<hr><center>nginx</center>
</body>
</html>
```