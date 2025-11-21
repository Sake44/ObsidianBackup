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