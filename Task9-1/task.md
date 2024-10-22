Create a deployment and perform rollback.

Name: nginx
Using container nginx with version 1.11-alpine
The deployment should contain 3 replicas
Next, deploy the app with new version 1.13-alpine by performing a rolling update and record that update.
Finally, rollback that update to the previous version 1.11-alpine 


## This is my answer 

kubectl create deployment my-dep --image=nginx:1.11-alpine --replicas=3

## kubectl create deployment my-dep --image=nginx:1.13-alpine --replicas=3

kubectl set image deployment/my-dep nginx=nginx:1.13-alpine --record

kubectl rollout status deployment/nginx

kubectl rollout undo deployment/nginx


