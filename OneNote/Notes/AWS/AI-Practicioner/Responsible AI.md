Responsible AI refers to practices and principles that ensure that AI systems are transparent and trustworthy while mitigating potential risks and negative outcomes. These responsible standards should be considered throughout the entire lifecycle of an AI application. This includes the initial design, development, deployment, monitoring, and evaluation phases.
To operate AI responsibly, companies should proactively ensure the following about their system:

- It is fully transparent and accountable, with monitoring and oversight mechanisms in place.
- It is managed by a leadership team accountable for responsible AI strategies.
- It is developed by teams with expertise in responsible AI principles and practices.
- It is built following responsible AI guidelines.

### Biases in AI systems

The number one problem that developers face in AI applications is accuracy. Both traditional and generative AI applications are powered by models that are trained on datasets. These models can make predictions or generate content based only on the data they are trained on. If they are not trained properly, you will get inaccurate data. Therefore, it is important to address bias and variance in your model.

**Bias** is one of the biggest challenges a developer faces in AI systems. Bias in a model means that the model is missing important features of the datasets. This means that the data is too basic. Bias is measured by the difference between the expected predictions of the model and the true values we are trying to predict. If the difference is narrow, then the model has low bias. If the difference is wide, then the model has a high bias. When a model has a high bias, it is underfitted. Underfitted means that the model is not capturing enough difference in the features of the data, and therefore, the model performs poorly on the training data.

**Variance** offers a different challenge for developers. Variance refers to the model's sensitivity to fluctuations or noise in the training data. The problem is that the model might consider noise in the data to be important in the output. When variance is high, the model becomes so familiar with the training data that it can make predictions with high accuracy. This is because it is capturing all the features of the data.

### Bias-variance trade off
Bias-variance tradeoff is when you optimize your model with the right balance between bias and variance. The goal is to achieve a trained model with the lowest bias and lowest variance tradeoff for a given data set.
![[Pasted image 20251021120028.png]]

To help overcome bias and variance errors, you can use: 
- Cross validation: technique for evaluating ML models by training several ML models on subsets of the available input data and evaluating them on the complementary subset of the data. Cross-validation should be used to detect overfitting.
- Increase data: Add more data samples to increase the learning scope of the model.
- Regularization: a method that penalizes extreme weight values to help prevent linear models from overfitting training data examples.
- Simpler models: use simpler models architectures to help with overfitting. If the model is underfitting, the model might be too simple.
- Dimension reduction: is a unsupervised machine learning algorithm that attempts to reduce the dimensionality (number of features) within a dataset while still retaining as much information as possible. 
- Stop training early: end training early so that the model does not memorize the data


### Challenges of GenAI
Just as generative AI has its unique set of benefits, it also has a unique set of challenges. Some of these challenges include toxicity, hallucinations, intellectual property, and plagiarism, and cheating. 

- **Toxicity**: Toxicity is the possibility of generating content (whether it be text, images, or other modalities) that is offensive, disturbing, or otherwise inappropriate. This is a primary concern with generative AI. It is hard to even define and scope toxicity.
- **Hallucinations**: are assertions or claims that sound plausible but are verifiably incorrect. Considering the next-word distribution sampling employed by large language models (LLMs), it is perhaps not surprising that in more objective or factual use cases, LLMs are susceptible to hallucinations.
- **Intellectual property**: Protecting intellectual property was a problem with early LLMs. This was because the LLMs had a tendency to occasionally produce text or code passages that were verbatim of parts of their training data, resulting in privacy and other concerns.
- **Plagiarism and cheating**: The creative capabilities of generative AI give rise to worries that it will be used to write college essays, writing samples for job applications. Some are in favor of explicitly forbidding any use of generative AI in settings where content is being graded or evaluated, while others argue that educational practices must adapt to, and even embrace, the new technology.
- **Disruption of the nature of work**: The proficiency with which generative AI is able to create compelling text and images, perform well on standardized tests, write entire articles on given topics, and successfully summarize or improve the grammar of provided articles has created some anxiety. There is a concern that some professions might be replaced or seriously disrupted by the technology.

### Core dimensions of responsible AI
The core dimensions of responsible AI include fairness, explainability, privacy and security, robustness, governance, transparency, safety, and controllability. No one dimension is a standalone goal for responsible AI. In fact, each topic should be considered as a required part for a complete implementation of responsible AI.

- **Fairness**: crucial for developing responsible AI systems. With fairness, AI systems promote inclusion, prevent discrimination, etc...
- Explainability: ability of an AI model to clearly explain or provide justification for its internal mechanism and decisions so that is understandable to humans.
- **Privacy and security**: Privacy and security in responsible AI refers to data that is protected from theft and exposure. More specifically, this means that at a privacy level, individuals control when and if their data can be used. At the security level, it verifies that no unauthorized systems or unauthorized users will have access to the individual’s data.
- **Transparecy**: communicates information about an AI system so stakeholders can make informed choices about their use of the system. 
- **Veracity and robustness**: Veracity and robustness in AI refers to the mechanisms to ensure an AI system operates reliably, even with unexpected situations, uncertainty, and errors. The goal of veracity and robustness in responsible AI is to develop AI models that are resilient to changes in input parameters, data distributions, and external circumstances.
- **Governance**: Governance is a set of processes that are used to define, implement, and enforce responsible AI practices within an organization. Governance addresses various responsible, legal, or societal problems that generative AI might invite.
- **Safety**: Safety in responsible AI refers to the development of algorithms, models, and systems in such a way that they are responsible, safe, and beneficial for individuals and society as a whole.
- **Controllability**: Controllability in responsible AI refers to the ability to monitor and guide an AI system's behavior to align with human values and intent. It involves developing architectures that are controllable, so that any unintended issues can be managed and addressed.

### AWS Tools for transparent and explainability
To help with transparency, Amazon offers AWS AI Service Cards and Amazon SageMaker Model Cards. The difference between them is that with AI Service Cards, Amazon provides transparent documentation on Amazon services that help you build your AI services. With SageMaker Model Cards, you can catalog and provide documentation on models that you create or develop yourself.

SageMaker AI Clarify is integrated with SageMaker AI Experiments to provide scores detailing which features contributed the most to your model prediction on a particular input for tabular, NLP, and computer vision models.

Amazon SageMaker Autopilot uses tools provided by SageMaker AI Clarify to help provide insights into how ML models make predictions. These tools can help ML engineers, product managers, and other internal stakeholders understand model characteristics.

#### Interpretability trade-offs
Interpretability is the degree to which a human can understand the cause of a decision. This might sound a lot like explainability, but there is a distinction difference.
**Interpretability** is the access into a system so that a human can interpret the model’s output based on the weights and features. For example, if a business wants high model transparency and wants to understand exactly why and how the model is generating predictions, they need to observe the inner mechanics of the AI/ML method.
**Explainability** is how to take an ML model and explain the behavior in human terms. With complex models (for example, black boxes), you cannot fully understand how and why the inner mechanics impact the prediction. However, through model agnostic methods (for example, partial dependence plots, SHAP dependence plots, or surrogate models) you can discover meaning between input data attributions and model outputs.
![[Pasted image 20251022113222.png]]
If a business wants high model transparency and wants to understand exactly why and how the model is generating predictions, then they need a model that offers interpretability. However, high interpretability typically comes at the cost of performance, as seen in the diagram.