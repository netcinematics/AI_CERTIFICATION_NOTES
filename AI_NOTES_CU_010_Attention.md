AI_NOTES_CU_Attention:

FOUNDATION Attention and FRONTIER SLM.

Small Language Models for efficient Agentic Tool Calling.

OPT-350M - AWS

DeepSeek OCR

Facebook OPT

ToolBench-style SFT (supervised fine-tuning)

ToolBench

Token Embeddings

Decode

Stability - single epoch.

___

Pre-training.

Scenario to Token Sequence.

BOS - Begining of Sequence

EOS - End of Sequence

_____

Attention is all you need - introduces Transformer (GPT).

3 Attention Blocks. Scaled Dot-Product Attention. 

Latex: QKV softmax(QK^T / sqrt(d_k)) V

Q - Query
K - Key
V - Value
W - Weight

Query pays attention to Key and Value.

MatMul -> Scale -> Mask(opt) Softmax -> MatMul

Matrix Multiplication is lot of dot products.

SCALE:
dimensions of a key.
Take square root of it.

SOFTMAX normalized.

results:
PROBABILITY DISTRIBUTION

Use value to get weighted sum.

Attention matrix contains percentages of attention.

Combine Tokens to get new tokens.

___

MULTI-HEAD ATTENTION:

(QKV)t transposed, 

different sets of weights. Weight values are different for each head.

QUERY: if you see the word "eat" - what do you want (consume)?

KEY: if you see the word "eat" - what do you give (food)?

VALUE: if you see the word "eat" - what does that mean (action)?

VA1 - value attention 1
VA2 - value attention 2
VA3 - value attention 3

(concatenated)
Attention Weighted Value
New token is combined result of all attention heads. (concatenated

Pass to next layer. 


model size 8, 512, 768, 1024.

Linear Projection 12 - to 8. Final Output Projection.

Tons of matrix multiplication under the hood.


__________________________________________

FRONTIER:
GDPL PPO PR DPO

FOUNDATIONS: TPU