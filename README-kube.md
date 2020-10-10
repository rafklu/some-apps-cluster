# Tworze rejestr obrazów na minikube

```
> minikube addons configure registry-creds

Do you want to enable AWS Elastic Container Registry? [y/n]: n

Do you want to enable Google Container Registry? [y/n]: n

Do you want to enable Docker Registry? [y/n]: Y
-- Enter docker registry server url: docker-images-registry
-- Enter docker registry username: admin

Do you want to enable Azure Container Registry? [y/n]: n
* registry-creds was successfully configured
```

```
PS C:\Users\rafal\Projects\apps-cluster\some-demo-app1> minikube addons enable registry
* Registry addon on with docker uses 32769 please use that instead of default 5000
* For more information see: https://minikube.sigs.k8s.io/docs/drivers/docker
* Verifying registry addon...
* The 'registry' addon is enabled
```

```
minikube dashboard
```

`http://localhost:5000/v2/_catalog`


kubectl get po -n kube-system

kubectl port-forward --namespace kube-system registry-<SOME_ID> 5000:5000

docker run --rm -it --network=host alpine ash -c "apk add socat && socat TCP-LISTEN:5000,reuseaddr,fork TCP:host.docker.internal:5000"


https://minikube.sigs.k8s.io/docs/handbook/registry/

https://hasura.io/blog/sharing-a-local-registry-for-minikube-37c7240d0615/