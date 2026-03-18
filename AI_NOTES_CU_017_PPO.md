# PPO - DPO, GRPO:

- Pretraining, Reward, 
- Inference
- Optimization

- Policy
- Value

- Policy Proximity Optimization PPO
- Direct Policy Optimization DPO
- Group Relative Policy Optimization GRPO

- RUBRIC

> EVOLUTION from ORIGINS

______________________________________________

## PRETRAINING

before GPT.
NLP pretraining of LLM. 
Illustrative examples:
"Training Sequences"
Classification.
From Web.
Token Input.
EPOCH.
- Model is predicting next token - probability.
- Shifted Position is TARGET probability.
- Infereence Sequential.
- current token predicts next token.
- 
### GRADIENT UPDATE

Gradient Update ongoing.
Sampling Process. For Probability Distribution.
Feedback Loop. Process. Sequential. - Not done in parallel.
Sampling Process.

### BEHIND THE SCENE.

PROBABILITY DISTRIBUTION.

REWARD MODEL.

## Generalized Advantage Estimate (GAE)

Sample Scentence - into Reward Model.

hire EXPERT. Look at PREFERENCES.

PRE GPT. 

REWARD
- Reward Discount Factor gamma (discount of future rewards)
- trace decay lambda (decay of trace overtime) 

Value Model 

Callculate Error:
Temporal Difference Error TD Error.
Subtract 1 score from the last score.
DISADVANTAGE.

### PROXIMITY

Policy Proximity Optimization PPO
Poximity of TRUST.
Dont over change. 
Dont over fit.
Dont over optimize.
Dont UNDER OPTIMIZE
Negative dissappointment
Positive Surprise
calculate difference.
Avoiding some things.
Learn how to avoid milk.
CLIPPING and LOSS.
Loss function.

## DPO

Direct Policy Optimization

Before GPT - hire experts.
collect feedback.
Feed to the Network. 
accepted / rejected.
Looking for positive feedback.
Penalize negative feedback.

DPO contains penalty.

ONE NETWORK - two different versions.
TWO POLICIES.

## GRPO

Group Relative Policy Optimization

IMPORTANCE SAMPLING RATIO

Pay more attention to signal.
Pay less attention to noise.
Pay less attention to signal.
Pay more attention to noise.

Appreciate ability to see different policies.

LLM can be SIMULATOR - with RUBRIC.

LLM simulates humans preference.

_________________________________

### INTERVIEW

Cameron Wolfe interview. (Netflix)

beat others without being beaten.

learn patterns over time to learn process.

Clear reward / value functions.


RL in LLM.

RL in Robotics.

LLM - focus on curating Supervised Learning.

Scaling up.

Training differently.

Trial and Error - reward / value functions.

Let model explore to define the correct answer.

Allow it to show REASONING.

REASONING MODELS.

### CHALLENGES

RL RESEARCH - difficulties.

- EFFICIENCY
- Small Scale to Large Scale.
- Scoring
- Policy update
- cComplex Pipeline.
- Leads to bottleneck.
- Difficult Systems Problem.

LONGFORM POSTS DISSERTATION. NEWSLETTER.

SUMMARIES.

RELATED WORK SECTIONS.

### RLVR:

DPO is offline.

Prompts - to Scalar Reward - Completions.  Plus Policy Update.

RLVR - Reinforcement Learning from Verifiable Rewards.

1 Model Input to Reasining Model. 

Less prone to Reward Hacking.

Key idea Enables Large scale RL training.

Power Laws for Compute.
Is RLVR enough?

Fuzzy Domains.

2 Apply Verifiable Domain to Non Verifiable Domain.

RLHF - before GPT. 

collect dataset prompts.
best picked - PPO reward model.
Scalar Score.
Run RL PPO.
Preference Dataset Chosen Response Rejected Response.
Preference Pair. Good vs Bad.
Correct vs Incorrect.
OPTIMIZE for preference.

LIMITATION RLHF

Lots of data
only as good at reward preference.
overfitting to artifacts.
reward hacking.
finding exploits in reward function. 
rather than actual training.

Preference Data.
Not control over optimization quality.

### LLM as JUDGE.

Commmon to evaluate LLM.

"Can you tell me if this is good or bad?"

System is simple ask to evaluate.

### Several Biases.

1. Verbosity Bias.

2. Position Vias.

3. Self Enhancement Bias.


AWARE and HEDGE against Biases.

- Capable JUDGES.

High level of reliability.

Check list of Evaluations - with score.

Provide more and more details.

RELIABLE.

### RUBRIC:

specific checklist to evaluate responses.

contain 7 - 20 objective quality criteria.

LLM aggregates scores.


### RaR Rubics as Rewards.

Constitutional AI 
Deliberative Alignment,
RLAIF (google)

Very safety focused.

Training Generation.
Inference Time.

Reward Signal.

### EXTENDED

Rubric as Reward.

LLM Judge output is reward for training.

_____________________________________________

Issues with 

reward hacking.

bad judge.

evolve rubrics.

Or specific rubric for safety.

OpenRubrics
Dr. Tulu

Results vary by domain.

Deep Reseearch Agents.

TRAINING PIPELINE.

smaller and cheaper and beginning to be impressive


### CONCLUSION

RLVR - large scale.

Open Research Question.

Rubric based RL.

LLM and JUdge - active researdch.
EEEP LEARNING FOCUS.

DEEP (LEARNING) FOCUS.

_________________________________


Cost implication

linear or sub linear.

Rubrics many approaches.


Alan Institute for AI - open research lab. LNAI
All code model weights data.

