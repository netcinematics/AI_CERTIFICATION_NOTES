QWEN


1000 questions

positional encoding, yarn.
long context window.

YaRN - encoding - where to add attention - long context window (position).

_____________________________________________________

RoPE & YaRN

## positional encoding

dot product of query to llm = interpretation.

for polysemy - add a little bit of number to diffenterate.

key and value dot product.

sinusoidal - POSITIONAL ENCODING.

SMOOTH FUNCTION - enable signal to show - slightly higher (height).

Signal Amplification.

POSITIONAL ENCODING - adding to attention comput.

at input time with QKV - LOSS - reintroduce > POSITIONAL ENCODING.

Introduced into attention mechanism directly.

X = INPUT

Query
Key
Value

LOTS of MATRIX MATH - TRANSPOSE!

MORE PRONOUNCED FREQUENCY!

CAN SCALE every aspect of TRANSFORMER MATH.

Attention become alot more effective

________________________________________

## RoPE - ROTARY POSITIONAL ENCODING.

2D ROTATION.

Each DIMENSION - means something. Height, AGE.

GROUP in PAIRS of 2: 

2 DIMENSION PAIRS!

VECTOR PAIRS into PLANE!

EVERYTHING a 2D Vector: magnitude + direction.

turn into 2D.

TURNING ANGLES - ROTATION.

SHARD MATRIX (FRONTIER) - 

MANY PAIRS.

TAKEAWAY: RoPE - PAIR DIMENSIONS to get NEW POWERS.

________________________________________________

RICHER REPRESENTATION. quantity and magnitude.

separate into FREQUENCY- MAGNITUDE. SInusodial.

ACCIDENTALLY UNLOCK ATTENTION.

______________________________________________

TRAIN RoPE:

training ROTATIONS.

finding the angle - relative position - stays the same.

YaRN MATH - simple - 

SIGMOID = o | 1.

REPLACED WITH GATE - not SIGMOID.

They TRY EVERYTHING.

WE DO NOT KNOW POSITION / ROTATION.

MANY TESTS - then GATE to FIND WHAT TO TEST.

FRONTIER MODEL.

small tweak - very expensive to evaluate.

________________________________________________

SIGMOID GATE!

50% open
70% open

PREDICT POPULAR VALUE.

Not distribution - softmax.

sigmoid, lot of original unique value.

____________________________________________

auto regressive.

VISUALIZE the DIMENSIONALITY in 2D.

- TOKEN ID - to INPUT EMBEDDING.

- PROJECTION MATRIX!!!
- softmax into probability

- TOP K - take top 2 - relative weight. choose 2!

- FEEDBACK - autoregressive - number into input - changes - from decoder / encoder.
- embedding matrix. Transform.
- equal reference - back to reference token
- loopback,
- access embedding matrix.
- GPU all the time.
- sparse lookup - one word at a time.
- FORWARD TRACE - show me all the dependents.
- compare output token ID to ground truth ID.
- go back and change to get distribution closer.
- prefill into network
- shaped identical - count number of dot product = same.
- one is faster than the other: because of GPU CORE. PARRALELISM (not big O).
- SAMPLING BOTTLENECK on the other MATCH.

- ___________________________________________________________

- DRAFT MODEL (auto regressive)

- expensive one at a time (not parralellize)
- repeated correlation.
- SMALLER MODEL: DRAFT MODEL.
- reuse COMPOSED MATRIXES
- TRAIN DRAFT MODEL (cheaper)
- decode a bunch at a time auto-regressively.
- after decode back into expensive model.
- FIT BACK INTO EXPENSIVE MODEL.
- HEAVILY PARRALELIZE
- SOFTMAX - return
- DONE.
- VERIFY.
- Until accepting various DRAFT MODELS.

- REVERSAL of LoRA

- TRACE, HIDDEN STATE, bypass TRANSFORMER - for smaller numbers.

- DRAFT TOKEN - FEEDBACK - PARRALLELIZABLE!

- MASSIVE MATRIX MULTIPLICATION.

- KEY VERIFICATION 4 things into softmax.

- DONE.

_____________________________________________________

- QWEN 4

- RNN : but adds MLP

- DECODING (one at a time slow), but PARRALLELLIZE (prefill) much cheaper tokens.
- continually retry until matches.

________________________________________________________
- multi modal language tower.
- flops (counting) 
- tokens
- hours

FRONTIER AI SOFTWARE ENGINEERING SERIES.

BUILD SOFTWARE THAT BUILDS.

- NEUMOTRON
- STATESPACE MODEL
- 
