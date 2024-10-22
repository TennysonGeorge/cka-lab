Upgrade master control plane components from version 1.20.0 to only version 1.20.1.
•  Drain the master before start the upgrade and uncordn once the upgrade is completed 
•  Update the kubelet and kubeadm as well


## Below is my answer to this questions

Kubectl cordon control plane 

kubectl drain control plane --ignore-daemonsets --delete-emptydir-data

## the command to upgrade to control plane node goes here 

sudo kubeadm upgrade apply v1.20.1

sudo apt-get install -y kubelet=1.20.1-00 kubeadm=1.20.1-00
sudo apt-mark hold kubelet kubeadm
sudo systemctl daemon-reload
sudo systemctl restart kubelet

Kubectl uncordon control plane 
