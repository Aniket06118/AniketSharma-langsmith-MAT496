## module 0
 - we did the basic setup required
 - made a simple RAG application using groq api
  
    ---
   
## module 1 
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

     
    
