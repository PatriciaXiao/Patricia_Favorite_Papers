# Graph Representation Learning

## Node Representation Learning

### Factorization-Based
pending

### Random-Walk-Based
- [**LINE**: Large-scale Information Network Embedding (WWW'15)](https://arxiv.org/abs/1503.03578)
    * first- and second-order proximities of the nodes

### Deep-Neural-Network-Based

#### Base Models
- [Semi-Supervised Classification with Graph Convolutional Networks (ICLR'17)](https://arxiv.org/abs/1609.02907)
    * Where **GCN** (Graph Convolutional Networks) is proposed
    * Discussed in [blog](https://tkipf.github.io/graph-convolutional-networks/), compared to [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://arxiv.org/abs/1606.09375)
    * Implementation in [Tensorflow](https://github.com/tkipf/gcn), [Keras](https://github.com/tkipf/keras-gcn) and [PyTorch](https://github.com/tkipf/pygcn)
- Graph Attention Networks (GAT)
- GIN

#### Extension onto HINs (Heterogenerous Information Networks)
- [Modeling Relational Data with Graph Convolutional Networks (ESWC'18)](https://arxiv.org/abs/1703.06103)
    * Referred to as relational-GCN, abbreviated as **r-GCN**.
    * Outputs the weighted sum of the embeddings from each relation, in each layer.
    * To reduce the parameters, designed two methods for weight-matrix decomposition.
    * Implementation in [Keras](https://github.com/tkipf/relational-gcn), [Tensorflow](https://github.com/MichSchli/RelationPrediction), [PyTorch](https://github.com/dmlc/dgl/tree/master/examples/pytorch/rgcn).
- HAN

#### Down-Sampling
- GraphSAGE
    * Treating the convolution 
- FastGCN

## Representation of the Whole Graph
pending