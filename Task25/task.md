Creae a persistent volume with name my-vol of capacity 10Gi and access mode ReadWriteOnce. The type of volume is hostPath and its location is /test/path


## below is my answer 

apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-vol
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /test/path

---

apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-vol
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /test/path


    