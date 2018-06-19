# kubernates

## what is Kubernates

* Container orchestrator

* Scalability

* pod = group of containers

  

## Kubeernates 

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

