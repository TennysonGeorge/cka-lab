*Create a service account my-sa in new namespace my-ns. *

*Create a cluster role with the name new-cluster-role and ensure the role only can create and list below resources. *

•  DaemonSets 
•  Deployments
•  Replicaset 
•  Pods

Ensure only the newly created service account can use the role and it is effective with the name space my-ns.


## Below is my answer

kubectl create ns my-ns

---

apiVersion: v1
kind: ServiceAccount
metadata:
  creationTimestamp: null
  name: my-sa
  namespace: my-ns


---

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  creationTimestamp: null
  name: new-cluster-role
rules:
- apiGroups:
  - ""
  resources:
  - pods
  verbs:
  - create
  - list
- apiGroups:
  - apps
  resources:
  - daemonsets
  - deployments
  - replicasets
  verbs:
  - create
  - list

kubectl create clusterrole new-cluster-role --verb=create,list --resource=daemonsets,deployments,replicaset,pods -n my-ns --dry-run=client -o yaml > new-cluster-role.yml

kubectl create clusterrolebinding new-cluster-role-binding --clusterrole=new-cluster-role --serviceaccount=default:my-sa -n my-ns --dry-run=client -o yaml > clusterrolebinding.yml

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  creationTimestamp: null
  name: new-cluster-role-binding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: new-cluster-role
subjects:
- kind: ServiceAccount
  name: my-sa
  namespace: default



# Apply the ClusterRole and RoleBinding
kubectl apply -f new-cluster-role.yml
kubectl apply -f bind-my-sa-to-new-cluster-role.yml

