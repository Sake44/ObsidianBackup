Generative AI is powered by models that are pretrained on internet-scale data, and these models are called foundation models (FMs).  With FMs, instead of gathering labeled data for each model and training multiple models as in traditional ML, you can adapt a single FM to perform multiple tasks.
FMs can also serve as the starting point for developing more specialized models.

### Foundation Model lifecycle
The foundation model lifecycle is a comprehensive process that involves several stages, each playing a crucial role in developing and deploying effective and reliable foundation models.

1. **Data Selection**: Unlabeled data can be used at scale for pre-training because it is much easier to obtain compared to labeled data. Unlabeled data includes raw data, such as images, text files, or videos, with no meaningful informative labels to provide context. FMs require training on massive datasets from diverse sources.
2. **Pre-training**: Although traditional ML models rely on supervised, unsupervised, or reinforcement learning patterns, FMs are typically pre-trained through self-supervised learning. With self-supervised learning, labeled examples are not required. Self-supervised learning makes use of the structure within the data to autogenerate labels. After the initial pre-training, the model can be further pre-trained on additional data. This is known as **continuous pre-training**.
3. **Optimization**: Pre-trained language models can be optimized through techniques like prompt-engineering, RAG and fine-tuning. 
4. **Evaluation**: the next step is to evaluate the model. An FM's performance can be measured using appropriate metrics and benchmarks.
5. **Deployment**: When the FM meets the desired performance criteria, it can be deployed in the target production environment. Deployment can involve integrating the model into applications, APIs, etc...
6. **Feedback and continuos improvement**: After deployment, the model's performance is continuously monitored, and feedback is collected from users, domain experts, or other stakeholders. This feedback, along with model monitoring data, is used to identify areas for improvement, detect potential biases or drift, and inform future iterations of the model.

## Essentials FMs

### Large Language Models (LLMs)
Large language models (LLMs) can be based on a variety of architectures, but the most common architecture in today's state-of-the-art models is the **transformer architecture**. Transformer-based LLMs are powerful models that can understand and generate human-like text. They are trained on vast amounts of text data from the internet, books, and other sources, and learn patterns and relationships between words and phrases.

To better understand how LLMs work, let's talk about Tokens, Embeddings and Vectors. 

#### Tokens
Tokens are the basic units of text that the model processes. Tokens can be words, phrases, or individual characters like a period. Tokens also provide standardization of input data, which makes it easier for the model to process.
![[Pasted image 20251016114723.png]]

#### Embeddings and Vectors
Embeddings are numerical representations of tokens, where each token is assigned a vector (a list of numbers) that captures its meaning and relationships with other tokens. These vectors are learned during the training process and allow the model to understand the context and nuances of language.
![[Pasted image 20251016115142.png]]

### Diffusion Models
Diffusion is a deep learning architecture system that starts with pure noise and random data. The models gradually add more and more meaningful information to this noise until they end up with a clear and coherent output, like an image or a piece of text. Diffusion models learn through a two-step process of **forward diffusion** and **reverse diffusion**.

#### Forward Diffusion
Usign forward diffusion, the system gradually introduces a small amount of noise to an input image until only the noise is left over.

#### Reverse Diffusion
In the subsequent reverse diffusion step, the noisy image is gradually introduced to denoising until a new image is generated.

### Multimodal models
Instead of just relying on a single type of input or output, like text or images, multimodal models can process and generate multiple modes of data simultaneously. For example, a multimodal model could take in an image and some text as input, and then generate a new image and a caption describing it as output.

These kinds of models learn how different modalities like images and text are connected and can influence each other. Multimodal models can be used for automating video captioning, creating graphics from text instructions.

### Other generative models

There are several types of generative models used in ML and AI. 

#### Generative Adversarial networks (GANs)
GANs are a type of generative model that involves two neural networks competing against each other in a zero-sum game framework. The two networks are generator and discriminator.  
  
**Generator:** This network generates new synthetic data (for example, images, text, or audio) by taking random noise as input and transforming it into data that resembles the training data distribution.  
  
**Discriminator:** This network takes real data from the training set and synthetic data generated by the generator as input. Its goal is to distinguish between the real and generated data.

#### Variational autoencoders (VAEs)
VAEs are a type of generative model that combines ideas from autoencoders (a type of neural network) and variational inference (a technique from Bayesian statistics). In a VAE, the model consists of two parts:  
  
**Encoder:** This neural network takes the input data (for example, an image) and maps it to a lower-dimensional latent space, which captures the essential features of the data.  
  
**Decoder:** This neural network takes the latent representation from the encoder and generates a reconstruction of the original input data.  
  
The key aspect of VAEs is that the latent space is encouraged to follow a specific probability distribution (usually a Gaussian distribution), which allows for generating new data by sampling from this latent space and passing the samples through the decoder.