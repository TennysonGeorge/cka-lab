Create a Static pod

Name: consul
Using image: consul
In a new Kubenetes namespace named tools


## Below is my answer 

kubectl create ns tools

kubectl run consul --image=consul -n tools --dry-run=client -o yaml > static-pod.yaml

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: consul
  name: consul
  namespace: tools
spec:
  containers:
  - image: consul
    name: consul
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

