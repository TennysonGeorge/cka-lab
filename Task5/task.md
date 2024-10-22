Create a new nginx Ingress resource as follows: 
o	Name: nginx-ingress
o	Namespace: ingress-ns 
o	Exposing service me.html on path /me.html using service port 8080
o	Exposing service test on path /test using service port 8080 



kubectl create ingress nginx-ingress --namespace=ingress-ns --rule="foo.com/bar=svc1:8080,tls=my-cert"


  kubectl create ingress nginx-ingress --class=default \
  --rule="/me.html=svc:8080" \
  --rule="/test=svc:8080" \
  -o yaml > ingress.yaml 