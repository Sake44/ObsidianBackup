A key part of the foundation model lifecycle is the optimization phase. An FM can be further optimized in several different ways. These techniques vary in complexity and cost, with the fastest and lowest cost option being prompt engineering.

### Prompt Engineering
Prompts act as instructions for foundation models. Prompt engineering focuses on developing, designing, and optimizing prompts to enhance the output of FMs for your needs.
A prompt's form depends on the task that you are giving to a model. Prompts contains some or all of the following elements: 
- **Instructions**: This is a task for the FM to do. It provides task description or instruction for how the model should perform. 
- **Context**: This is the external information to guide the model
- **Input data**: This is the input for which you want a response.
- **Output indicator**: This is the output type or format.

### Fine Tuning
Although FMs are pre-trained through self-supervised learning and have inherent capability of understanding information. 
 Fine-tuning is a supervised learning process that involves taking a pre-trained model and adding specific, smaller datasets. Adding these narrower datasets modifies the weights of the data to better align with the task.
There are two ways to fine-tune a model: 

- **Instruction fine-tuning** uses examples of how the model should respond to a specific instruction. 
- **Reinforcement learning from human feedback (RLHF)** provides human feedback data, resulting in a model that is better aligned with human preferences.

### Retrieval-augmented generation (RAG)
RAG is a technique that supplies domain-relevant data as context to produce responses based on that data. RAG retrieves a small set of relevant documents and uses that to provide context to answer the user prompt. RAG will not change the weights of the foundation model, whereas fine-tuning will change model weights.