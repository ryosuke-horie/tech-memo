
[Windows 11 に Hyper-V 機能をインストールする方法](https://qiita.com/mmake/items/cd96a0c59226e8460af6)
- この記事をもとにしてHyper-Vを用意する
- 別記事も使って調べるとHomeエディションでは有効化できないみたい

## 面倒くさいからWSL2でminikubeを試す
https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download
```
https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download
```

### クラスタの起動
```
 minikube start
😄  minikube v1.33.1 on Ubuntu 22.04 (amd64)
✨  Automatically selected the docker driver. Other choices: none, ssh
📌  Using Docker driver with root privileges
❗  For an improved experience it's recommended to use Docker Engine instead of Docker Desktop.
Docker Engine installation instructions: https://docs.docker.com/engine/install/#server
👍  Starting "minikube" primary control-plane node in "minikube" cluster
🚜  Pulling base image v0.0.44 ...
💾  Downloading Kubernetes v1.30.0 preload ...
    > preloaded-images-k8s-v18-v1...:  342.90 MiB / 342.90 MiB  100.00% 22.48 M
    > gcr.io/k8s-minikube/kicbase...:  481.58 MiB / 481.58 MiB  100.00% 23.00 M
🔥  Creating docker container (CPUs=2, Memory=3900MB) ...
🐳  Preparing Kubernetes v1.30.0 on Docker 26.1.1 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: default-storageclass, storage-provisioner
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

### kubectlのダウンロード
```shell
minikube kubectl -- get po -A
    > kubectl.sha256:  64 B / 64 B [-------------------------] 100.00% ? p/s 0s
    > kubectl:  49.07 MiB / 49.07 MiB [------------] 100.00% 30.61 MiB p/s 1.8s
NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-7db6d8ff4d-xxqhs           1/1     Running   0             33s
kube-system   etcd-minikube                      1/1     Running   0             47s
kube-system   kube-apiserver-minikube            1/1     Running   0             47s
kube-system   kube-controller-manager-minikube   1/1     Running   0             48s
kube-system   kube-proxy-kdzvh                   1/1     Running   0             33s
kube-system   kube-scheduler-minikube            1/1     Running   0             47s
kube-system   storage-provisioner                1/1     Running   1 (11s ago)   46s

# シェル設定でminikubeを省略する設定
alias kubectl="minikube kubectl --"

# localhostでダッシュボードをかくｎ
```