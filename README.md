# Let's investigate the yaml files a little bit
code .

# show AWS Console Fargate cluster

# create the CloudWatch Log group
aws logs create-log-group --log-group-name /ecs/virtual-kubelet-logs --region us-west-2

# show virtual-kubelet deployment and apply it
kubectl apply -f virtual-kubelet/

# check the pod and node
kubectl get pod
kubectl get nodes

# in a new tab turn on logs of virtual kubelet pod
kubectl -n default logs svc/virtual-kubelet -f --tail 10

# create a NS
kubectl create ns openshift-anwendertreffen

# switch to namespace
kubectl config set-context $(kubectl config current-context) --namespace=openshift-anwendertreffen

# Deploy the nginx example on the cluster
kubectl apply -f nginx-example-service.yaml -f nginx-example.yaml
watch kubectl get pod

# show the AWS Console with Fargate Cluster tasks

# explore the nginx service Load Balancer

# explore the logs of virtual-kubelet

# scale the deployment and watch the pods coming up
kubectl scale deployment nginx-deployment --replicas=15
watch kubectl get pod

# check the AWS Console with Fargate Cluster tasks again

# throw some load on to the service
ab -n 1000 -c 100 <LOAD BALANCER PUBLIC DNS>

# explore the logs of virtual-kubelet



