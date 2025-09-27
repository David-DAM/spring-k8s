```bash
docker build -t tu_usuario/spring:1.0
```

```bash
docker push tu_usuario/spring:1.0
```

Sustituir el valor de la imagen de deploy por la tuya propia si lo has subido a DockerHub

Despues proceder a ejecutar los comandos

```bash
kubectl apply -f k8s-deployment.yaml
```

```bash
kubectl apply -f k8s-service.yaml
```

```bash
kubectl apply -f k8s-hpa.yaml
```

Para ver las métricas del servidor usar esto

```bash
kubectl apply -f k8s-metric-service.yaml
```

Ver los pods existentes en el namespace de kube-system

```bash
kubectl get pods -n kube-system -w
```

Ver el uso de recursos de todos los pods

```bash
kubectl top pods
```

Generar carga para aumentar los pods

```bash
kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://spring; done"
```

Ver el estado de los pods con el horizontal pod auto scaler

```bash
kubectl get hpa spring --watch
```