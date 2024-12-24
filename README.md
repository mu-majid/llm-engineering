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