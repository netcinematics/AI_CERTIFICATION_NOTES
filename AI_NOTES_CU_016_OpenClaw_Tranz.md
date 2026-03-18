# CU OPENCLAW TRANZ

___

## AI Evolution

LLM Evolution.

Transformer innovation.

## Language TRANSFORMATION.
### Text COMPLETION.
   (prompt | completion )
### INSTRUCTION mode.
   (user | assistant)


### RAG innovation.
   (system | context)
   - use context as response.

### CHAT Innovation.
    - recursive CONTEXT WINDOW.
    - interface

### AGENT innovation.
    (tool defs | tool call | tool output)
    (system | memory ) 
    (reasoning | step by step | CoT)
- Tool Use.
- World Knowledge.
- Memory.
- CoT.

____

## OPENCLAW

- Heartbeat.
- memory
- tool use
- Message Queue
- debouncing

(SOCIOL INPUT | Loop | wait | enqueue | dequeue)
___

## NOTES:

AI ORIGIN STORY:

token representation | embedding | encoding

vector hidden representation | decoder

useful!

innovated prompt before encode - into decoder only!

completes the next word! 

Model thinks of it as an instruction. Reasoning. Self-Reflection.

Sampling Process - many possibilities to respond.

Instruction Tuning - minor adjustment in next word choice (tuned).

Fine-Tuning - many parameters to adjust.

Instruction Tuning. 

Fine-Tuning. 

#### Token Level

PREFILL - user input into LLM, assistant decodes

RESPONSE: FEED TOKENS to USER ASSISTANT CYCLE.

### RAG

models can only read encoded knowledge. 

knowledge cut off time : solution RAG.

Can use tool use for internet search.

Augment Context TOKENS. 

EMBED to DATABASE as prompt, SYSTEM TOKEN  retrieves context from database.

PREFILL from CONTEXT TOKEN and USER TOKEN - for better response.

assistant feeds tokens back to user.

### CHAT GPT

SYSTEM PROMPT TOKENS: be helpful, harmless, honest.

PREFILL SYSTEM PROMPTS (persona) and USER PROMPTS (context).

prompt tokens cheaper because feed all at once.

response tokens expensive because feed one at a time.

PREFILL - illusion of communication - feed back tinto large model.

PREFILL - all tokens at once.

DECODING - one token at a time.

STREAMING - shows one token at a time.

STATELESS ILLUSION preserved by sending full context each time.

### AGENTS

Use external tools.

tool definitions are part of the system prompt (tokens).

user prompts, 

PREFILL - choose the right tool.

TOOL call and TOOL output - PREFILL.

CHAT 

PREFILL - tool call output.

CONTEXT MANAGEMENT - CONTEXT KEEPS GROWING..

### MEMORY

use system prompt to include MEMORY TOKENS.

part of context. 

 - 

 ### COT

 "Think step by step" - steer model to reason.

 Magic happen - "REASONING" reasoning token.

 every time decode use all previous. 

 CoT added to context.

 ____

 ## OPENCLAW

 Heartbeat - keep alive.

 Message Queue - FIFO.

 Debouncing - prevent duplicate messages.

#### HEARTBEAT

 HAPPENING as BACKGROUND PROCESS - by HEARTBEAT.

 Chron Job. 

 SOCIAL MEDIA becomes USER INPUT.

#### MEMORY 

markdown file.

human readable memory. cannot read DB.

FILE READ INTO SYSTEM MEMORY CONTEXT WINDOW.

Same as before but reads MEMORY from local md.

CONCANTENATED file operation.

If too much memory - truncate | MEMORY COMPACTION.

#### MESSAGE QUEUE

FIFO - First In First Out.


#### security

prompt injection: tool output - feed to llm.

out of scope?

#### BUNDLING QUEUE.

Batching - multiple requests at once.


## OllamaLLM

Val Andrei Fajardo.

LLama Index slopocalypse.

https://www.youtube.com/watch?v=l41501_0g9A

Build a Multi-Agent system.

Synthesis and Response.

MODE: Chat INTERFACE

- chat history.

- tools: plotter, function(), search_engine(), 



