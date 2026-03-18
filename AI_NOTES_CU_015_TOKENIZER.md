CU NOTES TOKENIZER.


Artificial Neuron - 6 levels of depth
Blackbox - Components - Coding
Srijanie Dey 
Chris Mayfield


### ENCODER | DECODER

### NEURON

Input output weights, weighted sum bias step function activation function output.

input weights bias activation linear function activation function.

inpt weights bias activation (3 to 1 networkd)

input in 3 places 
weights are on line
bias on the side
activation i


### TENSOR level.

Shape is dot product of two vectors.


ReLU - sets all the negative numbers to 0!


W * x + b = Z (dot product | relu | bias)

Relu y = max(z,0) //set all negative to 0.
Rectified Linear Unit.

Symbolic Math.



### CODING

artificial neuron.

dot product between input vector and encoded weights.

________________________________________________________


Industry problems.

fast moving. - how to make it usable.

understanding model architecture and system level behavior.

how do we scale inference efficiently.

problems are at intersections between models and systems.

problems in combinations of units.


______________________________________________________________

### diagram

Into encoder and decoder

3 Attentiona

Feed forward

softmax

positional encoding

Add & Norm.

_________________________________________________________________

source language into embedding layer. to decoder destination language.

embedding layer - turns into higher dimension.

Transformer layers = attention and feed forward.

Run in parallel.

Prefill encoder to run in parallel.

Decoder cannot prefil.

_________________________________________

DECODER

<START> 

Self attention 

Cross Attention

Feed Forward

Linear logits. Matches the input layer size. Score before softmax probability.

logit is score - probability distribution.

Softmax - turns into probability distribution.


causal masking.

cannot be parallel because of attention.
___________________________________________________________

X - input
Hx = hidden input = embedding layer

Transformer encodes 

Weights hidden

weight ff

attention QKV attention score - logit - softmax - probability.

multiply by v to get attention weighted.

W output transposition of decoder embed into linear layer output as TIE.

___________________________________________________


Scaling - partition matrix to GPU.

__________________________________________________

