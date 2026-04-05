KAGGLE BENCHMARK RECIPIES.

kaggle-benchmarks library - create, run, evaluate benchmarks.

1) TASK
2) BATCH
  - evaluate model across DataSet.

  .run() - task function.
  .evaluate() - DataSet inside tasks.

  EVALUATE - pandas DataFrame.

  else 

  kbench.assertions.assert_true

  MUST RETURN VALUE - to score a dataset.

  1) RETURN BOOL
  2) RETURN RANGE
  3) RETURN RATIO

_______________________

1-10 IS NUMBER ODD?

0-1 Is NUMBER RATIO?

O RIDDLES?

_______________________________

BOOL ACCURACY PERCENTAGE

_________________________

TASK DETAIL PAGE:

- when you click "Save Task".

- must have one primary task.

Chose a different TASK FUNCTION:

> %choose batch_riddle_solver

______________________________

MORE FEATURES:

O - MULTI-TURN INPUTS
O - Advanced Logic: Agents, Tools, Multi-Model Comparison)
O - Deep Evaluation
  - LLM-as-a-Judge
  - Return Types. 


  _______________________


  ## QUICK_START.md

 ### REPLICATION
  - exact inputs, outputs, model interactions for review.

  ### COMPLEX EVALUATIONS:

  - code execution, tool use, 
  - MULTI-TURN "conversational" abilities!

  ### RAPID PROTOTYPING

  - test a models capabilities - new creative tasks!

> !pip

___________________________

### CORE CONCEPTS

#### Task: unit of assertion.

INPUT: LLM and prompt
- optionally return a value.
- without return PASS/FAIL based on ASSERTIONS.

- FIRST PARAM always LLM being tested.

- additional params optional.

#### LLM
 object representing LLM. INTERFACE. wrapper.

 > kbench.llms["vendor/model-name"]


#### Chat and Actor

CHAT: llm.prompt() or kbench.user.send() 
- Message is added to Chat

ACTOR: kbench.user or llm

- whoever sends the Message.

ASSERTION:

- verify model output.
- recorded in run results.

> kbench.assertions.assert_that(llm, expectation)

> kbench.assertions.assert_equal(answer, response, expectation="")

EXPECTATION:

- message summary on leaderboard.

- custom assertions decorator

> @kbench.assertions.assertion_handler

RUN:

- recorded TASK RESULTS

captures everything.
- definition, input, full chat , assertion results, and final return value.


_________________________

## FIRST BENCHMARK

O - return STRUCTURED OBJECT not txt.

- supports: dataclasses, pydantic models, dictionaries, primitives.

- schema param in llm.prompt

O - dataclass decorator

- varies by LLM and PROMPT, consider providing examples?


__________________________

## ADVANCED Features

### IMAGE INPUT

O - Can you read this TEXT SNAPSHOT, or TEXT SCREENSHOT?

> image = kbench.content_types.images.from_base64()

### MULTIPLE LLMs

compare multiple models - single Task.

separate Chat contexts.

> with kbench.chats.new()

_______________________________

O - Poem Evaluation

- 1 Gemini Orchestrator

- 2 JUDGE_LLMS

- 3 Chats

> kbench.llms
> with kbench.chats.new()


### Python SCRIPT RUNNER

- access to tool use.

- allow model to execute code

O - fibonacci counter

> code_to_run = kbench.tools.python.extract_code()

> exec = kbench.tools.python.script_runner.run_code()

> kbench.assertions.assert_empty()

__________________________________________

### Creative and Robust ASSERTIONS

- external libraries.

O - Levenshtein fuzzy string matching.

____________________

### Dataset

- pandas DataFrame

- aggregate performance metrics.

> .evaluate()

 - runs each row in parallel.

 O - capitals around the world.

 > gold_target

 - one TASK loops over singular TASKS of llm.prompt()s.

 > with kbench.client.enable_cache().evaluate()

 O - ACCURACY mean
 O - std Standard Deviation?

 - .evaluate() is POWERFUL BATCH PROCESSOR.

 - progress bar of tasks completed.

 - returns RUNS object - list of individual RUN objects.

 - large data sets:
 > os.environ["render_subruns"] = "false" ish.

 ___________________________________

 ### IPython magics

 > %autopilot - generate code

 > %choose - select a notebook task into runtime - for leaderboard.

 - removes run.json and task.json

____________________________________

### EXAMPLES

X - clone into GitHub

> !ls /benchmarks/documentation/examples/

> %load - load and run magic command

> %load /benchmarks/documentation/examples/tic_tac_toe_game.py

________________________________________


## USER GUIDE

### TASK

decorator

> @kbench.task

> def my_task(llm):
>    pass

### CHATS

> kbench.user.send()

O - what do you see in this image?

> kbench.chats.new()

O - test context of learning new language?

- sun, blackhole, moon.

### CHAT USAGE

> msg.usage.input_tokens_cost_nanodollars

> msg.usage.total_backedn_latency_ms

> msg.sender.role = "assistant"

### ASSERTIONS

expectation parameter inside assertions

text on leaderboard

### CUSTOM ASSERTIONS

> kbench.assertions.assertion_handler

encapsulate custom validation logic

###  assess_response_with_judge

> kbench.assertions.assess_response_with_judge

O - complex assessment - beyond simple checks.

 - set of natural language criteria.

 - where quality is nuanced understanding

 - returns AssessReport - list per criterion

 - iterate over criterion (results) to record assertion for benchmark.

O - summarize little red riding hood.

### CUSTOM PROMPTS and SCHEMAS

> prompt_fn      : prompt
> output_schema  : response

- useful for Judge to return specific feedback