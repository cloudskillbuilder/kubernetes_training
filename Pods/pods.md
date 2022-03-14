# pods
Kubernetes Training

You can find all information regarding Pods Onject for Kubernetes


$ kubectl run "pod_name" --image="image_name" --restart=Never

Example: kubectl run cloudskillbuilderpods --image=nginx --restart=Never


$ kubectl describe "obje_type" "obje_name"

Example Command: kubectl describe pods cloudskillbuilderpods

To see pods logs. (-f tail method)

$ kubectl logs "cloudskillbuilderpods"

Example: kubectl logs cloudskillbuilderpods
Example: kubectl logs -f cloudskillbuilderpods

How to run command inside pods (If you have multiple container inside pods, please use -c "container_name" )

$ kubectl exec "pod_name" -- "command"

Example: kubectl exec cloudskillbuilderpods -- printenv
Example: kubectl exec cloudskillbuilderpods -c container_name --printenv


$ kubectl exec -it "pod_name" -- "shell_command"

Example: kubectl exec -it cloudskillbuilderpods -- /bin/sh
Example: kubectl exec -it cloudskillbuilderpods -c container_name -- /bin/sh

to delete a object in K8S

$ kubectl delete "object_type" "object_name"

Example: kubectl delete pods cloudskillbuilderpods


$ kubectl apply -f "deploy.yaml"

Example: kubectl apply -f ./deploy.yaml


Adding Label and port 

$ kubectl run "pod_name" --image="image_name" --port="port_number" --labels="value" --restart=Never

Example: kubectl run cloudskillbuilderpods --image=nginx --port=80 --labels="app=front-end,team=developer" --restart=Never

How to open K8s object using text editor & Edit

$ kubectl edit "object_type" "object_name"

Example: kubectl edit pods cloudskillbuilderpods

Example: kubectl get pods -w

Port Tunneling
Example: kubectl port-forward pod/multicontainer 8080:80
