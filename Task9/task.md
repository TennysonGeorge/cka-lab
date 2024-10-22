Scale the deployment learning to 3 pods

apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: "2024-10-17T21:53:19Z"
  generation: 1
  labels:
    app: my-dep
  name: my-dep
  namespace: kube-system
  resourceVersion: "95171"
  uid: 0b1637d3-897c-4b68-ab6c-e60360dae549
spec:
  progressDeadlineSeconds: 600
  replicas: 3
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: my-dep
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: my-dep
    spec:
      containers:
      - image: busybox
        imagePullPolicy: Always
        name: busybox
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
status: {}