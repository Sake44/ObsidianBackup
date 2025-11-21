In this tutorial will create an Enteprise Knowledge Assistant with AWS Services. This tutorial is available in [AWS Skill Builder](https://skillbuilder.aws/learn/5YB3FCEE1H/aws-cloud-quest-generative-ai-practitioner/) (you need to access with APN Credential, you can create your partner account following this path: [AWS | Getting start with AWS Training (APN/SKill Builder) - Search | Degreed](https://degreed.com/learning/search?term=AWS%20%7C%20Getting%20start%20with%20AWS%20Training%20\(APN%2FSKill%20Builder\)&orgId=421&viewLearningId=49469054)) The services involved in this tutorial are:
1. Amazon S3
2. Amazon Bedrock
3. Amazon OpenSearch Live
The system uses advanced embedding technology and Retrieval Augumented Generation (RAG) to provide, instant, accurate response. 
## How Assistant work
User interact with the Amazon Nova FM to answer complex questions related to documents uploaded on S3 Bucket.
Thanks to RAG technique that enhances a FMs response allowing them access to retrieve information stored in an Amazon Bedrock Knowledge Base (KB).
To create a KB first we need a database to store vector embeddings which are numerical representations of the information in the source documents. This solution uses OpenSearch Serverless to store vector embeddings.
Also, we need a data source. In this solution, the data source is a bucket in Amazon S3.
To complete the knowledge base, a data source sync is initiated to populate the OpenSearch vector store.
Since this solution is just for test purpose, we can test it through built-in Amazon Bedrock testing tool.

## S3 Bucket 
Let's choose the documents you want to enhance FMs. Create an S3 Bucket. For this tutorial I'll use a reserved instance provided from course it self. (I'll replicate it in free-tier AWS Account). 



