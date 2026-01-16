AI_NOTES_CU_SLM:

_____

SLM

DEEP SEEK OCR (Optical Character Recognition):
SLM (dense global attention).
INPUT - whitepaper (pdf).
DEEP ENCODER:
SAM stands for Self Attention Module 
- local window attention perception (tokenizer).
CONV - down-sample conversion (16x).
VISION TOKENS - n/16 (low activation).
CLIP - stands for Contrastive Language Image Pre-training
- dense global attention.

Training Metrics:
- Vary's "compact language model"
- next token prediction framework - to train DeepEncoder.
- OCR dataset
- plus 100M general data sample from LAION dataset.
- 2 epochs,
- batch size 1280.
- AdamW optimizer
- cosine annealing scheaduler
- learning rate 5e-5.
- training sequence length 4096.


____


AWS: limited by data not architecture.

more data better, noisy labels, mismatches.

Question Response Pairs : training data.

    1) Ambiguous - if overly verbose or overly confident - should be modest and ask for clarification.

    if not controlled verbosity and confidence - can be dangerous.

    overly long and confident - and incorrect.

    2) evaluation mismatch.

    what users want and loss function does not align.

    helpful, trustworthy, and safe.

    offline metrics. accuracy of task, but less aligned for users.

    user expectations.

    3) LLM DEBUGGING.

    inconsistent reasoning - not obvious - not easy to catch.

    can happen at any level of training. Training is large system.

    Really hard to debug.

    _____

FRONTIER: Agentic Tool Calling.

    SLM - Small Language Models


Role for SLM in Agentic workflow - more efficient.

OPT-350M - AWS - 350M parameters - 100x smaller than GPT-3.5

- 100x smaller than GPT-3.5
- 100x faster than GPT-3.5
- 100x cheaper than GPT-3.5

OPT - Facebook OpenAI Tool 


Compact Language Model. - text image alignment.


2 heads of attention.

Causal Mask. Cannot pay attention to head infront.

Lower triangle things in future.

350 million trainable parameters.

Feed Forward Network.More feed forward networks. 

Routing mechanism.  MOE - Mixture of Experts.

Model gets really bit.

200k vocabulary.

softmax(200k).

Much larger than 52,000K parameters.

Attention Layer

Feed Forward Layers (hidden).

- when increase context window, goes up - weights do not change.

Everything scales to more context window.

grow quadratically. 

____

### "toolbench" supervised fine tuning:


1. Pre-training - fluency, task to complete (next most likely word).
2. Instruction Tuning - System | User | Assistant | - helpfuls, trustworthy, safe.
3. Tool Calling Tuning - System adds Action: tool call currency_convert, input params
    - observation: to assistant for output.

SLM for tool calling tuning. No need for LLM in that 3rdstage.

____

SENARIO to TOKEN:

flatten maessages to single flat sentence

Text Join.

Split into tokens.

Tokenize.

Feed to model to fine-tune.

Token Embeddings:
vocabulary - ID lookup table.
from token to embedding.
use lookup table to go from embedding back to token.

Linear Model could be Transformer, with Feed Forward Network.

Linear Projection Model - finds most probable word.

Perplexity - many possible words. Should be only 1.

Loss Function - how close we are to the correct word.

capture low number of perplexity back to 1 perplexity.

Negative Log Loss function. high rate of loss of next token.

Probability higher, loss is smaller. 

Only need a subset of tokens for took call.

Mark as 1, 1, 1, 1. as MASK. 

Only select Assistant tokens for loss.

Masked Loss. 

Sum of total Loss.

Cross Entropy Loss math.

"only train this part" - for tool calling.

Do not retrain: USER | SYSTEM parts.

____

Single Epoch - can do this by dense revision - every token of loss.

we know exactly which tokens are next. Dense High-Quality performance, small.

Train for patterns not fluency.

Pattern picks the tool.


___

WARMUP:

adjust weights to get better performance.

loss gradient. to get new weights - gradient descent.

1 - learning rate (classic gradient update)

 - Learing Rate Schedules (0.1, 0.01, 0.001)

gradually increase learning rate, into desired learning rate.

- one epoch. 

One chance to influence weights.

gradually ease training into desired learning rate.

____





