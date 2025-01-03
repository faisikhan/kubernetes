# Welcome to Kubernetes by DevOps Molvi

This repository will have all the Kubernetes learning material that we'll discuss and learn together on my DevOps Molvi YouTube channel.

By the way, I'll explain Kubernetes here but if you want to watch my Kubernetes Lectures, I'll list them out here:

1. What is Kubernetes- https://youtu.be/iznUPUHChEc
2. What is K8s Used for- https://youtu.be/ma6_i4XMYEc
3. Kubernetes Architecture- https://youtu.be/gSGMD7X0neQ
4. Kubernetes Cluster Deep Dive- https://youtu.be/LgmN3bDITwE
5. Kubernetes Terminology- https://youtu.be/3wC7-cMUYDk
6. How to Install MiniKube- https://youtu.be/DSNEBqLFLrk
7. kubectl commands cheat sheet- https://youtu.be/9ROeiqi3UOQ

# Kubernetes

1. One of the most popular tools for container orchestration.
2. A node means a server in Kubernetes.
3. A cluster means a number of servers coupled together. In Kubernetes, there should be at least 2 nodes in a cluster:

**i.  Master Node**
It is the main node in Kubernetes which does the administration part, it runs **kubeadm**. Kubeadm performs the actions necessary to get a minimum viable cluster up and running quickly. 

**ii. Worker Node**
Worker nodes are servers that run the workloads. Workload means containerized apps running in the production.

## Control Plane

In simple words, the Kubernetes API Server is known as the Control Plane.

## kubelet

It is the main agent used for communication among the nodes, it should be installed on the master and all worker nodes.

## kubeadm

Simply we can say, it is the Kubernetes system administrator. It initializes and administer the cluster.

## kubectl

It is a Kubernetes tool that allows users to run the commands inside the Kubernetes clusters. It communicates with your API server. It can not modify or change the cluster settings. 

## kubernetes-cni

A Kubernetes tool for containers network and data exchange.

1. mkdir $HOME/.kube
2. cp -i k8s-escluster-kubeconfig.yaml $HOME/.kube/config
3. chown $(id -u):$(id -g) $HOME/.kube/config
4. kubectl config view
5. kubectl exec -it elasticsearch-0 -- /bin/bash
6. kubectl delete pods --all -n faisal-elasticsearch --force
7. kubectl delete statefulsets es-cluster --namespace=faisal-elasticsearch
8. kubectl rollout status sts/es-cluster --namespace=faisal-elasticsearch
9. kubectl get pvc -n faisal-elasticsearch
10. kubectl get all --all-namespaces -o yaml > all-resources.yaml
11. kubectl get svc -n faisal-es
12. kubectl describe svc -n faisal-es elasticsearch
13. kubectl apply -f es-main-cluster.yaml -n faisal-es
14. watch kubectl get pods -n faisal-es
15. curl -X GET -k -u elastic:password http://139.59.160.220:30315
16. curl -X DELETE -k -u elastic:password http://139.59.160.220:30315/vfront_bm_escluster_5_*
17. curl -X DELETE -k -u elastic:password http://elasticsearch.tm8.co.uk:30414/vsupm2_escluster_1_url_rewrite_*


![image](https://github.com/faisikhan/kubernetes/assets/21220549/94469fda-160b-4e89-ab9f-fc839112054b)





1. Create a Kubernetes Cluster:

![image](https://user-images.githubusercontent.com/21220549/208852432-6fbd8328-3566-4d20-91ad-786936263c74.png)

If we select Zonal, the control plane [which manages the worker nodes and the Pods in the cluster] and nodes run in a single zone. We can select more replica zones, however, it'll increase the costs. 

Cluster region can not be changed once its created. By default, a regional cluster replicates the control plane and worker nodes across three zones.

A node pools is a group of VMs, servers we can say in the same zone. In a single node pool, the number of nodes can be increased or decreased depending on the workload.

![image](https://user-images.githubusercontent.com/21220549/208858664-b5b5b9c0-50c6-49be-9277-6fa75d172a80.png)

**With the default maximum of 110 Pods per node for Standard clusters, Kubernetes assigns a /24 CIDR block (256 addresses) to each of the nodes.**

![image](https://user-images.githubusercontent.com/21220549/208859009-c2f96986-fe95-4aa6-bce4-c96450da375f.png)

The cluster has been created with 3-nodes in one zone.

![image](https://user-images.githubusercontent.com/21220549/208883877-588d77ff-af39-4d37-8d4e-fd68632ba3a6.png)

We can see that the control plane node and the worker nodes are in the same zone. 

## Attach to a Pod

Go to the kubectl option, you will see the exec ====> nginx-1. We will be connected to the pod.

![image](https://user-images.githubusercontent.com/21220549/208887844-5858d393-cc24-40b7-8f43-53786efef183.png)

## Migrate for Anthos

Moves your current workloads/apps to GCP Kubernetes. The workloads can be on your physical datacenter or other cloud providers like Azure and AWS.

That's how the process should work while we use the migration using Anthos:

![image](https://user-images.githubusercontent.com/21220549/208912157-916b3bc1-efcb-4d5e-b9bb-62921ca8ac8b.png)

I won't be going into the details, but "migctl" command is used to migrate the workloads to Anthos.

![image](https://user-images.githubusercontent.com/21220549/208914811-ffd68784-b73a-46b1-87a7-d852e4600db0.png)

## Kubernetes Manifests

/etc/kubernetes/manifests

-rw------- 1 root root 2392 Dec 19 04:02 etcd.yaml
-rw------- 1 root root 4009 Dec 19 04:02 kube-apiserver.yaml
-rw------- 1 root root 3520 Dec 19 04:02 kube-controller-manager.yaml
-rw------- 1 root root 1440 Dec 19 04:02 kube-scheduler.yaml

1. kubectl config view
2. kubectl get pods
3. kubectl get pods my-pod-name
4. kubectl get nodes  

![image](https://user-images.githubusercontent.com/21220549/208919735-bcd954e3-4c6d-448a-8973-470df9c9f424.png)

1. kubectl create deployment my-deployment --image nginx:latest --port 8088    =============> A new deployment will be created with one replicaset.
2. kubectl get deployment
3. kubectl describe deployment my-deployment

![image](https://user-images.githubusercontent.com/21220549/208929979-579094e5-955c-46bf-8ceb-d8d6b3faadb9.png)

4. kubectl delete deployment my-deployment    =============> It will delete the deployment.
