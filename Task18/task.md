•	Reconfigure the existing deployment front-end:
Add a port specification named http exposing port 80/tcp of the existing container nginx add a selector entry with key foo and value bar 
•	Create a new service named front-end-svc exposing the container port http. Also use the new selector entry foo to select the service's target. 
•	Configure the new service to also expose the individual Pods via a port on the host on which they are scheduled. 





____WORKINPROGESS!!!


## below is my attempt to answer this problem 

kubectl edit deployment front-end


kubectl create deployment front-end --image=nginx --port=80  --dry-run=client -o yaml > front-end1.yaml 

apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: front-end
  name: front-end
spec:
  replicas: 1
  selector:
    matchLabels:
      app: front-end
      foo: bar
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: front-end
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - name: http
          containerPort: 80

## Creating the service named front-end-svc

kubectl create service front-end-svc --tcp=80:8080 -l name=bar 

kubectl expose deployment front-end --name=front-end-svc --port=80 --target-port=http --selector=foo=bar --type=NodePort


