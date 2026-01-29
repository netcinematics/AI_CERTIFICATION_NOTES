
//AI fundamentals --------------------------------------------------------------

MATH EVAL METRICS equations.

PERPLEXITY. PPL

exponent. 

WORD ID into Embedding model.
Transformer Decoder.

Linear Softmax.

For LOGITS, PROBABILITIES, and GROUND TRUTH. 

Sum Log and Exponent give a single number.

//------------------------------------------------

### Negate Log Likelihood

Negative Log Likelihod, worst likelyhood, 

Model predicts score, softmax, cross entropy, backpropagation
Why do we take log? Trick: turn product into sum. Easer to calculate.

Product = column vector
Log(numbers) = sum. 

Is no longer probability (outside of 0-1 range), is now likelihood.

Negation. Linear scale: surprised and not surprised.
Make the model as not surprised as possible.
model is very wrong needs correction, model is aready confident.

Log Scale. more reward for correcting prediction. 
Small reward for already good models. 
Phenomena of big changes on good models - usually bad.

### CROSS ENTROPY LOSS

Most common loss function.  PyTorch, Keras, Tensorflow. Trainer FLAS.

positive to negative loss function.

Output GROUNDTRUTH: know next token. 1 and 0 distribution. Less wrong.

Get weights from softmax. Log and Negate to GROUND TRUTH matrix identity.

Sum is equivalent to dot product. before log. 
sum log gets the dot product back.

Get cross entropy loss. Results in ideal number.

### KL Divergence:

extended cross entropy loss, or cross entropy loss is one example of KL divergence.

compare two distributions. 
compare ratio of one distribution to another. .
Subtraction of ratios to get log, then multiply by probability to get KL divergence.
Single number that quantifies difference between two distributions.

New reward for every iteration. Good models get less.
Not too divergent. Not overfitting.


### Accuracy

Precision of predictions. 

4 positive and 4 negative examples.

binary classification problem: is this a face, car or cat?

One value to another value. 

language usses softmax, but this uses sigmoid.

Threshold of 0.5. creates mask.

decision above threshold is positive, 1 below is negative 0

binary classification problem.

accuracy determined by decision compared to labels. 

0.9 rejects everything. 0.1 accepts everything. 

So 0.5 is threshold. 50% accuracy. 

//--------------------------------------------------------------

Train LLM cross entropy loss - determins when to stop training.

RAG, Agent measure is there retrevial is accurate.

Precision Recall of retrieval. Does it find the right answers?

METRICS: Open RAG eval?
- chunks relevant (umbrela)
- AutoNuggetizer (vital chunks existent)
- FCS - response grounded int chungks (hallucination)
- Citation Faithfulness, 
- Consistency, run 5 times get 5 different answers.
- want average response to be close to ground truth.
Really hard to measure relevance for everything of a large corpus..

USE LLM AS A JUDGE:
special prompt to get LLM to rate responses.
Nugget Creation
Vital Nugget Selection
Support Evaluation.

EVALUATION.

Highly correlated - to what humans judges responses to be good or bad.

Benchmark. Golden answers.
IN practice answers can change. So updating manually.

Nuggetizer does not require gold answers.

//----------------------------------------------------

Precision and Recall

Look at precision and recall of retrieval.

Curve that shows dropping precision and recall.

10 positive and 10 negative examples.

Weights. Into Probability.

TP - True Positve
PP - Predicetedly Positive
AP - Actual Positive

generous to false positive - threshold.

RECALL - is actually positve  actually positive?

precision - is predicted positive actually positive?

F1 - harmonic mean of precision and recall.

//----------------------------------------------------------

ROUGE

Only recall 3 out of 6. Recall ration is 0.5.

//-----------------------------------------

BLEU
UNI-GRAM:
1 gram 2 gram 3 gram 4 gram

log = turn product into sum.

weight & sum

exponent turns sum back into product.

brevity penalty.

saying nothing is precise.

//-------------------------------------


BERT SCORE

L2 Norm, gets recall and precision.

Compined with F1.

Transformer model: BERT

BERT stands for:  Bi directional encode Transformer.

PERPLEXITY.

Benchmark tools from Vectera.

