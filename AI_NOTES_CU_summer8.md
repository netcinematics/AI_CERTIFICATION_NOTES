COUNTING by HAND


space complexity - big O notation

computational complexity.

how much do tokens cost?

____

FLOPS - how much floating point operations per second.

1 petaFLOP per second is 1 quadrillion FLOPS.

In Transformer COMPUTATION.

FLOPS per TOKEN INPUT.

Producing more TOKENS means more FLOPS means more GPU.

optimize "work cost"

____

EXAMPLE:

3 tokens in - 
4 tokens out.

OUTPUT COST MORE THAN INPUT TOKENS.

generate word by word. Token by token.

because of "attention mechanism" generativity.

embedding | attention | MLP | output processing.

_____

## ATTENTION MECHANISM cost:

basic chat:

O(N^2) or quadratic complexity in terms of input length N.

1000 tokens in:

1000 * 1000 = 1,000,000 operations (quadratic).

60B parameters model - Gpt-3.

200B parameters - Llama 2-200B.

1 trillion parameters - GPT-4.

Trillions of operations per second.

_____ 

