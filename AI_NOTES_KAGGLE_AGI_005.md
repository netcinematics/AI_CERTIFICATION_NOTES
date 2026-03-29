# EXAMPLES of BENCHMARK LEADERBOARDS

- 50 Examples to review.


Can be ORGANIZED by BENCHMARK HIGHLIGHT - to target NEEDS.

## METHODOLOGY

- go through each of the RECIPE NOTEBOOKS and add IDEAS - then build them.

## RECIPE IDEAS

O - COGNITIVE ABILITIES

### ASSERTIONS:

- output vs criteria

> assert_equal
> assert_true / assert_false
> assert_in / assert_not_in
> assert_empty / assert_not_empty
> assert_contains_regex / assert_not_contains_regex
> assert_fail
> assert_response_with_judge


IDEA: most important is assess_rsponse_with_judge
IDEA: haiku_evaluation into 
 O - polysemy_evaluation
 O - homonymy_evaluation
 O - ambiguity_evaluation
 O - misnomer_evaluation
 O - orchestrator chat.
 O - riddle analysis
 O - haiku analysis
 O - neolog analysis

### BASIC RETURN TYPES:

- None, BOOL, float, tuple, dict.

Most important is Score, Tuple return.

IDEA:
 O -  statistics.mean(scores), statistics.stdev(scores)

### STRUCTURED RETURN TYPES:

- schema param in llm.prompt()

- dataclasses and Pydantic models.

- useful for parsing llm response (force into dataclass)

- Native python types, int & bool.

- Pydantic Instance is JSON as SCHEMA!?!

- DATACLASS decorator as SCHEMA

- PYDANTIC MODEL

IDEA:
O - Pydantic Model Class for complex schema, and nested structure.
O - otherwise JSON DICTIONARY or dataclass decorator.

### TASK for LEADERBOARD:

> llmstream_reponses = True

> assert_in

> parsing HTML

IDEAS:

O - animated HTML.

### Dataset Evaluation

> DataFrame is array of objects.

O - pandas DataFrame Batch
O - task evaluate whole dataset
O - accuracy and std

- isolate judges
> chats.new()

O - try: except blocks - exception handling

"EVALUATION PIPELINE"

> .evaluate() # multipe models.

### CONVERSATIONS

> llm.prompt() and llm.send() and llm.respond() # saves context

> kbench.chats.new() # isolates context (cheaper)

 - CHAT HISTORY & ISOLATED CHATS

 O - Twenty questions game loop.

### STORYTELLING BENCHMARK

 O - multi- agent collaboration

 O - compare genai across llms

 O - textarena


### SEND IMAGE to LLM

O - can you read this screenshot?

O - local image file.

### Turn Based Games

O - generic turn-based game framework

### custom assertions

### tooluse

- manual and automatic tool calling

___________________________________________

## EXAMPLES

### LLM HISTORY

### ROMANIA

### LLM MATH


### spymaster

### wordl

### word chain

### arc agi

### psycho mirror

_________________________________________________


## FACTS BENCHMARKS

### Parametric

### Search

### Multimodal

### Grounding
