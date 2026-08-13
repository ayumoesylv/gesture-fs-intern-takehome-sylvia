# Plan

### 1. Understand the problem and the solution

Who is the likely customer? -> a business or individual that would like to use a marketing agency, potentially for a product or service

What problem is this solving? -> reducing resources necessary to manually answer the same questions for multiple clients

What would the customer care about? 
- Will using this agency increase my visibility? -> Requires relevant evidence to answers
- Does this service answer my questions concisely and clearly? -> Direct answers from context and evidence 
- Does this marketing agency understand my personal needs? -> (potential extension) tailor the response to the consumer's context by introducing an onboarding section that collects data and is accessible to add to the context for the prompt.

### 2. Understand the codebase 

What I focused on:
- understanding the conceptual layers (data layer -> response generation layer -> orchestration layer -> client layer)
- mapping those to the files and functionality that already existed:
    - Data: Raw text files -> chunked document objects -> vector stores 
    - Response generation layer: local LLM, prompt composition
    - Orchestration layer -> LangChain 
    - Client layer -> CLI (Interactive mode and CLI args)
- Determine data types of variables to better understand the flow 

### 3. Decisions
In main(), I chose to create a nested function display_output, because after creating a conditional block to handle single question mode and interactive mode, I noticed repeated functionality. This way, I could extract that and avoid repetition, while ensuring this helper is not exposed or used outside of the main() function. 

In main(), I chose to only handle the FileNotFoundError because I felt that for any other error, I would like that error to propagate out, as it would not be something to recover from. It would signal something was truly wrong. 
