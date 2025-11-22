Static Provisioning is a pivotal method in Kubernetes storage management where a cluster administrator pre-creates storage volumes and makes them available for use in the cluster. This approach allows for precise control over the storage's specifications, such as its capacity, access modes, and reclaim policy, ensuring that the storage is perfectly tailored to the needs of the applications.

### Create a Persistent Volume
1. Kick off our lab session by creating a Persistent Volume (PV) with NFS (Network File System) as the underlying storage. You can find all the code for this lab inside the **kubernetes-storage-and-scheduling** directory.
```
cd ~/kubernetes-storage-and-scheduling/challenges/02/
kubectl apply -f nfs.pv.yml
```
This PV will be configured with the ReadWriteMany access mode, allowing multiple pods to read and write simultaneously, and the Retain reclaim policy keeps the data on the volume even after a PVC no longer uses it.

The following message will be displayed:
```
persistentvolume/pv-nfs-data created
```
2. After creating the PV, it's crucial to verify its attributes to ensure it meets your specifications.
```
kubectl get PersistentVolume pv-nfs-data
```

![[Pasted image 20251121151938.png]]
This command displays the details of **pv-nfs-data**, including its status, access modes, and reclaim policy. The reclaim policy should be set to **Retain**, ensuring data persistence beyond the PVC's lifecycle.
3. To gain deeper insights inot your PV's setup, use the describe command:
```
kubectl describe PersistentVolume pv-nfs-data
```
![[Pasted image 20251121152830.png]]
This will provide you with a comprehensive overview of the PV's configuration, including its Capacity, Access Modes, the Reclaim Policy, and a **Status** of **Available**, allowing you to confirm it's configured as intended.
### Create a persistent volume chain
Next, bind your PV to a specific application by creating a Persistent Volume Claim (PVC):

```
kubectl apply -f nfs.pvc.yaml
```
This PVC requests storage from the PV, matching the specified size and access modes, and resulting in the following output:

```
persistentvolumeclaim/pvc-nfs-data created
```

Once the PVC is created, it's essential to check the binding status to ensure the PV and PVC are correctly linked:
```
kubectl get PersistentVolume
```
You should see the STATUS of your PV change to Bound, which indicates a successful claim.

You can further see the STATUS with the kubectl get PersistentVolumeClaim and describe commands:
```
kubectl get PersistentVolumeClaim pvc-nfs-data
```
![[Pasted image 20251121192011.png]]
```
kubectl describe PersistentVolumeClaim pvc-nfs-data
```
![[Pasted image 20251121192035.png]]
### Deploy your application
With your PV and PVC defined, apply the deployment **nfs.nginx.yaml** . This deployment-mounts the NFS-backed volume into your [NGINX](https://www.nginx.com/) pods, making the NFS-shared data available at a specific path inside your containers.
1. Apply the **nfs.nginx.yaml** file to create a deployment that includes a pod configured with a Persistent Volume Claim (PVC) on **pvc-nfs-data**, along with a corresponding service:
```
kubectl apply -f nfs.nginx.yaml
```

The output looks like this:

```
deployment.apps/nginx-nfs-deployment created
service/nginx-nfs-service created
```
2. Retrieve the service IP to access your application:
```
SERVICEIP=$(kubectl get service | grep nginx-nfs-service | awk '{ print $3 }')
echo $SERVICEIP
```
![[Pasted image 20251122112701.png]]
3. Ensure your pod is in a **Running** state before proceeding, confirming the operational status of your deployment.
```
kubectl get pods
```
#### Validate Deployment and Storage Access
Verify that your deployment is running and that the NFS volume is correctly mounted
1. Utilize **curl** to fetch content from your deployed application, demonstrating live access to the NFS-stored data:
```
curl http://$SERVICEIP/web-app/demo.html
```
2. Determine which pod is utilizing the NFS-mounted storage by describing the PVC:
```
kubectl describe PersistentVolumeClaim pvc-nfs-data
```

![[Pasted image 20251122112841.png]]
Note the **Used by** value, which is the _pod name_, as you'll use it in the next task _and later in the lab._
3. Explore the pod file system, diving into the pod's container to explore the mounted NFS volume, validating the presence and content of your demo file, replacing podname with the nginx-nfs-deployment prefixed value you noted in the last task.
```
kubectl exec -it <<pod name>> -- /bin/bash 
ls /usr/share/nginx/html/web-app 
cat /usr/share/nginx/html/web-app/demo.html 
exit
```

![[Pasted image 20251122113125.png]]
4. As you're done with the challenge, you can clean up the resources created. These commands fully reuse the storage and delete the PV, PVC, and deployment.
```
kubectl delete deployment nginx-nfs-deployment 
kubectl delete pvc pvc-nfs-data 
kubectl delete pv pv-nfs-data
```
### StorageClasses for Dynamic Provisioning
The cluster supports dynamic storage provisioning out of the box. It uses the **nfs.csi.k8s.io** provisioner, a Kubernetes CSI (Container Storage Interface) plugin that provides automated provisioning, mounting, and management of NFS (Network File System) volumes in Kubernetes clusters.
1. Enter into the challenge **03** folder.
```
cd ~/kubernetes-storage-and-scheduling/challenges/03/
```
2. Create the StorageClass nfs-csi:
```
kubectl apply -f storageclass.yaml
```
This storage class, via the contents of the **yaml** file, specifies the NFS parameters: the server, **nfs-server**, and share, **/export/volumes/pod**. The Kubernetes cluster provides the ability to mount this filesystem path itself.
3. Explore available StorageClass:
```
kubectl get StorageClass
```
### Use nfs-csi in an NGINX Deployment
1. Deploy the NGINX deployment with the nfs-csi StorageClass:
```
kubectl apply -f nfs-csi.nginx.yaml
```
