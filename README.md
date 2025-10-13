## Module 0
 - we did the basic setup required
 - made a simple RAG application using groq api
  
    ---
   
## Module 1  
1. **Introduction**
   - in this module we will be learning how to implement tracing in a basic LLM
   - tracing helps in dealing with unexpected outputs while building an LLM app
   - it helps us track how each part of our application is contributing to the output
2. **Lesson 1**
   - projects have a collection of traces , each time the user runs the application a trace gets published in langsmith.
   - in our RAG application there are mainly 2 Runs , Retrieve Document and Generate response.
   - we can use tracing by the traceable decorator , to set it up we need to add @traceable to each of our functions.
   - traceable streams the name of the function and the inputs to langmith each time the function is called .
   - When a function returns or throws an error, its output or error is  added as an update to the trace.
   - Adding metadata to a function allows you to store additional information about the function's execution, such as tags or version info
3. **Lesson 2**
   - LangSmith supports multiple run types in @traceable: LLM, Retriever, Tool, Chain, Prompt, Parser
   - LLM traces require inputs and outputs in specific formats and can include metadata like ls_provider and ls_model_name
   - Streaming outputs can be converted to the same format as non-streaming outputs
   - Retriever traces log documents retrieved from databases or indexes and need run_type="retriever" with page_content, type, and metadata
   - LangSmith provides custom rendering for LLM, retriever, and tool calls to help visualize and debug executions
4. **Lesson 3**
   - Learned that @traceable decorator is the default way to enable tracing in LangSmith.
   - Understood that different nodes in a graph use LangChain components, and metadata can be passed using the config argument in invoke().
   - Tracing occurs automatically once environment variables are set up for LangChain and LangGraph
   - The with trace() block allows logging of specific code sections for detailed tracing control.
   - Learned that wrap_openai() enables tracing for all OpenAI SDK calls, and metadata can be added using the langsmith_extra field.
5. **Lesson 4**
   - Learned about threads, which are abstractions that group multiple traces together.
   - Each trace represents a single invocation or call within the application.
   - Threads help in tracking and debugging an entire interaction flow between a human and an LLM app.
   - You can create threads by adding a UUID as a key–value pair in the metadata using the langsmith_extra field.
   - This approach provides better context and organization for analyzing multi-step LLM interactions.

     ---

     ## Module 2
 1. **Lesson 1**
    - Learned that datasets are structured lists of examples used to test and evaluate LLM applications instead of relying on random checks.
    - Created datasets containing both inputs and outputs, and learned to tag dataset versions for testing across different app versions.
    - Learned to add new data manually or directly from trace runs.
    - Understood the role of schema in maintaining consistent data formatting and explored adding AI-generated examples.
    - Discovered how to split, share, download, or clone datasets for effective collaboration and evaluation
2. **Lesson 2**
   - Learned that evaluators are functions or processes used to measure and score the performance of an LLM application.
   - Evaluators compare the model’s output with the dataset examples to assign a performance score.
   - They can be defined and run in Jupyter notebooks or directly in the LangSmith web interface
   - Learned that custom evaluators can be created using your own code for specific evaluation needs.
   - LLMs themselves can also be used as evaluators, acting as “judges” to assess the quality of responses.
3. **Lesson 3**
   - Learned that experiments involve running an LLM application over a dataset and evaluating its performance using evaluators.
   - Experiments can be executed via the SDK (evaluate()) or directly in the LangSmith UI
    - Understood the importance of analyzing the impact of changing the LLM model on performance.
    - Learned how to run experiments on specific subsets of examples, including dataset versions, splits, or individual examples.
    - Experiments can be customized with parameters like repetitions, concurrent threads, and metadata to ensure consistent and detailed 

    ---

   ## Module 3
1. **Introduction**
   - quality of a promt directly affects the LLM's output.
   - with the right promts we can ensure out app delivers accurate and reliable responses
   - Langsmith's playground environment helps us in experimenting with different promts and models on various inputs.
   - promt hub is usefull for saving , organizing and versioning your promts over time.
2. **Lesson 1**
   - Understood the difference between hardcoded prompts and prompt templates, where templates provide greater flexibility by allowing variable inputs.
   - Explored the LangSmith Playground and observed how modifying the system prompt can significantly influence the model’s output.
   - Experimented with different models and parameters in the Playground to compare their responses and performance.
   - Learned about output schemas, which enforce a specific structure for model outputs, and discovered that tools can also be used for similar purposes.
   - Found that the Playground enables testing datasets directly, making it easier to evaluate prompt behavior and output quality.
     **tweaking**
     - got the output for a promt inside the langsmith playground with the gpt 4o mini model.
     - tried comparing different models on the same promt in the langsmith playground , but couldnt find any  model's API key for free.
     - created a custom dataset and ran experiments on it inside the langsmith playground.
3. **Lesson 2**
   - Learned about LangSmith’s Prompt Hub, a centralized place to store and manage prompt templates.
   - Understood that each template consists of a list of messages, which can be either system or human messages.
   - Found that these messages are dynamic templates, not static strings — they can include variables filled in at runtime
   - Discovered that a prompt template includes the templated messages, model configuration, and optionally an output schema.
   - Recognized how the Prompt Hub helps maintain organized, reusable, and adaptable prompts for different use cases.
     **tweakings**
     - created a promt as "you are a 18 year old student " and asked questions like how to clear an exam in english language
     - updated the same promt to you are a teacher and asked questions like how to make a student clear an exam in english language
4. **Lesson 3**
   - Learned how to use the LangSmith Playground and Prompt Hub together to iterate and refine prompts within an application.
   - Understood how to perform end-to-end prompt optimization, testing and improving prompts directly through the interface.
   - Discovered that edits and commits made in LangSmith automatically reflect in the application’s code.
   - Realized that this removes the need to manually update the code every time a prompt is modified
   - Found this workflow extremely efficient and powerful for maintaining and improving prompt performance seamlessly.
     **tweakings**
     - created a new promt which asks the LLM to answer in the shortest way possible.
     - tested it on the same dataset as I found creating a new dataset hard as the rag application only answerd questions based on the langsmith document , therefore I tested my new promt on the same dataset.
     

    
