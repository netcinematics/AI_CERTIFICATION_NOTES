_________________________________________________


metalanguage_powertools
ontology is skeleton of writing
corpus is body of work
nomenclature is domain of science words
AI_NOMENCLATURE for input optimization
neologisims
lexicon - complete inventory of words and patterns in domain.
Semantif Field (domain) - concept space.
taxonomy - heirarchical structure of is-a relationships.
nomenclature - system of names in science
metalanguage - language to analyze language itself.
glossary - list of terms with definitions.
Onomasiology - soudy of how concepts are named
Semasiology - study of what names mean.
terminiology
___________________________________


PROMPTING a CONCEPT ECOSYSTEM.

wordwebz aMETZaNETZa of GEMZ, COGZ, VIEWZ, CHOOZE, ACTZ, and METASTATEZ.

define the CONCEPT_CONSTELLATION

"false friends"

in domain ecosystem.


___________________________________


Home of benchmark ecosystem (API)

Python LIbrary: kaggle-benchmarks

ML Task benchmarks


- robustness
- reproducibility 
- transparency
- to trust benchamarks

- model-agnostic

1) Research Benchmarks

2) Community Benchmarks

_____________________________________

Use LLM as a judge to rate it from 1-5.

Measure how often LLM uses "AMBIGUOSITY": misnomer, ambiguity.

prove one model is better than another.

Kaggle Benchmark Framework

Result is LEADERBOARD.

- reproducability
- complex evaluations
- agregate metrics

- run benchmarks over entire datasets

What ABILITY to MEASURE, - measurability.

KAGGLE AI BENCHMARKS - which is best?

Model Evaluation Metrics. 

__________________________________________

kaggle-benchmarks

challenge llm - compare answers

python tools 

- interpreter

- assertions

task - code function

benchmark - collection assemble

comprehensive evaluation.

@kbench.task decorator

# function to evaluate for each model

# llm.prompt - talk to model

# llm = what ever is in leaderboard

# assertion check correctness (build in functions)

# LEADERBOARDS pass/fail/score


count the number of r's in strawberry
 it should be exactly 3

@kbench.task(name="solve_riddle")
def solve_riddle(llm, riddle: str, answer: str) -> dict:
    # 1. Prompt the LLM
    response = llm.prompt(riddle)
    print(f"Model Answer: {response}")

    # 2. Grade the response (simple string check instead of Regex)
    is_correct = answer.lower() in response.lower()

    # 3. Assert based on the boolean calculation
    kbench.assertions.assert_true(
        is_correct,
        expectation=f"The model's answer should contain '{answer}'."
    )

    # 4. Set a return value (optional, but useful for batch evaluation - see part 2)
    return {
        "is_correct": is_correct,
        "model_response": response
    }

# Run the task immediately to test it
# kbench.llm is the default model pre-loaded in this environment
solve_riddle.run(
    llm=kbench.llm,
    riddle="What gets wetter as it dries?",
    answer="Towel",
)