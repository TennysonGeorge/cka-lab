A Kubernetes worker node, labelled with name "node-01" is in state NotReady . Investigate why this is the case, and perform any appropriate steps to bring the node to a Ready state, ensuring that any changes are made permanent.

```
$ kubectl get nodes
kubectl describe node-01
$ ssh node-01
$ sudo -i
$ systemctl status kubelet ## checking the kubelet agent on the worker node 
$ systemctl start kubelet ## starting the kubelet on the worker node
$ systemctl enable kubelet 
```