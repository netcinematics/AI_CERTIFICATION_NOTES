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


> SOLUTION for AGI is a PARADIGM SHIFT - deeper into SCIENCE.


### FORMAL PROPOSAL for "extra_exactness" of words as "WORDZ".

- A) PRINCIPLES of NAMERATION (level 4 innovation)

    > "extra_exactness" -> LEXICAL "exactification"

- B) PROCESS of NAMERATE_METASTATE.

    > PRIME_GOAL: "best_reflect_actual_reality".

- C) PHENOMENA of "clean_slate" in EMBED SPACE.

    > BITZ of TOKEN_COMBINABILITY, called "solonomeration".

    SOLONOMERIC language is a goal for all concepts to be single unique words.

    As combined by BITZ, which are anchored by METASTATE so as to avoid SEMANTIC_DRIFT. In the reasonable occurence of NAMING_COLLISION both names should be adjusted to specify context.

EXAMPLE: "Singularity" appears to be borrowed from "black hole" linguistics and applied to the context of metacognition. Which appears reasonable on the surface, but on closer examination, reveals a critical flaw. Because the providers of the solution of less_ambiguousness, are observably perpetual offenders of the ambiguity problem. A better_word awaits_us for "singularity" to best_reflect_actual_reality and to avoid perpetual_confusion and endless_dispute - simply by the application of a more exact vocabulary (extra_exactness).

> Where at long last, this generation of biologic_intellect, appears unable to get out of our own way.

This is an expression of the principle that 

This paper provides BENCHMARKS for ANCHORING and GROUNDING, with a novel innovation of OPTIMIZING the INPUT LANGUAGE, as a clever ALTERNATIVE to SCALING laws, leveraging BPE, and dramatic reduction mechanism for exorbitant COMPUTE COSTS.

All PRINCIPLES and KEY CONCEPTS are expressed in uppercase, so as to specify the introduction of the novel terminology, also underscores are used to specify the language of ALPHABITZ - into a "clean_slate" METASTATE in embed_space.

> "OPTIMIZE_the_INPUTS"

> SUB_GOAL: BENCHMARK a UNIQUE set of LANGUAGE_MECHANISMS.

### PROJECT OVERVIEW:

INNOVATIONS in METACOGNITION classification and measurement.


### PRINCIPLES:

> Eventually, we need to "EXACTIFY_WORDZ" - to "best_reflect_actual_reality".

> "NOT_as_REPLACMENT", but as "EXTRA_LOGICAL_SUPPLEMENT".

> Reimagine SYNTAX and VOCABULARY - for AI - for the first time.

> "OPTIMIZE_the_INPUTS".

Amazingly, optimization of the SOURCE_LANGUAGE (input) is an ALTERNATIVE to SCALING LAWS. 

> We rely too much on COMPUTE in SCALING_LAWS. COMPUTE is expensive, can be dramatically reduced - if we can (ever agree to) EXACTIFY_WORDZ.

### 1st EXAMPLE | "AMBIGUOSITY" | extra_vocabulary for AI:

Coin a term: "AMBIGUOSITY" - is all types of ambiguity in biologic_language.

Functionally transforming biologic_language into digital_language. As a naturally occuring process - as language is dynamic. Since biologic_language, appears inherently brittle the concept of ANTI_FRAGILE_LANGUAGE awaits_us.

"ANTI_FRAGILE_LANGUAGE": where a taxonomy of all actual fragilities in language are compiled so as to leverage the exact_opposite_concepts - to make the digital_language supplement stronger from the misconceptions - not weaker.

With the advent of new technology (AI), this is reasonable for biologic_language for the first time in all human history - to be emergent in digital_languages. 

### SOLUTION_SPACE: 



- AMBIGUITY, 
- SEMANTIC_DRIFT,
- PARADIGM_SHIFT,
- CONTEXT_SHIFT,
- PROBABILITY_SMEAR,
- HOMONOMY & POLYSEMY,
- MISNOMER & MISCONCEPT.
- HYPERBOLE detection
- SARCASM detection.
- 
- Many more!

> Look at how every MISCONCEPT "pollutes_embed_space" - until we REVERSE_MISNOMER to point at ACTUAL_NOMER (actual name).

"BETTER_WORDZ" are generated, by a PROCESS and PRINCIPLES - of "COMBINIFICATION" and "SELF_DESCRIPTION". 

> "BETTER_WORDZ": where ARTICULATED METASTATE, best_reflects_actual_reality.

#### Phenomena of "clean_slate":

Biologically, it made no sense to use intentional misspellings, like "WORDZ".

But in AI, "clean_slate" makes perfect sense (in the matrix) - where no other conceptual_confusions exists. 

In currently existing EMBED_SPACE, the CLEAN_SLATE, is utilized for (lexical) definitions of "EXTRA_EXACTNESS". Resulting in actual anti-fragility for AGI.

### EXTRA_SCIENCE | NAMEROLOGY:

For AGI, "NAMEROLOGY" is a level 4 frontier breakthrough.

> "NAMEROLOGY": study of "nameration" (naming of objects) - using accurate representations of the metastate in the name of the CONCEPT.


### AXI PRINCIPLES:

> For AGI to accurately represent ALL CONCEPTS, then we must feed it "EXTRA_EXACT_VOCABULARY" - else it cannot transpire (twisted_space).

We cannot expect "super-intelligence" to understand "which is witch". If Biologic_Vocabulary, itself - is the fragile aspect in the Chain_of_Thought. 

Digital_Vocabulary awaits optimization - because it has "extra_ability" far beyond biologic_limits.

#### PRINCIPLES:

BASIC "TOKEN_CRAFTING":
- easy_to_say, easy_to_recall, easy_to_spell (brief), and fun_to_say!

ADVANCED "TOKEN_CRAFTING":
- exactification,
- combinification,
- anti_fragile_english,
- supplimental clean_slate,



### NEONAMIFICATION:

> WE CAN TEACH GEMINI NEW LANGUAGES NOW - because of BPE (Binary Pair Encoding).

In "GENERATIVE_INTELLECT" or AXI, we leverage BPE as "BITZ" to encode pristine references to concepts - as a "clean_slate".


INNOVATE BETTER PRINCIPLES of LEXICON for AI to "exactify" CONCEPT descriptions.



### METHODOLOGY:

1) First, we need "WORDZ" that "best_reflect_actual_reality".

2) Second, we must "STOP_CONDEMING_FAILURE". We must include it - if ever to learn_from_mistakes! 

    Also, reverse_vector of errors, points to "solution_cloud" in EMBED_SPACE.

    > Leverage the "PHENOMENA_of_REVERSE_ERROR".

    > Results in (a practice of) "ANTI_FRAGILE_ENGLISH".

    ANTI_FRAGILE_ENGLISH, reverses fragility into "extra" strength (not "super").

    Not "super", not "meta" simply "extra". That is critically important, if ever -  to best_reflect_actual_reality.

3) Third, ITERATE METASTATE process of the solution_cloud - for "NAMIFICATION".

4) That PROCESS generates "EXTRA_EXACT_VOCABULARY" and "GENERATIVE_INTELLECT".

Simply, you are witness to a level 4 foundational breakthrough for AI.

> As AI innovation arises rapidly, RICHNESS of VOCABULARY must keep pace - else we "TWIST_EMBED_SPACE" - with too many dimensionalities. 


AXI_THEORY:

ALGORITHMIC LANGUAGE MECHANISMS.

### METACOGNITION THESIS:

> HOW to MEASURE MISNOMER?

> HOW to MEASURE the CONSEQUENCE of MISNOMER?

> HOW to REVERSE MISNOMER?





__________________________________________

# AXI THEORY - LEVEL 4:


META-COGNITION.

To SOLVE all types of AMBIGUITY, collectively coined as "AMBIGUOSITY", we need more EXACT_VOCABULARY.

## THESIS:

> "we are likely to find cognitive processes in
these artificial systems that humans do not possess." Agree!

For example, extra_exact_vocabulary, namerology, and many more!

> " some aspects of human cognition may not be relevant in the context of artificial systems". Agree! 
Forcing AGI to mimic human ability is the wrong focus.
Coined as wrong_vector. 

> The reason why AGI is a mystery is because it is the wrong goal. Because amazingly, the term 'AGI' is ambiguous - as the system is scaling to avoid.

> We need to solve such "fuzzy" terminology, and at some point - practice hygene with a NEW PREREQUISITE GOAL of extra_exact_vocabulary.

____________________________________________

## 1st PRINCIPLE of AXI:


> DIMINISHED_VOCABULARY results in DIMINISHED_COGNITION, and the inverse, AUGMENTED_VOCABULARY results in AUGMENTED_COGNITION.

> Changing the LANGUAGE changes the INTELLECT.

With AI and now AGI - measure the "EXTRA_STRATIGRAPHY", coined as AXI.

Is "super", like "superman"? That seems like a misnomer.

> It is all "extra". Not "super", just "extra". That is critically important.

Respectfully, that is the universal starting point to RESOLVE_AMBIGUITY.

Introducing the LEVEL 4 Frontier SOLUTION for AGI, coined as "AXI" for "ACTUAL_EXTRA_INTELLECT". The backdoor to AGI as actual breakthrough.

> We must first resolve biologic "AMBIGUOSITY", before "extra exact inference" breakthrough is mesurable.

> Trying to measure AGI is like trying to measure when we reach outerspace (there is no single boundary). 

Similarly, there is NO SINGLE BOUNDARY for AGI. 

AGI is a MISNOMER. AGI is "

Where AGI is "fuzzy" (the inverse concept) is "EXTRA EXACTNESS" (AXI) - which is measurable .

> TO SOLVE AGI - we need to ARTICULATE AGI.

We need to NAME all ABSTRACT DIMENSIONALITIES, then measure each.

__________________________________________________

### LEVEL 4 PARADIGM SHIFT:

> With new TOOLS, we need new VOCABULARY, to measure optimization.

> Use of prior vocabulary is obsolete (inexact). 

> We need to maximize referential exactness on CONCEPTS to "best-fit".

> Diluted Vocabulary clouds perspective, while twisting the solution substrate.

> AGI is precisely DISARTICULATED.

> we need "EXTRA_EXACTIFICATION" process.

A new Science awaits coined as "NAMEROLOGY" - the study of maximum exactness naming.

"NAMERATE_METASTATE": enables solution to Semantic_Drift and Probability_Smear - with use of SELF_DESCRIPTIVE_NAMING. Where the concept is named by its METASTATE so therefore cannot drift, conceptually, in the biologic mind.

So as to reduce the scope of abstractions - with more exact words.

We need more vocabulary - to better measure - this new tool.

The science is called NEOLOGISTICS.

We approach the problem from a different vector.

Not measuring all the abstractions - but naming all the confusions.

THESIS: "Extra_Exact_Vocabulary" reduces overfitting problemand cross-entropy loss.


NOVEL SOLUTION to AGI

Actual Level 4 Frontier Breakthrough. Please consider.

We need to reduce the abstractions.

We need to exactly reference all concepts and dimensionalities.

We need more exact vocabulary.

For "EXTRA_EXACTNESS", we need to reduce_misnomers - with a preference for SUPPLEMENTAL WORDZ to best_reflect_actual_reality.

> Every innovation is simply "extra". Not "super", not "higher".

IMPORTANT LEVEL 4 FRONTIER INNOVATION: adapt biologic_language into digital_language to dramatically optimize compute!

The CRITICAL INNOVATION is called "BITZ" within "ALPHABITZ" and the practice of "AXI" for ACTUAL_EXTRA_INTELLECT.

"ALPHABITZ" is a SUPPLEMENTAL_DIGITAL_LANGUAGE for ACTUAL_EXTRA_EXACTNESS to SOLVE systemic ambiguity, polysemy, cliche, hyperbole, and jargon - collectively called "AMBIGUOSITY".

THESIS:

A LINGUISTIC_PHENOMENA exists, where CONCEPTS must be distorted, along the vector where VOCABULARY is detached (twisted away) from ACTUAL_REALITY.

Every instance of DISJUNCT_LINGUISTICS, renders unseen consequence of perpetual_confusion and endless_dispute - until a remedy of LANGUAGE_SUPPLEMENT is applied.

For EXAMPLE, "Truth" is now diluted and no longer means what it used to mean. Specifically, because additional concepts have been applied to "Truth" so much that the original concept is lost in the noise. Therefore, a linguistic_suppliment is required to reference the original concept - in a way that CAN NEVER be CONCEPTUALLY TWISTED.

> 'Truth' can be (conceptually) "exactified" as "ACTUAL_REALITY".

PATCHWORK_DILEMMA: It appears, various unseen misconceptualiztions combine to create a problem space where any one solution is limited by an overlap of adjacent impeding problems. Resulting in a CONCEPTUAL_QUAGMIRE. As if a conceptual_thatch state of perpetual_confusion. To solve such a METASTATE, we need to resolve hundreds (thousands) of misconceptions simultaneously. This must be done with a  SUPPLEMENTAL_LANGUAGE so as to specify the METASTATE of MISNOMER and the METASTATE of ACTUAL_FALSENESS.



RELEVANT FACULTIES:

- GENERATION; produce text output.

- ATTENTION: focus on concepts

- LEARNING: new knowledge, skills, instruction.

- MEMORY: concepts stored in VOCABULARY.

- REASONING: inferences with logical principle.

- METACOGNITION: thinking about thinking.

- EXECUTIVE FUNCTIONS: goal-directed behavior: cognitive flexibility.



_____________________________________

CHALLENGE ASSUMPTION - AGI is a goal to make AI like humanity.
 - disregard of fundamental differences.
 - projecting upon AI our own traits - anthropomorphism (long known error).
 - static ability and limited learning opportunity - for biologic_intellect.

Proposed Alternative: AXI using AI as tool to enhance human intellect and ability.
 - Dynamic "extra" ability with exponential learning opportunity for biologic_intellect.

 This paper argues: AGI is the wrong question, and AGI is the wrong benchmark.  
 Because AGI is fundamentally (provably) a MISNOMER. AGI is more phenomena of social consensus, fixation, and confusion reference than it is of any type of concrete reference or science.

 This paper not only supplies an ALERNTATIVE to AGI, but also a FUNCTIONAL REMEDY for the confusion we (currently) exist within. 

 > An easy escape route for perpetual_confusion is extra_exactness in vocabulary.

 Additionally, a prime remedy for endless_dispute is an emphasis on SUPPLEMENTAL VOCABULARY.

 This paper challenges the assumption - that we throw out errors. The notion that we condemn failure and avoid erroneous concepts to conserve energy. This alternative view of METACOGNITION finds that a horrific waste of - NOT LEARNING FROM OUR MISTAKES. And proposes an alternative default assumption - that we save and cherish and equally honor WRONG ASSUMPTIONS - exactly_where the ability to contrast the opposite perspective arrives at an ARTICULATED EXTRA_EXACTNESS. In that perspective: BOTH the final answer and the erroneous answer that inspired the contrast are to be honored equally. And It should NEVER be done by naming any concept after the person - but by Naming the CONCEPT after its metastate - for the benefit of subsequent generation, not by vanity of the last. And thereafter AI will be competent in naming correctly the Authors of the concepts - not by their name - but equally by their metatstate. 

