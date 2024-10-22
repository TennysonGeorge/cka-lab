Create a NetworkPolicy named k8s-netpol in the namespace namespace-netpol in a way that pods running on namespace internal on port 9200 can only access pods running in namespace-netpol.
a. Allow the pods to communicate if they are running on port 9200 within the namespace
b. Ensure the NetworkPolicy doesn’t allow other pods that are running other than port 9200 
c. The communication from and to the pods running on port 9200
d. No pods running on port 9200 from other name spaces to allowed 

NB: There will be a default deny all from any namespace netpol will be already present.




____WORKINPROGESS!!!

## This is me trying to get it right with out using chatgpt 

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: k8s-netpol
  namespace: namespace-netpol
spec: 
    policyTypes:
  - Ingress
  - Egress
        ports:
        - protocol: TCP
          port: 9200
       


## This is the correct code below

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: k8s-netpol
  namespace: namespace-netpol
spec:
  podSelector: {}
  policyTypes:
  - Ingress
  - Egress
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          name: internal
    ports:
    - protocol: TCP
      port: 9200
  egress:
  - to:
    - namespaceSelector:
        matchLabels:
          name: internal
    ports:
    - protocol: TCP
      port: 9200
      