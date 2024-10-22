Create a pod named kucc8 with a single app container for each of the following images running inside (there may be between 1 and 4 images specified): nginx + redis + memcached. 


## Below is my answer 

kubectl run kucc8 --image=nginx --image=redis --image=memcached --dry-run=client -o yaml > k8s-exam-task16 

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: kucc8
spec:
  containers:
  - image: nginx
    name: nginx
  - image: memcached
    name: memcached
  - image: redis
    name: redis
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

