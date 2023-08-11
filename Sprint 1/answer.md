# Sprint 1
TODO: Student to complete code and comments in the sections below.

## Install Kubernetes node 1

- Customized kubeadm-config.yaml:
kind: InitConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
bootstrapTokens:
- token: ipmycx.ku9jvun6f34lo5aq
nodeRegistration:
  ignorePreflightErrors:
  - NumCPU
---
kind: JoinConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
discovery:
  bootstrapToken:
    apiServerEndpoint: hol11:6443
    token: ipmycx.ku9jvun6f34lo5aq
    unsafeSkipCAVerification: true
nodeRegistration:
  ignorePreflightErrors:
  - NumCPU
---
kind: KubeletConfiguration
apiVersion: kubelet.config.k8s.io/v1beta1
failSwapOn: false
---
kind: ClusterConfiguration
apiVersion: kubeadm.k8s.io/v1beta3
apiServer:
  certSANs:
  - 35.87.153.76






$ kubectl get node
NAME    STATUS   ROLES           AGE   VERSION
hol11   Ready    control-plane   19m   v1.27.4

$ kubectl get namespaces --show-labels -w
NAME              STATUS   AGE   LABELS
default           Active   20m   kubernetes.io/metadata.name=default
kube-node-lease   Active   20m   kubernetes.io/metadata.name=kube-node-lease
kube-public       Active   20m   kubernetes.io/metadata.name=kube-public
kube-system       Active   20m   kubernetes.io/metadata.name=kube-system
