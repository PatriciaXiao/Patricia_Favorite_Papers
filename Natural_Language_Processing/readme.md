# Natural Language Processing

## Word Embeddings

### Base Models
- **word2vec**: [Efficient estimation of word representations in vector space (ArXiv'13)](https://arxiv.org/abs/1301.3781)
    * predicting the neighborhood, negative sampling, more flexible design, etc.
- **GloVe**: [GloVe: Global Vectors for Word Representation (EMNLP'14)](https://nlp.stanford.edu/pubs/glove.pdf) ([homepage](https://nlp.stanford.edu/projects/glove/))
    * predicting the global count, larger memory consumption
- **ELMo**: [Deep contextualized word representations (NAACL'18)](https://arxiv.org/abs/1802.05365)
    * bi-LSTM, using weighted combination of the trained embeddings of the two LSTM layers
- [**BERT**: Pre-training of Deep Bidirectional Transformers for Language Understanding (ArXiv'18)](https://arxiv.org/abs/1810.04805)
    * based on [Transformer](https://arxiv.org/abs/1706.03762)
- [**XLNet**: Generalized Autoregressive Pretraining for Language Understanding (NeurIPS'19)](https://arxiv.org/abs/1906.08237)
    * based on [Transformer-XL](https://arxiv.org/abs/1901.02860), which enables the transformer to attend beyond a fixed-length context

#### Discussions on the Models
- [Don’t count, predict! A systematic comparison of context-counting vs. context-predicting semantic vectors (ACL'14)](https://www.aclweb.org/anthology/P14-1023.pdf)
    * shows that predict-model (e.g. word2vec) has certain advantages over count-model (e.g. GloVe)
- [Improving Distributional Similarity
with Lessons Learned from Word Embeddings (TACL'15)](https://levyomer.files.wordpress.com/2015/03/improving-distributional-similarity-tacl-2015.pdf)
    * shows that word2vec could be easily improved by negative-sampling on a different distribution

### Sentence Embeddings
- **SIF**: [A Simple but Tough-to-Beat Baseline for Sentence Embeddings (ICLR'17)](https://openreview.net/pdf?id=SyK00v5xx)
    * still a weighted combination of the words' embeddings, but weighted more carefully