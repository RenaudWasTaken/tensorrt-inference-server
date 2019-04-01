# NVIDIA Inference Server Helm Chart

Simple helm chart for installing the NVIDIA Inference Server.

# Quickstart

This guide assumes you already have a functional Kubernetes cluster.
A later section in this guide goes over installing helm.
Setting up the model repository is also detailed later in this guide.

To deploy the inference server:
```shell
$ git clone https://gitlab-master.nvidia.com/rgaubert/nvidia-inference-server.git
$ helm install nvidia-inference-server
```

In the future the user experience might be (the first two steps might even be unecessary):
```shell
$ helm repo add gpu-helm-charts https://nvidia.github.io/tensorrt-inference-server/helm-charts
$ helm repo update
$ helm install nvidia-inference-server
```

# Cleanup

If you want to cleanup the inference server:
```
$ helm list
NAME            REVISION        UPDATED                         STATUS          CHART                           APP VERSION     NAMESPACE
wobbly-coral    1               Wed Feb 27 22:16:55 2019        DEPLOYED        nvidia-inference-server-1.0.0   1.0             default

$ helm delete wobbly-coral
```

# Install helm
You'll find the official helm install guide at this url: [https://github.com/helm/helm/blob/master/docs/install.md](https://github.com/helm/helm/blob/master/docs/install.md)

The following steps will give you a quick and dirty setup:
```
$ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | bash
$ kubectl create serviceaccount -n kube-system tiller
serviceaccount/tiller created
$ kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
$ helm init --service-account tiller --wait
```
