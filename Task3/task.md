From the pod label name=cpu-burner, find pods running high CPU workloads and Write the name of the pod consuming most CPU to the file /tmp/cpu.txt.

## Below is my answer 

kubectl top pod -l name=cpu-burner --no-headers | sort -k 2 -nr | head -n 1 | awk '{print $1}' > /tmp/cpu.txt
