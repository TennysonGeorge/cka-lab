Schedule a pod as follows Name :- nginx01 image :- nginx Node Selector :-  name=node.


## below is my answer 

apiVersion: v1
kind: Pod
metadata:
  name: nginx01
spec:
  containers:
  - name: nginx
    image: nginx
  nodeSelector:
    name: node
