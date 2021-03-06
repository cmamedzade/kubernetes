# classicToTyped
kubectl create -f fromfile.yaml   --creates resource based on file content
kubectl replace -f fromfile.yaml  --changes resource based on file content
kubectl get replicationcontrollers
kubectl get pods
kubectl describe pod <podname>
kubectl get deployments
kubectl get all
kubectl logs my-pod
kubectl logs -f my-pod 
kubectl delete --all deployment --deletes all deployments, controllers, pods

kubectl run transaction --image=cassandra   // create pod
kubectl create -f deployment.yaml --namespace=dev   --creates deployment in the dev namespace

kubectl config set-context $(kubectl config current-context) --namespace=prod  --permenantly directs to dev
kubectl get pods --all-namespaces

kubectl create -f deplyoments.yaml --dry-run=client  --shows only output does not creat resources
kubectl create -f deplyoments.yaml -o yaml           --shows resource output as yaml file

kubectl create deployment --image=nginx nginx
kubectl create deployment --image=nginx nginx --dry-run -o yaml
kubectl create deployment nginx --image=nginx --replicas=4
kubectl scale deployment nginx --replicas=4
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml

kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml

docker build -t getting-started .  --creates docker image from docker file
docker build -f /home/ceyhun/Documents/kubernates/cassandra/DifferentDockerFile .
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)

sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk

# Docker images creation
RUN add-apt-repository ppa:openjdk-r/ppa
RUN apt-get update 
RUN apt install -y openjdk-11-jdk

docker run ubuntu sleep 5   -- container remain till end of timeout
kubectl get pod webapp -o yaml > my-new-pod.yaml
kubectl edit deployment my-deployment
kubectl get pods --output=wide

kubectl get cm  --displays config map
kubectl create cm config --from-literal=MESSAGE="hello,world"
kubectl config get-contexts  --get current namespace

docker exec -it 32a346228c98 /bin/bash

## taint
kubectl get serviceaccount
kubectl describe node minikube | grep -i taint
kubectl describe node minikube | grep -i taint
kubectl run newabs --image=cassanra --restart=Never --dry-run=client -o yaml > newabs.yaml     --create yaml file
kubectl explain pod --recursive | less
kubectl explain pod --recursive | grep -A5 tolerations      --prints toleration code block
kubectl apply -f newabs.yaml
kubectl get pods -o wide
kubectl taint node minikube color=grey:NoSchedule    --taint
kubectl taint node minikube color=grey:NoSchedule-   --untaint
########
# lable node
kubectl label node minikube size=large
##
NodeAffinity
kubectl get nodes minikube --show-labels
#########
kubectl scale deployment transaction --replicas=2


minikube addons enable metrics-server

kubectl top node
watch "kubectl top node"

kubectl get pods --show-labels
kubectl get pods -l app=prod
kubectl get pods -l app=prod --no-headers | wc -l
kubectl get all -l app=prod
kubectl get all -l app=prod --no-headers | wc -l

kubectl create -f yamlfile --record   --to record change commands
kubectl rollout status deployment/transaction     --rollouts deployments
kubectl rollout history deployment/transaction
kubectl rollout history deployment/nginx --revision=1
kubectl set image deployment nginx nginx=nginx:1.17 --record
kubectl rollout history deployment nginx
kubectl edit deployments. nginx --record  or open deployment file and edit then apply -f
kubectl apply -f filename --record=true
kubectl rollout history deployment nginx
kubectl rollout undo deployment nginx
kubectl rollout history deployment/nginx --revision=version-number  --describes version