Set the node labelled with name:node-01 as unavailable and reschedule all the pods running on it.


## Below is my answer

kubectl get node -l name=node-01

kubectl cordon node-01

kubectl drain node-01 --ignore-daemonsets --delete-emptydir-data


kubectl uncordon node-01


