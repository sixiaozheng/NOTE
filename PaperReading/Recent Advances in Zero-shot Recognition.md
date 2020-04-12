# Recent Advances in Zero-shot Recognition

>   Yanwei Fu, Tao Xiang, Yu-Gang Jiang, Xiangyang Xue, Leonid Sigal, and Shaogang Gong

**Abstract**--从representations of models， datasets，evaluation settings综述existing zero-shot recognition techniques。related recognition tasks，one-shot and open set recognition，是natural extensions of zero- shot recognition。重要的是，指出现有方法的局限性（limitation），并之处未来的研究方向。

## Introduction

受人类可以识别未见过的物体的能力激发，learning to learn or lifelong learning研究领域受到关注。

zero-shot learning：novel visual categories没有训练样本

one-shot learning：novel visual categories有少量的训练样本

‘open-set’ setting：testing instance属于seen或unseen/novel categories。

这些问题可以在transfer learning的setting下解决。transfer learning强调transfer across domains，tasks 和distributions的知识，他们相似但不同。

>   Transfer learning [5] refers to the problem of applying the knowledge learned in one or more auxiliary tasks/domains/sources to develop an effective model for a target task/domain.

现有domain adaptation方法很难直接应用到zero-shot learning上，因为target domain只有少量的training instances。所以key challenge是学习一个domain-invariant and generalizable feature representation。

## Overview of Zero-shot recognition

>   Thus the main challenge of zero-shot recognition is how to generalize the recognition models to identify the novel object categories without accessing any labelled instances of these categories.

 一个主要的想法是探索和利用seen和unseen classes之间的语义相关性的知识。semantic representation被编码到一个high dimensional vector space。semantic representation 包括semantic attributes 和semantic word vectors。semantic representation被source 和 target dataset共享。给定一个pre-defined semantic representation，每个class name可以被表示为一个attribute vector或者一个semantic word vector--一种称为class prototype的representation。

>   The zero-shot recognition can be considered a type of life-long learning.
>
>   Therefore, zero-shot recognition is crucial for recognizing dynamically created novel concepts which are composed of new combinations of existing concepts.

## Semantic Representation in Zero-shot recognition

### Semantic Attributes

>   An attribute (e.g., has wings) refers to the intrinsic characteristic that is possessed by an instance or a class (e.g., bird) (Fu et al. [11]), or indicates properties (e.g., spotted) or annotations (e.g., has a head) of an image or an object (Lampert et al. [9]).
>
>   in attribute and object-based modeling (Wang et al. [18])) is to take the at- tribute labels as latent variables on the training dataset, e.g., in the form of a structured latent SVM model with the objective is to minimize prediction loss.
>
>   A key advantage of attribute learning is to provide an intuitive mechanism for multi-task learning (Salakhutdinov et al. [19]) and transfer learning (Hwang et al. [20]).

1.  User-defined Attributes：User-defined attributes are defined by human experts [32], [9], or a concept ontology [11].  unary（一元） (e.g., red colour, round texture)，是简单属性，可以由单独的图像片段捕获(外观为红色，形状为圆形)。binary （二元）(e.g., black/white stripes)是更复杂的属性，其基本元素是一对片段(例如，黑白条纹)。

2.  Relative Attributes：可以作为一种信息量更大的方式来表达更丰富的语义，从而更好地表达视觉信息。可以直接用于zero-shot recognition。

3.  Data-driven attributes: 

    >   To better augment such user-defined attributes, Parikh et al. [50] proposed a novel approach to actively augment the vocabulary of attributes to both help resolve intra-class confusions of new attributes and coordinate the “name-ability” and “discriminativeness” of candidate attributes.

    user-defined attributes还远远不足以建模更复杂的视觉数据，原因（1）inefficient (costing substantial effort of user experts) and/or insufficient (descriptive properties may not be discriminative). 所以有必要从可视化数据中自动分离出更具鉴别性的中间表示，即数据驱动属性。

4.  Video Attributes：对于action recognition and activity understanding很重要

![1574345442962](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1574345442962.png)

### Semantic Representations Beyond Attributes

1.  Concept ontology：Concept ontology is directly used as the semantic representation alternative to attributes. WordNet是一个最广泛研究的concept ontology, 其中不同concept之间有一个semantic distance。
2.  Semantic word vectors：The se- mantic word vector space is trained from linguistic knowledge bases such as Wikipedia and UMBCWebBase using natural language processing models [71], [87]. each dimension of the space does not have a specific semantic meaning. ## MODELS FOR ZERO-SHOT RECOGNITION

## Models for zero-shot recognition

zero-shot recognition 首先学习一个embedding model，然后做recognition。

>   The embedding models aim to establish connections between seen classes and unseen classes by projecting the low- level features of images/videos close to their corresponding semantic semantic vectors (prototypes). Once the embedding is learned, from known classes, novel classes can be recognized based on the similarity of their prototype representations and predicted representations of the instances in the embedding space. The recognition model matches the projection of the image features against the unseen class prototypes (in the embedding space).

### Embedding Models

1.  Bayesian Models