# Spiking Neural Networks

**SNN**是更接近地模仿自然神经网络的[人工神经网络](https://en.wikipedia.org/wiki/Artificial_neural_network)模型。除[神经元](https://en.wikipedia.org/wiki/Artificial_neuron)和[突触](https://en.wikipedia.org/wiki/Electrical_synapse)状态外，SNN还将时间概念纳入其[运行模型](https://en.wikipedia.org/wiki/Operating_Model)。这个想法是SNN 中的[神经元](https://en.wikipedia.org/wiki/Artificial_neuron)不会在每个传播周期发射（就像在典型的多层[感知器网络中](https://en.wikipedia.org/wiki/Perceptron)发生的那样），而是仅在[膜电位](https://en.wikipedia.org/wiki/Membrane_potential)发生时触发 - 与其膜电荷相关的神经元的内在质量 - 达到特定值。当神经元发射时，它会产生一个信号，该信号传播到其他神经元，然后根据这个信号增加或减少它们的电位。

在尖峰神经网络的背景下，当前的激活水平（建模为一些[微分方程](https://en.wikipedia.org/wiki/Differential_equation)）通常被认为是神经元的状态，其中进入的尖峰将该值推高，然后随着时间推移发射或衰减。

## Beginnings

-   现代人工神经网络通常是完全连接的，接收连续值并输出连续值。尽管这些网络使我们在许多领域取得了突破，但它们在生物学上是不准确的，实际上并不模仿生物大脑中神经元的运作机制。[[2\]](https://en.wikipedia.org/wiki/Spiking_neural_network#cite_note-blog.csdn.net-2)



## Softwares

Brian

nest

BindsNET

## Deep Learning in Spiking Neural Networks
ANN: a single, static, continuous-valued activation

SNN: discrete spike to compute and transmit information, spike times, spike rates

-   differences: structure, neural computations, learning rule
-   most important differences: information propagates between their units. broadcasting trains of action potentials, also known as spike trains to downstream neurons. sparse, high information, uniform amplitude (100 mV with
    spike width about 1 msec).
-   spike timing: including latencies, and spike rates

SNN architecture: spiking neurons and interconnecting synapses (adjustable scalar weight)