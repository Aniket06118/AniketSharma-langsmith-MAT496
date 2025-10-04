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
   
