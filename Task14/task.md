Check to see how many nodes are ready (not including nodes tainted NoSchedule) and write the number to /path/to/node


## Below is my answer to this problem

kubectl get nodes | grep "ready" > /path/to/node


## imporved solution

kubectl get nodes --no-headers --field-selector=status.conditions[?(@.type=="Ready")].status==True \
  | awk '{print $1}' | xargs -I {} kubectl describe node {} \
  | grep -v 'NoSchedule' | wc -l > /path/to/node
