Create a Pod as follows:

Name: jenkins
Using image: jenkins
In a new Kubenetes namespace named tools

## Below is my answer

kubectl create ns tools 

kubectl run jenkins --image=jenkins --namespace=tools --dry-run=client -o yaml > jenkins.yaml 

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: jenkins
  name: jenkins
  namespace: tools
spec:
  containers:
  - image: jenkins
    name: jenkins
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}