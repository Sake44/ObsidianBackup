**Security at AWS**
 
As you move to AWS cloud, you need to consider some security factors:
 
1. **Data Security:** the reality is that your data are more secured in cloud than on-premises physical servers. All storage mediums at AWS are encrypted with the **Advanced Encryption Standard** (AES). Amazon **S3 buckets** are encrypted with keys provided by the S3 service or the Key Management Service (KMS). Data **durability** provides additional security as all data stored in AWS is stored on multiple physical locations. **Amazon S3 objects** are replicated across at least **three** separate availability zones within the selected AWS region, producing a very high level of durability.
2. **Data Privacy:** Amazon ensures that each AWS account's stored data records remain isolated from other AWS customers. Each s3 bucket is can be shared publicly but first all data records are created as a private resources.
3. **Data Control:** Customers are fully responsible for storing and retrieving their data records stored at AWS. it's customer responsibility to define the security and accessibility of all data records stored in AWS.
4. **Security Controls:** AWS Identity and Access Management (IAM) permissions policy can be defined at a very granular level to control access to all resources.