#FL 
[[Federated Learning]]


# <u>Abstract</u>

## Summary
The selected text is an abstract of a research paper that discusses the use of Federated Learning (FL) in Vehicular Edge Computing (VEC) within 6G networks. FL is used to protect consumer data privacy, but it can lead to expensive communication overheads. The authors propose an efficient-communication approach called FedCPF, which consists of three parts: Customized, Partial, and Flexible. FedCPF provides a customized local training strategy for vehicular clients, introduces a partial client participation rule, and presents a flexible aggregation policy for valid updates. Experimental results show that FedCPF outperforms the traditional FedAVG algorithm in terms of testing accuracy and communication optimization. Compared with the baseline, FedCPF achieves efficient communication with faster convergence speed and improves test accuracy by 6.31% on average, while the average communication optimization rate is improved by 2.15 times.

## <u>Important Terms</u>

[[Federated Learning]]

##### <u>An anomaly-based Intrusion Detection System (IDS):</u>
It is a type of cybersecurity system that aims to identify and detect abnormal or suspicious behavior within a network or system. Unlike signature-based IDS, which relies on predefined patterns of known attacks (signatures), anomaly-based IDS focuses on recognizing deviations from established normal patterns of network or user behavior.

##### <u>A multiclass classification model:</u> 
It is a type of machine learning model designed to categorize data into more than two classes or categories. Unlike binary classification models that classify data into two classes (e.g., yes/no, true/false), multiclass classification models can handle multiple classes simultaneously.

##### <u>Transfer learning:</u>
It is a machine learning technique that leverages knowledge gained from solving one problem to improve the performance of a related but different problem. In the context of deep learning, transfer learning involves using a pre-trained model on a large dataset and applying it to a different but related task or dataset. This approach is particularly useful when the target dataset is small or lacks sufficient labeled examples for training a model from scratch.


# <u>Proposed Methods (IV)</u>


### C. <u>A customized Local training Strategy</u>

##### <u>Gradient Diversity</u>
Gradient diversity is a concept in machine learning that measures the dissimilarity between concurrent gradient updates in distributed implementations of mini-batch stochastic gradient descent (SGD) algorithms. It has been experimentally observed that distributed implementations of mini-batch SGD algorithms exhibit speedup saturation and decaying generalization ability beyond a particular batch-size. High similarity between concurrently processed gradients may be a cause of this performance degradation. On problems with high gradient diversity, mini-batch SGD is amenable to better speedups, while maintaining the generalization performance of serial (one sample) SGD. 
- **<u>Concurrent Gradient Updates</u>** : Concurrent gradient updates refer to the process of updating the model parameters in parallel by multiple devices or workers in a distributed system. In the context of distributed implementations of mini-batch stochastic gradient descent (SGD) algorithms, a master node stores a global model, and multiple worker nodes compute gradients for a batch of data points with respect to the same global model. These gradients are then sent back to the master node, which applies them to the global model and sends the updated model back to the workers
- **<u>Mini-batch stochastic gradient descent (SGD):</u>** is a popular optimization algorithm used in machine learning. It is a variant of the stochastic gradient descent algorithm, which is an iterative method for minimizing an objective function. In mini-batch SGD, the gradient of the objective function is estimated using a small, randomly selected subset of the training data, called a mini-batch, at each iteration. This allows for faster convergence compared to using the full dataset at each iteration, as in batch gradient descent, while still providing a good estimate of the true gradient
#### <u>Earth Mover's Distance (EMD)</u>
- Earth Mover’s Distance (EMD) is a measure of the distance between two probability distributions over a region. In the context of the selected text, EMD is used to measure the distance between the data distribution on a client and the whole data distribution. This distance measurement is affected by factors such as the learning rate, the number of training epochs, and the gradient. The text explains that weight divergence in Federated Learning (FL) is mainly caused by two aspects:
- <u>L^2 Norm</u> : Basically Euclidian Distance.
	- <mark style="background: #BBFABBA6;">(1)</mark>the weight divergence accumulates after T-1 communication rounds.
	- <mark style="background: #BBFABBA6;">(2)</mark> weight divergence is induced by the probability distance for the data distribution on client k compared with the actual distribution for the whole data set. As a result, it is necessary to set an appropriate local training strategy for each client with different training amounts to reduce weight divergence.
		- **(2) Explained :** The 2nd point means that the data distribution on each client may not be representative of the whole data distribution. For example, if the data set is about images of animals, some clients may have more images of cats than dogs, while others may have more images of birds than fish. This means that the probability of each label (such as cat, dog, bird, fish) is different on each client. This probability difference is measured by EMD, and it affects the weight divergence because it influences the direction and magnitude of the gradient updates on each client. Therefore, the global model may not converge well if the data distribution on each client is too different from the whole data distribution. 



