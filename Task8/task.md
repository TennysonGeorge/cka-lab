Monitor the logs of pod loggy and extract log lines issue-not-found. Write the output to /tmp/pod.txt.

kubectl get logs ## the correct command is kubectl logs 
Kubectl get pods loggy 
kubectl exec -it loggy 
cp var/logs > /tmp/pod.txt.

## below this the correct command 
kubectl logs loggy | grep "issue-not-found" > /tmp/pod.txt
