ML is a subset of AI that focuses on developing algorithms and statistical models so that computer systems can learn from data and make predictions or decisions without being explicitly programmed. ML models learn patterns and relationships from data rather than relying on hard-coded rules for instructions.
When choosing an ML solution, it’s not just about the technology, but also about understanding the appropriate ML techniques for specific use cases. ML learning techniques represent the backbone of modern AI and empower systems to learn from data and make intelligent decisions without explicit programming. To deep dive into those techniques go to: [[Supervised and Unsupervised ML]], [[Reinforcement Learning (RL)]]. 

Supervised learning has two subcategories: 
1. Classification: Classification is a supervised learning technique used to assign labels or categories to new, unseen data instances based on a trained model. The model is trained on a labeled dataset, where each instance is already assigned to a known class or category. The goal of classification is to learn patterns from the training data and use them to predict the class or category for new unlabeled data instances.
	1. Fraud detection
	2. Image Classification
	3. Customer retention
	4. Diagnostics
2. Regression: Regression is a supervised learning technique used for predicting continuous or numerical values based on one or more input variable. It is used to model the relationship between a dependent variable (the value to be predicted) and one or more independent variables (the features or inputs used for prediction).
	1. Advertising popularity prediction
	2. Weather forecasting
	3. Market forecasting
	4. Estimating life expectancy
	5. Population growth prediction
In unsupervised learning, the data includes labels so that modelcan learn the patterns and relationships. In unsupervised learning, the model is trained on unlabeled data. The algorithm tries to discover hidden patterns or structures within the data without any prior information or guidance.

Unsupervised learning has two subcategories: 
1. Clustering:  This kind of algorithm groups data into different clusters based on similar features or distances between the data point to better understand the attributes of a specific cluster.
	1. Customer segmentation
	2. Targeted marketing
	3. Recommended systems
2. Dimensionality reduction:  technique used to reduce the number of features or dimensions in a dataset while preserving the most important information or patterns.
	1. Big data visualization
	2. Meaningful compression
	3. Structure discovery
	4. Feature elicitation
![[Pasted image 20251013133332.png]]


### Machine Learning Process
The machine learning process starts with collecting and processing training data. Bad data is often called _garbage in_, _garbage out_, and therefore an ML model is only as good as the data used to train it.
There are several different types of data used in training an ML model. Difference between **Labeled data** and **Unlabeled data**. 
- Labeled data is a dataset where each instance or example is accompanied by a label or target variable. 
- Unlabeled data is a dataset where the instances or examples do not have any associated labels or target variables.
The main types of data used in training are **structured** and **unstructured data**.

- Structured data refers to data that is organized and formatted in a predefined manner, typically in the form of tables or databases with rows and columns.
- Unstructured data is data that lacks a predefined structure or format, such as text, images, audio, and video. This type of data requires more advanced machine learning techniques to extract meaningful patterns and insights.

### Inferencing 

After the model has been trained, it is time to begin the process of using the information that a model has learned to make predictions or decisions. There are two main types of inferencing in ML: 
1. **Batch Inferencing**: Batch inferencing is when the computer takes a large amount of data, such as images or text, and analyzes it all at once to provide a set of results. This type of inferencing is often used for tasks like data analysis, where the speed of the decision-making process is not as crucial as the accuracy of the results.
2. **Real-time inferencing**: Real-time inferencing is when the computer has to make decisions quickly, in response to new information as it comes in. This is important for applications where immediate decision-making is critical, such as in chatbots or self-driving cars. The computer has to process the incoming data and make a decision almost instantaneously, without taking the time to analyze a large dataset.


## Deep Learning

The field of deep learning is inspired by the structure and function of the brain. It involves the use of artificial neural networks, which are computational models that are designed to mimic the way human brain processes information. 

### Neural Networks
At the core of deep learning are neural networks. Just like our brains have neurons that are connected to each other, neural networks have lots of tiny units called nodes that are connected together. These nodes are organized into layers. The layers include an input layer, one or more hidden layers, and an output layer.

![[Pasted image 20251015154955.png]]

When a neural network learns to recognize these patterns from the examples, it can then look at data for completely new customers that it has never seen before and still make predictions about what they might buy or how they might behave.

### Most important FM

![[Pasted image 20251013150530.png]]

### Machine Learning frameworks
The ML frameworks layer plays a crucial role in the development and deployment of machine learning models. At the core of the frameworks layer is Amazon SageMaker AI. SageMaker AI offers the right tools to effectively build, train, and run LLMs and other FMs efficiently and cost effectively.