# Kubernetes 学习文档

## 简介

Kubernetes（简称 K8s）是一个开源的容器编排引擎，用于自动化容器化应用程序的部署、扩展和管理。它提供了一种在集群中运行和管理容器化应用程序的平台。

## 基本概念

### 1. Pod

Pod 是 Kubernetes 中最小的部署单元，它可以包含一个或多个容器。Pod 内的容器共享网络和存储，并且经常一起部署和调度。

### 2. Deployment

Deployment 是一种 Kubernetes 资源，用于定义和管理 Pod 的部署。它提供了声明式的方法来创建和更新 Pod，使得应用程序的部署更加容易和可靠。

### 3. Service

Service 是一种抽象，用于定义一组 Pod 的访问方式。它可以将一组具有相同标签的 Pod 组合成一个单一的网络端点，并为它们提供稳定的访问地址。

### 4. Namespace

Namespace 是 Kubernetes 中用于隔离和组织集群资源的逻辑分区。它可以帮助团队在共享集群的情况下对资源进行隔离和管理。

## 常用操作

### 1. 创建一个 Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx:latest
```

### 2. 创建一个 Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
```

### 3. 创建一个 Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

## 学习资源

1. [Kubernetes 官方文档](https://kubernetes.io/docs/)
2. [Kubernetes in Action](https://www.manning.com/books/kubernetes-in-action)
3. [Kubernetes 教程 - Runoob](https://www.runoob.com/kubernetes/kubernetes-tutorial.html)
4. [Kubernetes Handbook](https://jimmysong.io/kubernetes-handbook/)
5. [Kubernetes By Example](https://kubernetesbyexample.com/)
