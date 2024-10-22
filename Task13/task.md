The node k8s-node is not in ready state. Ssh to the node and troubleshoot the issue, make the changes permanent to avoid the problem in future.

## below is my answer or steps that I would take to slove this problem

kubectl get node 

kubectl describe node k8s-node 

ssh k8s-node 

## After logging into k8s-node, look at kubelet agent to see if it's active 

## Also look at other processes that are need to run k8s, see if those processes are active too 

## If any processes that are need to run k8s are not active you would need to active them 

## this is how I would slove this problem 

systemctl status kubelet

sudo systemctl start kubelet

journalctl -u kubelet -f

