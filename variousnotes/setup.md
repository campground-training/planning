# Install Kind and Get your Cluster On

Have Docker installed / running.

Install [Kind](https://kind.sigs.k8s.io/)

Create a file somewhere you can get to it called `kind-config.yaml` with the following content. Save it.


```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: hypertheory
nodes:
- role: control-plane
  kubeadmConfigPatches:
  - |
    kind: InitConfiguration
    nodeRegistration:
      kubeletExtraArgs:
        node-labels: "ingress-ready=true"
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: TCP
```

In the directory with that file, run:

```bash
kind create cluster --config .\kind-config.yaml
```

After it finishes, create a few namespaces:

```bash
kubectl create namespace camping

kubectl create namespace data

kubectl create namespace auth
```
# Admin Tasks

These are tasks just to get things up and running. After these are done, you won't have to do this again unless you delete your local cluster.

## Create the Mongo Database

Switch to the `data` namespace:

```shell
kubectl config set-context --current --namespace=data
```

We will use a Helm Chart to install MongoDb. 

If you haven't previously installed Helm, follow the instructions here [Helm Installation Guide](https://helm.sh/docs/intro/install/).

Add the Bitnami repo:

```shell
helm repo add bitnami https://charts.bitnami.com/bitnami
```

Install the helm chart:

```bash
helm install mongo --set auth.rootPassword="TokyoJoe138!",auth.rootUserName="admin"  bitnami/mongodb
```

Switch back to the `camping` namespace:

```bash
kubectl config set-context --current --namespace=camping
```