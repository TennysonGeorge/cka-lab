*Create a PVC my-pvc with the capacity 10Gi and storage class k8s-csi-plugin. *

•	Assign the PVC to the pod named nginx-pod with image nginx and mount to path /usr/share/html
•	Ensure the pod claims the volume as ReadWriteMany access mode 
•	Use kubectl patch or kubectl edit to update the capacity of the PVC as 70Gi to record the change.


## Below is my answer

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 10Gi
  storageClassName: k8s-csi-plugin

---

apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx-pod
      image: nginx
      volumeMounts:
      - mountPath: "/usr/share/html"
        name: my-pvc
  volumes:
    - name: my-pvc
      persistentVolumeClaim:
