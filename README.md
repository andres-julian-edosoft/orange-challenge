# Nivel Docker Jenkins

## 1. Build de docker

```
cd docker
docker build -t jenkins-orange:0.0.2 .
```

## 2. Desplegar k8s
```
kubectl create -f deployment.yaml
kubectl create -f roles.yaml
kubectl create -f rolebindings.yaml
kubectl create -f service.yaml
kubectl create sa jenkins
```

Con el token de la service account `jenkins` generamos un kube-config para nuestro cluster en un fichero llamado `kube-config`
```
kubectl create configmap jenkins-config \
               --from-file=kube-config \
               --from-file=jenkins.yaml
```

## 3. Añadir un nuevo job en jenkins con nuestro repositorio
Crear un nuevo job de tipo _Pipeline_ y seleccionamos _Pipeline Script from SCM_ -> _Git_ -> y escribimos la URL de nuestro repositorio

# Nivel Kubernetes

## Aplicar configuración de terraform
```
cd terraform
terraform apply
```

## Aplicar roles de kubernetes
```
kubectl apply -f kubernetes-dashboard-admin.rbac.yaml
```