# kind
Kubernets study based on Kind

First one:

- Create kind Cluster. In this example, we have one ``control-plane`` and two ``worker nodes``

To create cluster:

```bash
kind create cluster --config config.yml --name kind-k8s-cluster
```

- After this, create a ``ingress`` based on file:

https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml

But, if you make kind cluster with more 1 node (In this case, 1 control-plane and 2 worker nodes) you must ensure that your ingress-controller is deployed on the same node where you have configured a PortMapping.

For this, you can download yaml file (wget https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml) and change one sentence in a file.

In a config for ``deployment`` you must add ``ingress-ready: "true"`` sentence:

```yml
      nodeSelector:
        ingress-ready: "true"
        kubernetes.io/os: linux
```