# Graph Representation Learning

## Node Representation Learning

### Factorization-Based
pending

### Random-Walk-Based
- [**LINE**: Large-scale Information Network Embedding (WWW'15)](https://arxiv.org/abs/1503.03578)
    * first- and second-order proximities of the nodes
    * (patricia's note) how the paper introduces its motivation, problem, solution, etc., is really worth learning from. everything is explained very clearly and briefly.
- [**GraphVite**: A High-Performance CPU-GPU Hybrid System for Node Embedding (WWW'19)](https://arxiv.org/abs/1903.00757)
    * a framework that significantly accelerate many (typically) random-walk-based models including LINE (for line, speedup 50X)
    * (patricia's note) hybriding with C/C++, switching between GPU/CPU, this work is really solid and admirable. inheriting LINE's style of providing good-explanations on everything.

### Deep-Neural-Network-Based

#### Base Models
- **GCN** (Graph Convolutional Networks): [Semi-Supervised Classification with Graph Convolutional Networks (ICLR'17)](https://arxiv.org/abs/1609.02907)
    * Discussed in [blog](https://tkipf.github.io/graph-convolutional-networks/), compared to [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://arxiv.org/abs/1606.09375)
    * Implementation in [Tensorflow](https://github.com/tkipf/gcn), [Keras](https://github.com/tkipf/keras-gcn) and [PyTorch](https://github.com/tkipf/pygcn)
    * (patricia's note) its math comes from graph spectrum theory, but after the many approximations, the spectral domain convolution finally becomes the same as the vertex domain aggregation. ([my old notes](http://web.cs.ucla.edu/~patricia.xiao/files/Reading_Group_20181204.pdf))
- **GAT**: [Graph Attention Networks (ICLR'18)](https://arxiv.org/abs/1710.10903)
    * Applying multi-head self-attention on each node and their neighbors at each layer (adding attention-layer), essentially assigning different importance to the neighborhood
    * Implementation in [Tensorflow](https://github.com/PetarV-/GAT), [PyTorch](https://github.com/PatriciaXiao/pyGAT) and in [PyTorch with DGL](https://github.com/dmlc/dgl/tree/master/examples/pytorch/gat)
    * (patricia's note) compared with GCN, it takes longer time each epoch, takes larger memory, but converges in fewer epochs, and thus converges in similar speed overall

#### Discussions on the Base Models
- [Deeper Insights into Graph Convolutional Networks for Semi-Supervised Learning (AAAI'18)](https://arxiv.org/pdf/1801.07606.pdf)

#### Architectural Improvements
- **GraphSAGE**: [Inductive Representation Learning on Large Graphs (NIPS'17)](https://arxiv.org/abs/1706.02216)
    * More details on its [homepage](http://snap.stanford.edu/graphsage/).
    * Treating the convolution operation as: (1) neighborhood-sampling (2) aggregation
    * Implementation in [Tensorflow](https://github.com/williamleif/GraphSAGE), [PyTorch](https://github.com/bkj/pytorch-graphsage), and [a simpler version of PyTorch](https://github.com/williamleif/graphsage-simple)
    * (patricia's note) sacrificing time for space, not good for higher-density graphs, slow sampling and still large memory consumption
- [**FastGCN**: Fast Learning with Graph Convolutional Networks via Importance Sampling (ICLR'18)](https://arxiv.org/abs/1801.10247)
    * Proposed to sample some vertices in a batch and use only the subgraph for that step.
    * Implementation in [Tensorflow](https://github.com/matenure/FastGCN)
    * (patricia's note) clever choice, good for large and high-density graphs; remember to include the training node set in validation and testing, otherwise the model simply won't work (we need to learn the unknown from known)
- **GIN** (Graph Isomorphism Network): [How Powerful are Graph Neural Networks? (ICLR'19)](https://arxiv.org/abs/1810.00826)
    * A more flexible, more general, thus more expressive version of GraphSAGE (e.g. the aggregation operation has more options)
    * Implementation in [PyTorch](https://github.com/weihua916/powerful-gnns) and in [PyTorch in DGL](https://github.com/dmlc/dgl/tree/master/examples/pytorch/gin).
    * (patricia's note) same as GraphSAGE in time-space-sparsity relations
- [**Cluster-GCN**: An Efficient Algorithm for Training Deep and Large Graph Convolutional Networks (KDD'19)](https://arxiv.org/pdf/1905.07953.pdf)
    * They split the large graph into parts and train each part separately, join them in the end
    * Implementation in [Tensorflow](https://github.com/google-research/google-research/tree/master/cluster_gcn), [PyTorch](https://github.com/benedekrozemberczki/ClusterGCN)
    * (patricia's note) the **running time analysis** of GCN-based models in their paper is super helpful

#### Extension onto HINs (Heterogenerous Information Networks)
- **r-GCN** (relational-GCN): [Modeling Relational Data with Graph Convolutional Networks (ESWC'18)](https://arxiv.org/abs/1703.06103)
    * Outputs the weighted sum of the embeddings from each relation, in each layer.
    * To reduce the parameters, designed two methods for weight-matrix decomposition.
    * Implementation in [Keras](https://github.com/tkipf/relational-gcn), [Tensorflow](https://github.com/MichSchli/RelationPrediction), [PyTorch (DGL)](https://github.com/dmlc/dgl/tree/master/examples/pytorch/rgcn).
- **HAN**: [Heterogeneous Graph Attention Network (WWW'19)](https://arxiv.org/abs/1903.07293)
    * Relying on metapaths to parse the heterogenerousity. Calculate node-level attention (of the neighborhood) under each metapath. Do also semantic-attention among the metapaths to generate the output embedding.
    * Implementation in [Tensorflow](https://github.com/Jhy1993/HAN), [PyTorch (DGL)](https://github.com/dmlc/dgl/tree/master/examples/pytorch/han)
    * (patricia's note) super sensitive to: (1) the quality of input features; (2) some features of the dataset (awaiting to be explored); (3) the quantity of the metapath. being super space-consuming, and space & time complexity increase at least linearly with the amount of metapaths.


## Representation of the Whole Graph
pending