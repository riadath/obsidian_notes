#FL 
# FedCPF An Efficient-Communication Federated Learning Approach for Vehicular Edge Computing in 6G Communication Networks



# <u>Abstract</u>

## Summary
The selected text is an abstract of a research paper that discusses the use of Federated Learning (FL) in Vehicular Edge Computing (VEC) within 6G networks. FL is used to protect consumer data privacy, but it can lead to expensive communication overheads. The authors propose an efficient-communication approach called FedCPF, which consists of three parts: Customized, Partial, and Flexible. FedCPF provides a customized local training strategy for vehicular clients, introduces a partial client participation rule, and presents a flexible aggregation policy for valid updates. Experimental results show that FedCPF outperforms the traditional FedAVG algorithm in terms of testing accuracy and communication optimization. Compared with the baseline, FedCPF achieves efficient communication with faster convergence speed and improves test accuracy by 6.31% on average, while the average communication optimization rate is improved by 2.15 times.

## <u>Important Terms</u>

#### [[Federated Learning]]

##### <u>An anomaly-based Intrusion Detection System (IDS):</u>
It is a type of cybersecurity system that aims to identify and detect abnormal or suspicious behavior within a network or system. Unlike signature-based IDS, which relies on predefined patterns of known attacks (signatures), anomaly-based IDS focuses on recognizing deviations from established normal patterns of network or user behavior.

##### <u>A multiclass classification model:</u> 
It is a type of machine learning model designed to categorize data into more than two classes or categories. Unlike binary classification models that classify data into two classes (e.g., yes/no, true/false), multiclass classification models can handle multiple classes simultaneously.

##### <u>Transfer learning:</u>
It is a machine learning technique that leverages knowledge gained from solving one problem to improve the performance of a related but different problem. In the context of deep learning, transfer learning involves using a pre-trained model on a large dataset and applying it to a different but related task or dataset. This approach is particularly useful when the target dataset is small or lacks sufficient labeled examples for training a model from scratch.


# <u>Proposed Methods (IV)</u>

## <u>A. System Model</u>

##### <u>Notations</u>
$K =$ Total number of clients
$k =$ Index  of the clients
$D_k =$ Local Dataset of each client
$| . |$  Denotes the size of the set

${D_1,D_2, ......D_k} =$ Whole dataset

$|D| = \sum_{k=1}^{K} |D_k|$ 

{$x_k$} some local dataset with label set {$y_k$} in $D_k$ 

##### <u>Objective</u>
for some input $x_i$ in the neural network (local) $y_i$ is the desired output with some loss function $f_i(\omega)$ .

For some client $k$ the loss function on the data set is defined as:
$min_\omega F_k(\omega) =\frac{1}{|D_k|} \sum_{i \in D_k} f_i(\omega)$


$\omega^0 =$  Initial global parameter
$\omega_k^t =$ Local model parameters of the $k_{th}$ client for the $t_{th}$ communication round
$F(\omega) =$ Averaged global model parameters after the aggregate phase
$f_k(\omega_k) =$ Loss function of the $k_{th}$ client

Generalized Loss function,
$min_\omega F(\omega) = \sum_{k=1}^{K} \frac{|D_k|}{|D|}F_k(\omega_k)$                                    (4)

Optimizing the loss function $F(\omega)$ in FL is equivalent to minimizing the weighted average of local loss function $F_k(\omega_k)$ . Each client performs the training locally and shares their own local parameters.

## <u>B. Total Communication Cost</u>

$n(t) =$ Number of devices that participate in the $t_{th}$ communication round  \[ $n(t) \le K$ ]
$T =$ Total communication rounds in the FL process
$\omega^* =$ Number of model parameters
$W =$ Total communication cost in FL 

Total Communication cost,

$W=\sum_{t=1}^{T} \{n(t) + K\}.\omega^*$

Upper bound of communication overheads,
$\tilde{W}= 2T*(K.\omega^*)$ 

##  <u>C. A customized Local training Strategy</u>

#### [[Gradient Diversity]]

#### [[Earth Mover's Distance (EMD)]]


This EMD distance measurement is affected by factors such as the learning rate, the number of training epochs, and the gradient. The text explains that weight divergence in Federated Learning (FL) is mainly caused by two aspects: \[<u>L^2 Norm</u> : Basically Euclidian Distance.\]
- <mark style="background: #BBFABBA6;">(1)</mark>the weight divergence accumulates after T-1 communication rounds.
- <mark style="background: #BBFABBA6;">(2)</mark> weight divergence is induced by the probability distance for the data distribution on client k compared with the actual distribution for the whole data set. As a result, it is necessary to set an appropriate local training strategy for each client with different training amounts to reduce weight divergence.
		- **(2) Explained :** The 2nd point means that the data distribution on each client may not be representative of the whole data distribution. For example, if the data set is about images of animals, some clients may have more images of cats than dogs, while others may have more images of birds than fish. This means that the probability of each label (such as cat, dog, bird, fish) is different on each client. This probability difference is measured by EMD, and it affects the weight divergence because <u>it influences the direction and magnitude of the gradient updates on each client</u>. Therefore, <u>the global model may not converge well if the data distribution on each client is too different from the whole data distribution</u>. 
## <u>F. Convergence Analysis</u>

#### IID : Independent and Identically Distributed
In the context of federated learning, an IID ideal federated network refers to a network where the data on each client is assumed to be independently and identically distributed. This means that the data on each client is assumed to be drawn from the same underlying distribution and is independent of the data on other clients. This is an idealized assumption that may not hold in real-world scenarios, where the data on different clients can be non-IID, meaning that it is not independently and identically distributed

