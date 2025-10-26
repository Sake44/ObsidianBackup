AWS offers a comprehensive suite of ML and generative AI services that can help you unlock the full potential of these transformative technologies.
![[Pasted image 20251021104523.png]]

The stack starts at the ML frameworks layer. At the core of this layer is **Amazon SageMaker**. SageMaker is a fully managed machine learning service that you can use to build, train, and deploy your own custom models.

Next is the AI/ML services layer, where you find a wide array of specialized services tailored for different use cases.
Below most common. 

### Text and Documents domain
- **Amazon Comprehend**: natural language processing
- **Amazon Translate**: language translation
- **Amazon Textract**: extract data from scanned documents
### Chatbots domain
- **Amazon Lex**: to build conversational interfaces powered by the same deep learning technologies that drive Amazon Alexa.
### Speech domain
- **Amazon Polly**: text to speech
- **Amazon Transcribe**: automatic speech recognition
### Vision domain
- Amazon Rekognition: deep learning-based computer vision service that can analyze images and videos for a wide range of applications
- Amazon Kendra: reimagines enterprise search for websites and applications so that individuals can readily find the content they are looking for.
### Recommendations domain
- Amazon Personalize: real-time personalization and recommendations

### Miscellaneous domain
- Amazon DeepRacer: a fully autonomous 1/18th scale race car that lets you get hands-on experience with reinforcement learning.

## Generative AI layer
- Amazon SageMaker JumpStart: provides a set of solutions for the most common use cases.
- Amazon Bedrock: fully managed service that makes FMs from Amazon and leading AI startups available through an API. With Amazon Bedrock, you can quickly get started, experiment with FMs, privately customize them with your own data, and seamlessly integrate and deploy FMs into AWS applications.
If you'd prefer to experiment with building AI applications, you can get hands-on experience by using PartyRock, an Amazon Bedrock Playground.
- Amazon Q: generative AI–powered assistant designed for work that can be tailored for a business's data
- Amazon Q Developer: providing ML–powered code recommendations to accelerate development in a variety of programming languages and applications.

### Cost considerations

When working with AI and ML services on AWS, it's essential to understand the various cost considerations involved. These trade-offs can impact factors such as responsiveness, availability, redundancy, performance, regional coverage, pricing models, throughput, and the ability to use custom models.

### Amazon Services and tools for Responsible AI
There are different services and tool that can help you in different areas of responsible AI. 

#### Foundation Model Evaluation
You should always evaluate a FM to determine if it will it is suited for your specific use case. To help you do this, Amazon offers model evaluation on Amazon Bedrock and Amazon SageMaker AI Clarify.

##### Model Evaluation on Amazon Bedrock
With **Model evaluation on Amazon Bedrock**, you can evaluate, compare, and select the best foundation model for your use case in just a few clicks. Amazon Bedrock offers a choice of automatic evaluation and human evaluation. 

- Automatic evaluation offers predefined metrics such as accuracy, robustness, and toxicity. 
- Human evaluation offers subjective or custom metrics such as friendliness, style, and alignment to brand voice. For human evaluation, you can use your in-house employees or an AWS-managed team as reviewers.
##### Amazon Sagemaker AI clarify
SageMaker Clarify supports FM evaluation. You can automatically evaluate FMs for your generative AI use case with metrice such as accuracy, robustness and toxicity.

#### Safeguards for generative AI
With **Guardrails for Amazon Bedrock**, you can implement safeguards for your generative AI applications based on your use cases and responsible AI policies. Guardrails helps control the interaction between users and FMs by filtering undesirable and harmful content, redacting personally identifiable information (PII), and enhancing content safety and privacy in generative AI applications. 

#### Bias Detection
SageMaker AI Clarify helps identify potential bias in machine learning models and datasets without the need of extensive coding. You specify input features, such as gender or age, and SageMaker AI Clarify runs an analysis job to detect potential bias in those features. SageMaker AI Clarify then provides a visual report with a description of the metrics and measurements of potential bias.
You can use **Amazon SageMaker Data Wrangler** to balance your data in cases of any imbalances. SageMaker Data Wrangler offers three balancing operators: random undersampling, random oversampling, and Synthetic Minority Oversampling Technique (SMOTE) to rebalance data in your unbalanced datasets.

#### Model prediction explanation
**SageMaker AI Clarify** is integrated with Amazon SageMaker AI Experiments to provide scores detailing which features contributed the most to your model prediction on a particular input for tabular, natural language processing (NLP), and computer vision models.

#### Monitor and human reviews
**Amazon SageMaker Model Monitor** monitors the quality of SageMaker AI machine learning models in production. You can set up continuous monitoring with a real-time endpoint (or a batch transform job that runs regularly), or on-schedule monitoring for asynchronous batch transform jobs.
**Amazon Augmented AI (Amazon A2I)** is a service that helps build the workflows required for human review of ML predictions.

#### Governance improvement
SageMaker AI provides purpose-built governance tools to help you implement AI responsibly.

Governance tools include the following:

- **Amazon SageMaker Role Manager**: With SageMaker Role Manager, administrators can define minimum permissions in minutes. 
- **Amazon SageMaker Model Cards**: With SageMaker Model Cards, you can capture, retrieve, and share essential model information, such as intended uses, risk ratings, and training details, from conception to deployment. 
- **Amazon SageMaker Model Dashboard**: With SageMaker Model Dashboard, you can keep your team informed on model behavior in production, all in one place.

#### Providing transparency
**AWS AI Service Cards** are a new resource to help you better understand AWS AI services. AI Service Cards are a form of responsible AI documentation that provides a single place to find information on the intended use cases and limitations, responsible AI design choices.
Each AI Service Card contains four sections that cover the following:

- Basic concepts to help customers better understand the service or service features
- Intended use cases and limitations
- Responsible AI design considerations
- Guidance on deployment and performance optimization