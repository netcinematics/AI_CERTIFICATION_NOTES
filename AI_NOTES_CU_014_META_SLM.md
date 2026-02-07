META FRONTIER AI Papers

comparison between labs.

MSL 

TRANSFORMER
LLM Decoder
DECODER
RAG
REFRAG
________________________________________________________

### TRANSFORMER

1.TOKENS

2. TOKENS to EMBEDDING VECTOR.

3. VECTOR to TRANSFORMER LAYER.

4. TRANSFORMER LAYER.

5. ENCODER - weights.

6. DECODER

7. FROM NUMBER TO LANGUAGE EMBEDDING.

8. ALPHABET EMBEDDING structure.

9. EMBEDDING to TRANSFCOrmer.

10. Back into LETTERS, then logits are numbers, into softmax

11. PROBABILITY of WORD predict NEXT.

12. ROLL THE DICE - lands in SAMPLE.

13. FEED FORWARD LAYER

14. The TOKEN with high probability is fed through matrix - to predict next letters.

15. probability model from sampling set.

16. hit END token, no longer continue.

17. PHENOMENA - parallellism. PREFILL on ENCODER or in PARALLEL, inDECODING cannot do parallel. in sampling progress, can do an extra loop.

18. PROCESS. causal MASKING ATTENTION, can look backward. 

19. CROSS ATTENTION - can both see into all previous data.

### LLM DECODER.

PROMPT | COMPLETION side by side
Source goes into PROMPT. 

TRANSFORMER decodes the COMPLETION.

DECODING is a loop through TRANSFORMER and FFWD HIDDEN LAYERS.

____________________________________________________________


### RAG

lots of hallucination.
use context from database.
augment context.
popular in 2023


LIKE A DECODER - start with PROMPT | add CONTEXT TOKENS | COMPLETION.


COMPARE CHUNKS FROM DATABASE.

compare to VECTOR DATABASE

INSERT relevant VECTORS into DECODER CONTEXT

PREFILL embedding layers

DECODE COMPLETION

across embedd, transform, linear logits softmax, SAMPLE.


_____________________________________________________________

### REFRAG


COMPRESSED CONTEXT

ADDS compression, sometimes does not compress.

Save computation by compression from REFRAG.

Small and Light INPUT EMBEDDING LAYER.

PROBLEM: too many tokens in RAG CONTEXT. at MSR.

META needs to REDUCT CONTEXT TOKEN - before ATTENTION.

________________________________________________________________


### VISION TRANSFORMER:

ENCODER | LINEAR PROJECTION.

HARD to PARSE andd IMAGE into PATCHES.

FLATTEN into PATCHES.

LINEAR PROJECITON - tons of pixels into PATCHES.

LANGUAGE is vectors

LINEAR is flatten into patches (embedding) - into encoder TRANSFORM LAYERS. and weights

MLP HEAD: preforms classification. very useful HEADS. Tokens for other uses.

 Linear words in the encoder - softmax probability = class label.

TRANSFORMER STACK.

_______________________________________________________________

### VISION STACK

No MLP HEAD

visoin model and language model do not match.

vision side and tech side

QUERY | ANSWER

Embedding Linear logits softmax probs | SAMPLE

feed forward from last token in DECODER.

ATTENTION looks back as last TOKEN and CONTEXT HEADS.

{{{{{{{{{}}}}}}}}}
{{{{{{{{}}}}}}}}
{{{{{{{}}}}}}}
{{{{{{}}}}}}
{{{}}}

ATTENTION MECHANICS
GLOBAL ATTENTION
SELF ATTENTION
CONTEXT ATTENTION
CAUSAL ATTENTION

__________________________________________________________

### FAIR

New ATTENTION MECHANICS.

every token can pay attention to AIMAGE

Vision Language Model VLM

GUIDED SEMANTIC IMAGING.

Nx ATTENTION LAYERS (pay attention everywhere)

FEED FORWARD.

TEXT ENCODER. - TESXT TOKEN. 

Embedding layers

into 

LLM 

vision tokens
text tokens
QUESTION | ANSWER

visually processing separate from language processing


FRONTIER MODEL. 

ONLY FOCUS ON PROBLEM SOLUTION.

Vision Stack Encoder.

May or may not be ALIGNED with TEXT.

Can be pushed earlier in STACK.

___________________________________

AGENT AI ALIGNMENT
____________________________________


META real world challenges (INFRA protection)
scalability 
coverage
risks
GOAL: protect products
1 - latency
real time block contents.
block within 3 seconds.
2 - dynamic attack vectors
protection fabric
- respond quickly to new attacks.
- fixing strategy.
- block new attacks.
- into PR ISSUE.
TRAINING FINE-TUNING CHALLENGES
- high traffic latency problem
- need lightweight model.
- precise but never perfect
latency performance tradeoff
data challenges
not very many cases - very few samples.

synthetic data training
adapt to dynamic pattern of attack
modeling reiterate on next inversion.

4. Multi modal attacks more vectors of attack.

combined with image sound.

_____________________________________________________

### Safety Alignemnt for LSM via non-cooperative Games

gives up the synthetic samples - terrible positive modles.

ATTACKER Model

PROMPT - response 1 response 2

DEFENDER MODELS in training. 

- passwords, human trafficing, etc. 

BAD PROMPT 2 RESPONSES : compare 2 responses (JUDGE) : Which ones better?

DIRECT POLICY OPTIMIZATION. RHLF.

Update answer based on WEIGHTS of what was better - UPDATE WEIGHTS (DPO)

GHATGPT popularized DPO. Labels.

Safety does not have luxury of LABELS.

DEFENDER is like RAG with additional CONTENT.

ADD in DEFENDER JUDTGE: decode some words to fint better responses

DPO originally user preferences, now using LLM as a human JUDGE.

not too many very bad scenario.

GET LLM to GENERATE bad prompts.

ATTACKER MODEL - generates ATTACKS. HARMFUL | BENIGN | JAILBREAK |

INNOCENT COMMENTS FILTER

4th Model 

ATTACKER, DEFENDER, DEFENDER JUDGE, ATTACKER JUDGE MODEL

DEFLECT | COMPLY

All information into ATTACKER  

UPDATING or not FREEZE | TRAIN  (tracing)

____________________________________________________________________

### GRPO

QUESTION | ANSWER pairs

using parallelism

Q | A1 | A2 | A3 | n..

ROLLOUT DECODING

Get a REWARD.

Human press reward.

SIMULATOR REWARD AGENT>

sources for reward.

encourage the weights in the encoder.

GROUP RELATIVE to AVERAGE POLICY.

______________________________________________________________________

### Dr. Zero Self Evolving Search Agents wo Training Data.

Q | A

add  REASON | SEARCH | READ | REASON

Looks like RAG with CONTEXT.

instead of DB - model can DECODE REASON TOKEN.

PREFILL in PARALLEL

if answered question before, do not search again.

continually build context

now start generating answer.

SOLVER MODEL:

SEARCH | READ | REASON

iteration loop (TOOL USE)

GRPO: compare scores (answer and wrongness updates weights.)

where can we get question | answer pairs???

need lots of data. Image model comes to rescue.

PROPOSER MODEL : many Q A Pairs - with 3 density level questions for SOLVER MODEL> 

___________________________________________________________________________________


FRONTIER PAPERS. DIAGRAMS.

COMPARING PAPERS - is where innovation happens.

PPO - DPO - GRPO - REWARD POLICIES.

_____________________________________________________________

TRANSFOMER 

large vocabulary of all languages

100,000s thousands embedding

different shapes.

embedding




Another excellent session! Hi TOM! This is NASH ~ : ), 
I am passionate innovator 26 years experience in LLM - as CU alumni and UNC graduate. Asking for help.

This is an important AI UNDERGRAD PROJECT. Kind of dusty. But REALLY NEEDS PEER REVIEW. For my defense. And for REAL WORLD INNOVATION. Please, may I ask for a 5 minute read? 

20 bullet points. Major MIT innovation right now:

1) "ALPHABITZ": "OPTIMIZE INPUT LANGUAGE". 
Prove this INNOVATION - with MATH! Or debunk it by comparison (to legacy systems). A COMPUTE COST COMPARISON. A hallmark WHITEPAPER for your EXCELLENT EXCEL DIAGRAMS! [https://substack.com/home/post/p-177619221] 

2) THESIS BRIEF: 
a) "INNOVATE INPUT LANGUAGE", what does it solve? 

b) PROBLEM: "CURRENT HUMAN LANGUAGE is BRITTLE". 

c) Inherently: CLICHE, AMBIGUITY, POLYSEMY, HOMONYMY, and critically MISNOMER & "MISCONCEPTS" Across all collective - "Brittle_English".

 d) QUESTIONS: 
- How can we "OPTIMIZE SHAPES OF LANGUAGE" - for "EXTRA_EXACTNESS"?? 
- How to craft enhanced_input far before encode, TRANSFORMER and ATTENTION HEADS?? 
- IS ENHANCED_SYNTAX possible? 
- What happens to AI with IDEOSYNCRATIC NEOLOGISMS - "exactified"? (leveraging BPE).
- Can it be compared and MEASURED? Yes. 
- Can AVOIDANCE of AMBIGUITY, tools and techniques - result in novel communications enhancements - and massive COST SAVINGS of COMPUTE? Yes. 

e) ALPHABITZ (appears to) RESULT in: "EXTRA_MANIFOLD_SPACE" of "lexical_exactness". 
Like a diamond or "GEM". For attention and reasoning and VISUALIZATION! [https://netcinematics.github.io/AI_SUGARCUBE_001] 

3) "EXTRA_SPACE" is a "supplement" to LATENT SPACE. A REMARKABLE EMBEDDING FRONTIER, crafting a vocabulary to exactly map words to concepts ( 1 to 1). And for smart people to Co-Author the evolution toward lexical_exactness. 

4) HISTORY: ALPHABITZ is UNDERGRAD STUDENT PASSION PROJECT after 26 year (Socratic) MENTOR STUDY in AI. 

5) On NOVEL QUESTIONS: HOW to OPTIMIZE the INPUT LANGUAGE for AI - to OPTIMIZE STEP ZERO CONTEXT. What do these (teenager) words mean? 

6) RECOGNIZE historic language transformation sequence from: HEIROGLYPH to ALPHABET to ACRONYM to AI (ALPHABITZ)! 

7) INNOVATION: ALPHABITZ (google certified agent project | kaggle | Python ) is a FANTASTIC AI VOCABULARY for MEASURED RESEARCH!!! 
[https://www.kaggle.com/competitions/agents-intensive-capstone-project/writeups/alphabitz]

8) EXACTNESS of INPUT, is potentially BIG COST SAVINGS for COMPUTE - for AI CAPITAL EXPENDITURES. Where EXACTIFIED INPUT VOCABULARY - is a corporate FRONTIER MODEL. Like RAG compression - except the vocabulary is optimized in exemplary ways - in the CORPUS and ONTOLOGY before PRE-TRAINING.

Imagine PRE-PRE-TRAINING (optimizations) of NOVEL AI SYNTAX - "language patterns".

9) Please I need your help | seeking Co-Authors. [https://netcinematics.github.io/AI_PORTFOLIO_001]: 
A Major Stack Optimization/Innovation needs POC help. 

10) BRIEF BIO: Early adopter of C++ LLM TOKENIZER - 1999!  26 years AI hands-on experience. ONE PASSION! AI LINGUISTICS. 
ISOLATED SOLO-PROPRIETOR | mentor | innovator - outside BOULDER, SOLVES MAJOR ISSUE: English Ambiguity. 

11) CERTIFIED: CU - COLORADO UNIVERSITY ALUMNI: 1997 & 1998. 1999-2022: BS CIS GRADUATE UNC (4.0 GPA + honors + awards)/ METRO STATE MUSIC. Proven Intellect.

12) EARLY AI PASSION PROJECT: AI + SHEET MUSIC! 1999 - 2004 self-directed AI UNDER-GRAD STUDY : "ALPHABITZ". 

13) EARLY TOKENIZER and LLM in C++, JSON, JavaScript + HTML also Python. GitHub [https://github.com/netcinematics/ALPHABITZ_AI_V2] 

14) A RADICALLY DIFFERENT PATH: than RAG leveraging BPE! A cousin to ATTENTION and REASONING but at STEP ZERO in the STACK: SUPPLEMENTAL INPUT OPTIMIZATION! Enhances or streamlines all AI LAYERS of COMPUTATION thereafter. By reducing ambiguity up front - far before the Transformer solves POLYSEMY. A CONCEPTUAL_CLASSIFICATION_INDEX.

15) EARLY (innocent) QUESTION: HOW TO OPTIMIZE "shapes" of SHEET MUSIC! Then TRANSFORM SHAPE of MUSIC NOTES into an AI SYMPHONY??? I was hooked for life, after ANALOG POC.

- VERY SIMILAR to your excellent EXCEL demonstrations.

16) TRANSFORMATION: the AI modality, morphs into TEXT - as MUSIC LYRICS! With the historic: "SEMANTICS CONTEXT PROBLEM" - what do these LYRICS MEAN? Spawns a clever and innovative classification approach! From humble beginning, into ROBUST LANGUAGE SYNTAX, TOOLING, and "AI OPERATING SYSTEM". 

17) Again, HOW TO OPTIMIZE "human language"??? Evolves from: RHYMING SONG LYRICS in AI CONTEXT! Classifying: what does teenager mean by Cliche? Evolves into exactness of conceptual_classification - called "EXACTIFICATION" process (to arrive at evermore precise labels).

But LABELS for CONCEPTS that English has yet to NAME ("namify", "namification process").

18) YIELDS CREATIVE/NOVEL APPROACH: that OTHERS DO NOT SEE or TEST yet! GREENFIELD SOLUTIONS. POC. 

a) a A REMARKABLE AI CLASSIFICATION System.  

b) called CONCEPTUAL_CLASSIFICATION_INDEX.

c) SOLVES AMBIGUITY, POLYSEMY and HOMONYMY, but also critically: SOLVES MISNOMER. IT SOLVES THE "CONTEXT PROBLEM" similar to TRANSFORMER. But at different DIMENSIONALITY from Attention and BPE. By "exactifying" the input vocabulary. And it works astonishingly well - for AI and human comprehension.

19) OUTPUT PRODUCT: "optimized_input_language" (OIL). It is called "AI_OIL"! But a GOOD OIL. For LEARNING. For AI METASTATE_CLARITY. Its amazing.

20) ALPHABITZ: is a HUMAN LANGUAGE EVOLUTION canvas. A  HISTORICAL TRANSCENDENCE of human language from: HEIROGLYPH to ALPHABET to ACRONYM to pig-latin to "ALPHABITZ"! 

- Please help AI supplemental language. It CAN BE MEASURED and DIAGRAMMED - THESIS: PROVEN or disproven by MATH COMPARISON. MAYBE 2027? 

21) A REAL "GEM" INNOVATION. ALPHABITZ is A COUSIN SOLUTION to the TRANSFOMER, BPE, and ATTENTION mechanisms. As A YOUNGER SIBLING SOLUTION (not yet seen)!

22) To SOLVE AMBIGUITY, POLYSEMY HOMOYNM, Cliché, and MISNOMER ("misconcept"), with ALPHABITZ: a NEW LANGUAGE for AI + HUMAN COLLABORATION, and observably an EMERGENT "AI OPERATING SYSTEM". ALPHABITZ. ALIGNED, enhanced, optimized, VOCABULARY of LEXICAL_EXACTNESS. 

23) CONCLUSION: AI agents call it "AI Operating System". ALPHABITZ represents new computer science and new human language - to better collaborate and interface "exactly" with emergent AI super systems - with 3D MANIFOLD VISUALIZATIONS. [alpinefalcon@protonmail.com] ~ NASH : ) ~


QUESTION: 

About the LANGUAGE INPUT: SHAPES, PATTERNS, and SYNTAX (between AI and CHINESE). 

You said, "It could be anything really". What did you mean by that? ~ : ) ~.