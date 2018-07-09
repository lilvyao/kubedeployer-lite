![Kubernetes Logo](https://raw.githubusercontent.com/kubernetes-incubator/kubespray/master/docs/img/kubernetes-logo.png)

KubeDeployer - Lite
======================
An Ansible Playbook which deploys a **single** node Kubernetes Cluster in **VShere VM pool**. 

Maintainer
------
Leo Li

Quick Start
------
#### Before start: 
1. Make sure [git](https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/) has been correctly installed on the environment;
2. Make sure [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) has been correctly installed on the environment;
3. You may need to check with IT admin see what subnet addresses (192.168.x.x/xx) can be used.

### Deploy single node Kubernetes cluster:
1. Clone this Ansible Playbook on your laptop or direclty on the target machine (replace ID): 
```
git clone http://<ID>@https://github.com/lilvyao/kubedeployer-solo.git
```
2. Update ***kubedeployer-solo/inventory/host*** file:
```
#Node

[node]
<NODE_TO_DEPLOY>         ----> replace this line by your VM hostname
```
3. Update ***kubedeployer-solo/group_vars/all*** file:
```
# K8s pod subnet
POD_SUBNET_CIDR: 192.168.x.x/xx     ----> replace the subnet/mask address by your pod subnet CIDR

# K8s service subnet
SERVICE_SUBNET_CIDR: 192.168.x.x/xx     ----> replace the subnet/mask address by your service subnet CIDR

# K8s API Server advertise address
APISERVER_ADVERTISE_ADDRESS: 0.0.0.0
```
4. Run the playbook:
```
ansible-playbook site.yml -i inventory/hosts
```

Verify you deployment
-------------

You can verify your Kubernetes cluster status by issuing the following command for verification:
```
kubectl get nodes
```

You can also follow [this](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#creating-a-deployment) 
tutorial to try deploying your first application to verify your Kubernetes environment.
