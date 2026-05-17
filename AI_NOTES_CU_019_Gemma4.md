AI SLM - GEMMA 4 - FRONTIER

- EXTEND in different DIMENSIONS.

TENSORS & VECTORS.

Query Key Value.

Weight - trainable

Weight - not-trainable - compute

WK*x
WV*X
WQ*x

dot-product TRANSPOSE.

REORIENT into new FORM.

dot-product COMPARISON - essence of attention.

pair-wise ATTENTION comparison.

SIMILARITY MATRIX.

SOFTMAX - similarities score. 

Convert into probability distribution.

WEIGHTED AVERAGE - sum of all values.

Weighted average - value information.

ATTENTION WEIGHTS.

OUTPUT = ATTENTION WEIGHTS * VALUE.


QKV - ATTENTION.

ATTENTION WEIGHTED SUM TOKEN.

____________________________________________________

QUADRATIC GROWTH - grows by 4.

Computationally expensive - most expensive.

How to keep open.

Causal Attention - can only look back, not future.

MASK COMPUTE BY -1 \ LOWER HALF LINE all -1.  SKIPPED dot product.

SAVED INTERPRETATION.

GLOBAL ATTENTION - ALL to ALL

CAUSAL ATTENTION - MASKED by -1 in lower half of SIMILARITY MATRIX.

LOCAL ATTENTION - ONLY WINDOW OF TOKENS. (NEIGHBORING).

GROUPED QUERY ATTENTION - MULTI HEAD - GROUPED

Different MASK! GRID MASK - excludes corners (skip connections).

MASK ATTENTION - looks like GRID.

GLOBAL ATTENTION - attention to everywhere.

CAUSAL ATTENTION - pay attention to past. ('NOT')

ALTERNATING ATTENTION LAYERS GLOBAL + CAUSAL. (GEMMA4)

Why alternating - so it does not repeat itself.

EXPENSIVE COMPUTE! Attention.

BEST OF BOTH WORLDS - GLOBAL + CAUSAL. (INNOVATIVE)

MASK saves compute in CUDA level!

Why innovation matters? Cost cutting!


____________________________________________________

KVCache

cache grows with context.

GEMMA 4 saves KV.


DECODING - no cache

DECODEING - with KVCache. KEY and VALUE stored in memory!

Faster & Efficient!

MATRIX MULTIPLICATION OPTIMIZATION.

QKV = GEMINI 1.5

QKV - No Repetition 

KV KACHE = Speed & efficiency

NO GEMINI - Just attention innovation for latency.

NO INNOVATION

INNOVATIVE!

QKV PROJECTION - OUTPUT DIMENSION! (PROJECTED).

> KEY and VALUE - into CACHE (KV Cache).

PROJECTION SAME DIMENSION OUTPUT.

If new Key & value - just add to KV Cache.

Then compute cache Q -> cache K -> Softmax -> Value -> Output.

Otherwise avoid MATRIX MULTIPLICATION (Compute Cost).

Token Layer - enriched - KV Cache - for attention (save lots of DOT PRODUCT).

Computation Savings is Significant! (Massive).

deep seek - compresses KV Cache.

What to do when hit ceiling: TRUNCATE or COMPRESS KVCache!


____________________________________________________

MIXTURE OF EXPERTS (MOE)

SPARSE MOE.

EXPERT? - FEED FORWARD LAYER - in TRANSFORMER.

Mixture of EXPERTS in FFW of TRANSFORMER.

Not all experts compute - only TOP 2.

Efficient Compute!

Only 2 of 8 compute!

TRICK: transform to HIGHER DIMENSIONAL SPACE.

Then project down. (Efficient).

Projection from 192 -> 768 -> 192. (4X).

GEMMA 4

EXPERT - ROUTER - NETWORK - 

SCORE per EXPERT. WEXPERTS.

SOFTMAX turn SCORE into probability distribution.

RANK and MASK - top 2 experts. (Efficient).

Mask tells CUDA - how to FEED FORWARD. (Parallel Processing).

OUTPUT = Top 2 Activated. Weighted Sum. (Weighted Average of ACTIVATED EXPERTS).

OTHERS do NOT ACTIVATE at all. (Sparsity).

Computation: 2 * EXPENSE (not 8 *) of GEMINI 1.5 MoE.

Only 12 - at first.

Choose 8 experts always on.

GEMINI 1.5 - 16 experts - choose top 2 (sparse).

GEMINI 1.5 - does NOT save much compute!

_____________________________________________

MIXTURE OF HEADS

SIMPLIFIED MULTI HEAD ATTENTION

GROUPED QUERY ATTENTION

K, Q, V shared for all heads. (Efficient).

GEMINI 1.5 - separate K, Q, V.

__________________________________

MIXTURE of EXPERTS 

MATRIX SUM of MIXTURE into SIMILARITY MATRIX!

___________________________________

INPUT EMBEDDING - (second biggest weight matrix)

Trained EMBEDDING MATRIX.

Vocab 200K - GEMINI 1.5 (BPE)

Vocab 64K - GEMMA 4 (BPE)

Simple lookup - for Embedding MATRIX. Not a MATRIX MULTIPLICATION!

Choose column - by token index.

RESIDUAL STREAM (Input Embedding Matrix)

"ATT" adding residual. and "NORM" normalize layers reintroduce.

BIRTHDAY CARD METAPHOR. My teacher has birthday, all students add message and pass on to next student. (Adding Messages)

RESIDUAL STREAM!
_____________________________________________

While in TRANSFORMER - feed forward network is

ADDING to RESIDUAL STREAM.

So there's no information loss.

Size of birthday card is MODEL SPACE.

Smaller means MESSAGE LOSS.

Sometimes re-introduce "OLD" information. (Residual Stream).

Reintroduce at LAYER NORM!

LayerNorm Normalize.

------------------------------

LoRa - lower rank.

Inference time - no cost.

Only used during TRAIN time.

When shape do not match - "UP PROJECTION" / "DOWN PROJECTION".

LoRa = "DOWN PROJECTION" -> "UP PROJECTION". (Efficient).

Split W into W1, W2, W3, W4.

LoRa = Additive matrices.

SIGNIFICANT savings in parameters for Training.

__________________________________________________

DYNAMIC Lo-Rank Layer Embedding

hidden value to predict embedding size.

Birthday card size is always the same.

COMBINE: static low-rank + dynamic size embedding (LoRa for Embedding).

FRONTIER RESEARCH FOCUS.

----------------------------------------

LIKE FLIP BOOK ANIMATION of BIRTHDAY CARD: adding messages.

Across the layers. Year after year added to it.

FINAL CARD = SUMMARY OF ALL YEARS!

Attention: "WHO IS IMPORTANT THIS YEAR"? (Global Attention) -> Add those messages.

Last 30 Days: "WHAT JUST HAPPENED"? (Causal Attention) -> Add only last 30 days messages.

(Weight = How important that message is).

---------------------------------

RESIDUAL NETWORK is most cited - deep neural network architecture.

From FLIP BOOK

_____________________________________

Per layer embedding.

Sometimes input is lost.

- expensive compute,

- difficult to train

- drifting.

Process of ADDING INFORMATION BACK.

ROTATIONAL POSITION ENCODING (QWEN)

Rotary + ALiBi = Innovation in Position Encoding.

GEMINI 1.5, GPT = Use ALiBi.

__________________________________

RESNET - RESIDUAL NETWORK (10 years ago)

Followed by ATTENTION TRANSFORMER.