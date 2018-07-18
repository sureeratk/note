# kubernates

## what is Kubernates

* Container orchestrator

* Scalability

* pod = group of containers

  

## Kubeernates (19/6/18) 

Src: https://github.com/domecloud/k9s-beer-talk

* **ClusterRole.yaml** - กำหนด role ให้แต่ละ node

* **ServiceAccount.yaml** - กำหนดสิทธิ์ให้ service account

* **Deployment.yaml** - deploy dynamic NFS provisioning 

* **StorageClass.yaml** - deploy storage class]

* **Claim.yaml** - claming tagged storage

* **galera-cluster.yaml** - deploy MySQL 3 replicas

  * galera - cluster control บน MySQL
  * StatefulSet จะรอเวลาเขียนพร้อมกัน
  * Init db-0 เป็น master (มี 0 มาก่อน 1 ถึงจะเกิด)

* **WordPress.yaml** - deploy wordpress -> ได้ port เอาไว้วิ่งเข้า

  

## Architecture

* On-Premise:
  * deploy บน private mode ไม่ต้องดักด้วย load balancer ใช้ proxy node 

* Cloud:

  * pod อยู่ใน layer 2 เดียวกันทั้งหมด 
  * ใช้ load balancer ดัก

* network ของ container performance ไม่ดี เพราะต้อง NAT ก่อน (ต้อง map port กันก่อน port ห้ามชนกัน)

* แต่ kubernates เราสามารถกำหนดให้ pod ใช้ port ซ้ำกันได้ เขียนเหมือนกัน ค่อย map port จากข้างนอกเข้ามา

  * ขึ้นอยู่กับ system ที่ deploy ด้วย

* ตัวอย่างใน wordpress.yaml https://github.com/domecloud/k9s-beer-talk/blob/master/WordPress.yaml

  * targetPort: 80 <- port ของ pod
  * nodePort: 30180 <- external port

## *Tip!* ท่า HA 

* หลัง deploy เสร็จ ก็ snap เลย 
* master กับ node ควรอยู่ใกล้ๆกัน 
* ต่อ node พ่วงเข้า master ผ่าน IP ของ vpn ถ้า master ตาย ก็ชี้ไป master อื่น



*google*

- Split brain
- funnel
- Openresty 



## Launch Single Node Kubernetes Cluster with Minikube

#### Few Concepts

* *deployments* = high-level construct that define application
* *Pods* = instances of container in a deployment
* *Services* = endpoints that export ports to the outside world  

#### Starting Minikube

* install kubectl  `brew install kubernetes-cli` 
  * after install, k8s cluster couldn't be connected. Must install minikube and start it first.
* install minikube `brew cask install minikube`
* checking version `minikube version`
* Start the cluster, by running the *minikube start* command: `minikube start`

### Cluster info

* The cluster can be interacted with using the *kubectl* CLI. This is the main approach used for managing Kubernetes and the applications running on top of the cluster.
* Details of the cluster and it's health status can be discovered via `kubectl cluster-info`
* To view the nodes in the cluster using `kubectl get nodes`
  * If the node is marked as **NotReady** then it is still starting the components.
  * This command shows all nodes that can be used to host our applications.

### Deploy Containers

* Using `kubectl run`, it allows containers to be deployed onto the cluster  

  `kubectl run first-deployment --image=katacoda/docker-http-server --port=80`

* The status of the deployment can be discovered via the running Pods - `kubectl get pods`

* Once the container is running it can be exposed via different networking options, depending on requirements. One possible solution is NodePort, that provides a dynamic port to a container.

  `kubectl expose deployment first-deployment --port=80 --type=NodePort`

* The command below finds the allocated port and executes a HTTP request. The results is the container that processed the request.

```
export PORT=$(kubectl get svc first-deployment -o go-template='{{range.spec.ports}}{{if .nodePort}}{{.nodePort}}{{"\n"}}{{end}}{{end}}')
echo "Accessing host01:$PORT"
curl host01:$PORT
```

* The Kubernetes dashboard allows you to view your applications in a UI. In this deployment, the dashboard has been made available on port *30000*.

## Kubeadm

* The first stage of initialising the cluster is to launch the master node. The master is responsible for running the control plane components, etcd and the API server. Clients will communicate to the API to schedule workloads and manage the state of the cluster.
* The command below will initialise the cluster with a known token to simplify the following steps.

`kubeadm init --token=102952.1a7dd4cc8d1f4cc5 --kubernetes-version $(kubeadm version -o short)`

* To manage the Kubernetes cluster, the client configuration and certificates are required. This configuration is created when *kubeadm* initialises the cluster. The command copies the configuration to the users home directory and sets the environment variable for use with the CLI.

```
sudo cp /etc/kubernetes/admin.conf $HOME/
sudo chown $(id -u):$(id -g) $HOME/admin.conf
export KUBECONFIG=$HOME/admin.conf
```

