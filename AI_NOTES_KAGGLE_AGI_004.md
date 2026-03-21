## COOKBOOK for kaggle-benchmarks

KAGGLE BENCHMARK LIBRARY, of 15 RECIPES from the COOKBOOK - a full review!

Basics - Data Evaluation - Conversational - Multimodal - Advanced Patterns

____________________________________

## BASICS

### 1 PASS/FAIL

 - returns nothing, true if all assertions pass
 - deterministic

 ### 2 JUDGE LLM

 - open ended, subjective tasks
 - non-deterministic
 - custom prompt and schema

 ### 3 NUMERIC SCORE

 - return float int

 def fn(llm) -> float:

 ### 4 Structured Output SCHEMA

 > @dataclass

 > schema = Custom  - inside of llm.prompt()

 ### 5 PUBLISH LEADERBOARD

 > %choose # magic

 ___________________________________________

 ## DATA EVALUATION

 ### 6 PERFORMANCE of DATAFRAME

 pandas DataFrame (array of objects)

 > .evaluate()

 - runs against every row.

> print(results.as_dataframe())

### 7 COMPARE SIDExSIDE MODELS

> inside .evaluate, llm=models

models = [ array of kbench.llms[]]

____________________________________


## CONVERSATIONAL AI

### 8 CHAT HISTORY

multi-turn conversations easy and natural.

> llm.prompt() # retains context

________________________________________


### 9 CONVERSATIONS for JUDGES

chats separate from MAIN AGENT

> with kbench.chats.new(): # avoids context 


### 10 MULTI-AGENT CHAT MANAGEMENT

- separate chat history for each agent

- use dedicated Chat object for each agent.

> contexts.enter()  # context manager, switch between context windows.

> chat1 = chats.Chat(name="chat1")


_________________________________________


## MULTIMODAL

### 11 SEND IMAGES to MODELS

 - data encoded string.

 - Base64 & URL.

 - Image Objects.

 #### 3 FACTORY METHODS:
 1) URL
 2) Local PATH
 3) Base64 String.

#### PROMPT vs SEND

> llm.prompt() # msg, resp, auto-converted base64.
> user.send multi-turn chat history - URL sent to model.

llm.PROMPT:
- use for optimized interaction. 

user.send:
- use for multi-turn interactions
- stack multiple images before a response.
- low-pass urls.


## ADVANCED PATTERNS

### 12 INTERACTIVE GAME LOOP

while loop over MODELS.

> llm.prompt()

### 13 REUSABLE CUSTOM ASSERTIONS

- reusable assertion functions

> @assertion_handler # decorator

### 14 PYTHON SCRIPT RUNNER

> kbench.tools.python.extract_code()
> kbench.tools.python.script-runner.run_code()

### 15 CUSTOM TOOLS for MODELS

- pass Python functions as tools - to MODEL!

- The model then calls fns() to:

1) retrieve information (data)

or

2) Perform Actions.

- experimental feature.

> tools=[customtool] # within llm.prompt

- wors best for "genai" models.










