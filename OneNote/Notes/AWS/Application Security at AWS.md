Both web and servers application hosted at AWS are usually located on a private subnets, which are not directly accessible from the internet. Customers requesting access to the application will be directly by DNS services (Route 53) to the DNS name of the load balancer.
 
To have just an example we could take in consideration a tier-three web application designed to using many encryption/decryption points, like:

1. **AWS Web Application Farewell (WAF):** custom traffic filter that can be associated with an Application Load Balancer to protect against malicious traffic requests.
2. **Application Load Balancer:** An application load balancer can accept encrypted HTTPS traffic on port 443
3. **EC2 instance hosting web application:** EBS boot and data volumes can be encrypted using the AWS KMS service
4. **EC2 instance hosting server application:** EBS boot and data volumes can be encrypted using the AWS KMS service
5. **RDS DB server:** All boot and data can be encrypted using **KMS.**