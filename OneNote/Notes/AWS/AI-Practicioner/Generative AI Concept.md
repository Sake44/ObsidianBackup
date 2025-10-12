Generative AI is supported under the hood by a Foundation Model. This models are pretrain with a lot of Ulabeled data. 
![[Pasted image 20251010093741.png]]
The main components of FMs are: 
1. Big amount of unlabeled data. After you FMs become a LLM.
2. LLM. Billions of parameters. You need a lot of compute to actually train your model. 

How do we get this unlabeled data? 
This data come from all the internet, actually it can be everything.
Usually, if you want to implement GenAI in your application, I don't train by yourself a FM. You can take an already trained FM and adapt it to your case. 
![[Pasted image 20251010094457.png]]

### Why are trasformers important? 
Early [deep learning](https://aws.amazon.com/what-is/deep-learning/) models that focused extensively on [natural language processing](https://aws.amazon.com/what-is/nlp/) (NLP) tasks aimed at getting computers to understand and respond to natural human language. They guessed the next word in a sequence based on the previous word.

To understand better, consider the autocomplete feature in your smartphone. It makes suggestions based on the frequency of word pairs that you type. For example, if you frequently type "I am fine," your phone autosuggests _fine_ after you type _am._

Early [machine learning](https://aws.amazon.com/what-is/machine-learning/) (ML) models applied similar technology on a broader scale. They mapped the relationship frequency between different word pairs or word groups in their training data set and tried to guess the next word. However, early technology couldn’t retain context beyond a certain input length. For example, an early ML model couldn’t generate a meaningful paragraph because it couldn’t retain context between the first and last sentence in a paragraph.
Transformer is important in GenAI context, cause it's responsible to take the input of unlabeled data and generate a sequence of output. 

#### Enable faster customization
With transformer models, you can use techniques such as transfer learning and retrieval augmented generation (RAG). These techniques enable the customization of existing models for industry organization-specific applications. Models can be pretrained on large datasets and then fine-tuned on smaller, task-specific datasets. This approach has democratized the use of sophisticated models and removed resource constraint limitations in training large models from scratch. Models can perform well across multiple domains and tasks for various use cases.