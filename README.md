# llm-engineering
Journey to learn Large Language Models (LLMs)

## Introduction:
### Setup:
1. installed Anaconda
2. Setup the environment using environment.yml file
  - `conda env create -f environment.yml`
3. Added my openai api key to be able to connect to openai apis.
4. Activate the conda env
  - `conda activate llms`
5. Run `jupyter lab` to spin up the notebooks.

### Notes:
 - Frontier models have some limitations, like:
    1. Not a PhD level in some specialised domains, so an expert is still needed there.
    2. Their knowledge is cut off to a certain date.
    3. Can have blind spots and give wrong answers very confidently.

 - Transformer Architecture is the one behind LLMs.
 - Parameters in a model are also called weights, and these weights are actually the one controlling how the output will look like form the model.
 - Tokens are the individual units which get passed into a model. Tokens are a middle ground solution and breakthrough (word stem) between trying to train the neural network on a character basis and trying to train them based on word by work basis.
 - Context Window: Max number of texts in terms of tokens that the model can consider when generating the next token.
 - LLMs are stateless, so they don't keep track of any info and every API call is unique (e.g User: "My favourite sport is football" - GPT: "That's great, football is ...." | User: "What's my favourite sport?" - GPT: "Sorry I don't have this information").
 - ChatGPT on the other hand is a separate application, different from simply making a stateless api call, it saves the conversation history and sends it every time you send something to the API so it has context.
 - Exceeding the context window is usually handled by two methods (trucating older parts of the chat's history, or Chunking the data to keep the logic coherent, then run LLM on the aggregated (LLM)processed chunks)

## Multi Modal Chatbot:

### Notes:
 - Tools basically refer to the idea of allowing frontier models to communicate with external functions.
 - This could be querying something, or doing an action.
 - LLMs are bad at calculations, so one use case is to use a calculator as an external function that LLMs can use.
 -  Agents (Agentic AI) is a software that can autonomously perform tasks. They are Autonomous, Task Specific, and Goal-oriented.
 - The term 'Agentic AI' and Agentization is an umbrella term that refers to a number of techniques, such as:

    1. Breaking a complex problem into smaller steps, with multiple LLMs carrying out specialized tasks
    2. The ability for LLMs to use Tools to give them additional capabilities
    3. The 'Agent Environment' which allows Agents to collaborate
    4. An LLM can act as the Planner, dividing bigger tasks into smaller ones for the specialists
    5. The concept of an Agent having autonomy / agency, beyond just responding to a prompt - such as Memory

## HuggingFace

### Notes:
 - This is an open source platform that has models, datasets, transformers, ... ready to use for us.
 - There are six libraries behind HuggingFace: ( Hub, datasets, transformers, Peft, TRL, Accelerate )
 - Hugging Face has two APIs: 1. Pipelines (high level, easy to use api), 2. Tokenizer&Models (Advanced API)
 - Tasks that we can do with pipelines API are, in addition to generating text, imgs and audio:
  1. Sentiment Analysis
  2. Classifier
  3. Named Entity Recognition
  4. Question Answering
  5. Summarising
  6. Translation

 - When using Tokeniezers&Models, there're some techniques that we should pay attention to:
  1. Quantization: Reducung the precision of the weights in the model, so it fits in memory and runs faster
  2. Streaming: Stream the result back instead of just returing it in a big bulk.

## Models for code Generation:
 - The Chinchilla Scaling Law: Number of parameters (Weights) in a model is proportional to the number of training tokens.
 - Common Benchmarks for deciding which model to use for a task at hand:
  1. ARC -> Reasoning -> used for evaluating scientific reasoning, MCQ..
  2. DROP -> Language Comparison -> Distill details from text then add, count,...
  3. HellaSwag -> CommonSense -> Harder endings, long contexts, low shot activities
  4. MMLU -> Understanding -> Factual recall, reasoning and problem solving across 57 subjects
  5. TruthfulQA -> Accuracy -> Robust in providing truthful replies in adversarial conditions
  6. Winogrande -> Context -> Test LLM understand context and resolve ambiguity
  7. GSM8K -> Math -> Math and word problems taught in elementary and middle schools

 - Specific Benchmarks:
  1. ELO ->  Chat -> Head-to-head face offs with other LLMs, Like ELO in Chess
  2. HumanEval -> Python Coding -> 164 problems wiiting code based on docstrings
  3. Multipl-E -> Broader Coding -> Translation of HumanEval to 18 programming langyages

 - Some of the limitations to the Benchmarks tests:
  1. Not consistently applied
  2. too narrow in scope
  3. hard to measure nuanced reasoning
  4. training data leakage
  5. Overfitting
  6. Frontier LLMs may be aware thet they are being evaluated (not yet proven)

 - New harder Benchmarks to overcome the limitation
  1. GPQA -> Graduate Tests -> 448  expert questions; non-phd humans score 34% even with web access
  2. BBHard -> future capabilities -> 204 tasks believed beyond capabilities of llms
  3. Math Lv 5 -> Math ->  High-school math competition problems
  4. IFEval -> difficult instructions -> like "write more than 400 words ..."
  5. MuSR -> Multiple Soft Reasoning -> Logical deduction, such as analyzing 1000 words murder mystery and answering "who has means motive and opportunity"
  6. MMLU-PRO -> Harder MMLU -> harder mmlu with 10 choices instead of 4 in the test

 - Hugging face Leaderboard is an awesome place for comparing models againsts different benchmarks.https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard#/