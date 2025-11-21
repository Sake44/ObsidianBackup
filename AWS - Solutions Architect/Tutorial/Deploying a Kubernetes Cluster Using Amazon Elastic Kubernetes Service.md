#### Create an Admin User Role

1. Under **Favorites**, select **IAM**. If you don't see a **Favorites** section, you can enter _IAM_ in the search bar on top of the console and select **IAM** from the search results to access the IAM dashboard.
2. In the lefthand navigation menu, select **Users**.
3. Click the **Add users** button.
4. On the **Specify user details** page, under **User name**, enter _eks-user_.
5. Click the **Next** button.
6. On the **Set permissions** page, under **Permissions options**, select **Attach policies directly**.
7. Under **Permissions policies**, click the checkbox next to **AdminstratorAccess** to grant admin access to the role being created.
8. Click the **Next** button.
9. On the **Review and create** page, click the **Create user** button.
10. Once the user is created, select **eks-user**.
11. Select the **Security credentials** tab.
12. Under **Access keys**, click the **Create access key** button.
13. On the **Access key best practices & alternatives** page, select **Command Line Interface (CLI)**.
14. Click the checkbox next to **I understand the recommendation and want to proceed to create an access key**.
15. Click the **Next** button.
16. On the **Set description tag - optional** page, click the **Create access key** button.
17. Click the **Download .csv file**.
#### Create and Connect to New Instance

1. In the search bar on top, enter _EC2_ and select **EC2** from the search results to access EC2.
2. Select **Instances (running)**.
3. Click the **Launch instance** button.
4. On the **Launch an instance** button, set the following parameters:

	- **Name and tags**: Enter _eks-admin_.
	- **Application and OS Images (Amazon Machine Image)**: Select **Amazon Linux**.
	- **Key pair name**: Select **Create new key pair**.

5. On the **Create key pair** page, under **Key pair name**, enter _eks-key_.
6. Click the **Create key pair** button to create the key pair.
7. Click the **Launch instance** button.
8. Under **Success**, select the link to the instance to see its status. It can take a little while for the instance to launch successfully and for the **Instance state** to change from **Pending** to **Running**.
9. Click the checkbox next to the **eks-admin** instance to select it.
10. Click the **Connect** button.
11. On the **Connect to instance** page, click the **Connect** button.

#### Create Cluster

1. Check the version of the CLI being used to verify that it is AWS CLI 2:
```
aws --version
```
You should see that the version being used is AWS CLI 1.18.

2. Download AWS CLI 2:
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
3. Unzip the downloaded CLI 2 file:
```
unzip awscliv2.zip
```
This can take a few minutes to unzip and create everything needed.
4. Check the location of our AWS files:
```
which aws
```
You should see they are located in usr/bin/aws.

5. Install the AWS CLI into that directory:
```
sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update
```
6. Re-check which version of AWS is being used:
```
aws --version
```
You should see we are now using AWS CLI 2.11.

7. Log into our AWS environment:
```
aws configure
```
8. From the CSV file created earlier, copy and paste the Access Key ID when prompted.
9. From the same CSV file, copy and paste the Secret Access Key when prompted.

When prompted for the default region name, enter us-east-1.
When prompted for the default output format, enter json.

10. Download kubectl:
```
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.30.2/2024-07-12/bin/linux/amd64/kubectl
```
11. Add execution permissions to the file:
```
chmod +x ./kubectl
```
12. Create a new bin directory and copy kubectl to the bin directory and home directory:
```
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```
13. Download eksctl:
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```
This will install the CLI tool you will use to create a cluster on Amazon EKS.

14. Move the files to usr/local/bin:
```
sudo mv /tmp/eksctl /usr/local/bin
```
15. Check the eksctl version:
```
eksctl version
```
This should show the version as 0.133.0.

16. Create the cluster:
```
eksctl create cluster --support-type STANDARD --name myeks --region us-east-1 --zones=us-east-1a,us-east-1b --nodegroup-name eks-workers --node-type t3.medium --nodes 2 --nodes-min 2 --nodes-max 4 --managed
```
This may take several minutes to finish creating the cluster.

17. Once the cluster is created, connect to the cluster:
```
aws eks update-kubeconfig --name myeks --region us-east-1
```
18. Verify that it is running eksctl:
```
eksctl get cluster
```
You should see that it is running.

#### Deploy a Test Application to Mimic the Application
1. Install the Git package:
```
sudo yum install git -y
```
2. Clone a repository from the EKS Basics course:

```
git clone https://github.com/ACloudGuru-Resources/Course_EKS-Basics
```
3. Change into the Course_EKS-Basics directory:
```
cd Course_EKS-Basics/
```
4. View the contents of the directory:
```
ls
```
You should see a license file, an nginx-deployment.yaml file, and an nginx-svc.yaml file.
5. View the nginx-deployment.yaml file:
```
cat nginx-deployment.yaml
```
6. View the nginx-svc.yaml file:
```
cat nginx-svc.yaml
```
7. Apply the nginx-svc.yaml file:
```
kubectl apply -f nginx-svc.yaml
```
This should create the Nginx service.
8. Apply the nginx-deployment.yaml file:
```
kubectl apply -f nginx-deployment.yaml
```
This should create the Nginx deployments.

9. Verify that the deployments are available:
```
kubectl get deployment
```
You should see that all three deployments are available.

10. Verify that all Pods are running:
```
kubectl get pods
```
11. Verify that the service is running:
```
kubectl get svc
```
You should see that the load balancer has a DNS name.

### Use the DNS Name of the Load Balancer to Test the Cluster

1. Copy the DNS name of the load balancer.
2. Use the DNS name to test that the cluster is working:
```
curl <PASTE DNS NAME HERE>
```
  You should see the test page for the Nginx service.