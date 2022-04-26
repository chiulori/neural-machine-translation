# Neural Machine Translation By Jointly Learning to Align and Translate

## Summary

The [article](https://arxiv.org/abs/1409.0473) mentions that neural machine translation is a relatively new concept for machine translation and is an improvement to traditional statistical machine translation. However, the authors of this paper suggest that this new approach of using an encoder-decoder algorithm has limitations on translating long texts. The authors propose that a bidirectional RNN model would be better suited for translation and would outperform the conventional encoder-decoder architecture. The paper compares the underlying architecture and performance of both models.

## What is the current state?

### RNN Encoder-Decoder
* Encodes the input sentence to a fixed-length vector
  * Defines vector *c* by combining the sequence of input vectors, *h*, a hidden state at time *t*

<p align="center"><img width="300" alt="Screen Shot 2022-03-21 at 7 13 52 PM" src="https://user-images.githubusercontent.com/19938311/159383103-facca493-ce33-4121-81c1-f0a8d5c943a3.png">

* Decodes fixed-length vector into translated variable-length output
  * Defines the probability of *y* by decomposing joint probability into ordered conditionals
  * Prediction is based on the vector *c* and previously predicted words

<p align="center"><img width="300" alt="Screen Shot 2022-03-21 at 7 16 03 PM" src="https://user-images.githubusercontent.com/19938311/159383300-6880d18b-3936-4ce7-8336-07daeda5f2e5.png">

## What is the proposed method?

### RNNsearch
* Bidirectional RNN encoder and decoder that searches the input in order to decode a translation
  * Concatenation of the forward and backward hidden states allow for the algorithm to account for annotations of the preceding and following words of the source

<p align="center"><img width="300" alt="Screen Shot 2022-03-21 at 7 19 31 PM" src="https://user-images.githubusercontent.com/19938311/159383566-c9eacf35-94c2-412b-9c20-ef95e4c641ef.png">
  
* Context vector *c<sub>i</sub>* consists of annotations *h<sub>i</sub>* that have information on the whole input with emphasis surrounding each word at the *i*th position
* Conditional probability is defined based on the context vector *c<sub>i</sub>* for each target word at the *i*th position, *y<sub>i</sub>*
* Unlike RNN Encoder-Decoder, decoder has an attention mechanism so that the encoder does not contain all of the information
  
## Model Comparison
  
### Experiment
* Task: English-to-French translation of the corpora provided by ACL WMT '14
  * Corpus contained 348M words
* Trained models with sentences up to 30 words and up to 50 words
  
<p align="center"><img width="600" alt="Screen Shot 2022-03-21 at 7 42 55 PM" src="https://user-images.githubusercontent.com/19938311/159385432-4a16a808-89e5-4e8d-afcf-34a948f27dcb.png">
  
* Result: RNNsearch-50 performed the best
  
## Critical Analysis

* Experimented only on English-to-French translation. The authors do not discuss translation of other text sources or other languages
* This approach requires computation of the annotation weight for each word which would limit the applicability to other tasks and could be costly
  
## Discussion Topic 1
Besides sentence length, what are other limitations of the RNN encoder-decoder approach?
  
## Discussion Topic 2
According to the figure showing performance of each of the models, RNNsearch-50 which performed the best actually has the lowest BLEU score at sentence length 0, why is that?
 
## Discussion Topic 3
What are some challenges with the RNNsearch model?
  
## Other Resources
* [Attention Mechanism](https://machine-learning-note.readthedocs.io/en/latest/attention.html)
* [Understanding Encoder-Decoder Sequence-to-Sequence Model](https://towardsdatascience.com/understanding-encoder-decoder-sequence-to-sequence-model-679e04af4346)
* [RNNsearch on Chinese-to-English translation](https://github.com/xwgeng/RNNSearch)
* [Neural Machine Translation with Recurrent Attention Modeling](https://aclanthology.org/E17-2061.pdf)
* [A Guide to the Encoder-Decoder Model and the Attention Mechanism](https://betterprogramming.pub/a-guide-on-the-encoder-decoder-model-and-the-attention-mechanism-401c836e2cdb)
* [On the Properties of Neural Machine Translation: Encoder-Decoder Approaches](https://arxiv.org/abs/1409.1259)

## Video Presentation
* Video Recording can be found [here](https://www.youtube.com/watch?v=A62bEN41TLs)


