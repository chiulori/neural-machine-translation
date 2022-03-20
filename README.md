# Neural Machine Translation
### By Jointly Learning to Align and Translate

## Summary

The [article](https://arxiv.org/abs/1409.0473) suggests that a traditional encoder-decoder translation model has limitations on translating long texts, and proposes that a bidirectional RNN model would be better suited for translation and would outperform the conventional encoder-decoder architecture. 

## What is the current state?

### Translation
* Find target sentence *y* that maximizes conditional probability given input sentence *x*

              *p*(y | x)

### RNN Encoder-Decorder
* Encodes the input sentence to a fixed-length vector
  * Defines vector *c* by combining the sequence of input vectors at time *h* is a hidden state at time *t*

      

* Decodes fixed-length vector into translated variable-length output
  * Defines the probability of *y* by decomposing joint probability into ordered conditionals
  * Prediction is based on the vector *c* and previously predicted words


## What is the proposed method?

### RNNsearch
* Context vector *c<sub>i</sub>* consists of annotations *h<sub>i</sub>* that have information on the whole input with emphasis surrounding each word at the *i*th position
  * Defined by the weighted sum of *h<sub>i</sub>*



* Conditional probability is defined based on the context vector *c<sub>i</sub>* for each target word at the *i*th position, *y<sub>i</sub>*


* Unlike RNN Encoder-Decoder, decoder has an attention mechanism
