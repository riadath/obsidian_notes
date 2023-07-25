#iot #FL 
# <u>Abstract</u>

### <u>Summary</u>
The abstract of this research paper that proposes a federated learning-based anomaly detection approach to proactively recognize intrusion in IoT networks using decentralized on-device data. The approach uses federated training rounds on Gated Recurrent Units (GRUs) models and keeps the data intact on local IoT devices by sharing only the learned weights with the central server of the FL. The approach’s ensembler part aggregates the updates from multiple sources to optimize the global ML model’s accuracy. The experimental results demonstrate that this approach outperforms the classic/centralized machine learning (non-FL) versions in securing the privacy of user data and provides an optimal accuracy rate in attack detection. 


### <u>Important Terms</u>

###### [[Federated Learning]]

#### [[Gated Recurrent Unit]]
- GRUs are a type of [[Recurrent Neural Network ( RNN )]] that can process sequential data such as text, speech, and time-series data. They are similar to [[Long Short-Term Memory ( LSTM )]] networks, but they have a simpler structure and fewer parameters. GRUs use two gates, called the update gate and the reset gate, to control the information flow and the memory state of the network. The update gate decides how much of the previous memory state to keep or forget, and the reset gate decides how much of the previous memory state to use for computing the new memory state. GRUs can learn long-term dependencies and avoid the vanishing gradient problem that affects basic RNNs. GRUs are useful for many applications such as music modeling, speech recognition, handwriting recognition, and natural language processing <u>Links</u> : https://www.geeksforgeeks.org/gated-recurrent-unit-networks/ 
	- [[Recurrent Neural Network ( RNN )]]  : Recurrent Neural Networks (RNNs) are a type of artificial neural network designed to process sequential data, such as time series, speech, or text. Unlike traditional feedforward neural networks, RNNs have feedback connections that allow them to maintain an internal state or memory. This allows them to take into account the context of the input data and make predictions based on the entire sequence, rather than just the current input. RNNs are widely used in natural language processing, speech recognition, and other applications where the order of the input data is important.
	- [[Long Short-Term Memory ( LSTM )]]: Long Short-Term Memory (LSTM) Networks : Long Short-Term Memory (LSTM) networks are a type of recurrent neural network (RNN) that can process sequential data such as text, speech, and time-series data. They are designed to overcome the vanishing gradient problem that affects basic RNNs by using gates to control the flow of information. LSTMs have an input gate, an output gate, and a forget gate that work together to allow the network to remember or forget information over long periods of time. This makes LSTMs well-suited for tasks such as speech recognition, machine translation, and natural language processing where long-term dependencies are important.  

#### <u>Learned Weights</u>
Learned weights are parameters that are adjusted during the training process of a machine learning model, such as a neural network. They represent how much each input feature contributes to the output prediction.

#### <u>Ensembler</u>
An ensemble in machine learning is a model that combines the predictions from two or more models. The models that contribute to the ensemble, referred to as ensemble members, may be the same type or different types and may or may not be trained on the same training data

# <u>Introduction</u>
- IoT devices micro-architecture style makes it less suitable to deploy computationally heavy security firewalls. 
- unguarded IoT devices could  turn into an open threat to all other network devices interconnected with them
- Mirai Attacks have grown exponentially
	- **Mirai Attacks :** Scans the public internet for IoT devices, attempting to establish a remote telnet connection using a list of common factory default usernames and passwords. Once one device is infected, the malware begins scanning for more victims. Mirai has the potential to harness the collective power of millions of IoT devices into botnets and launch attacks 
- ML based solutions are the least preferred because : 
	- The prerequisite to having the whole set of training data on a central server.
	- The prerequisite to having the whole set of training data on a central server.
	- Training huge volumes of data on a single server can be computationally expensive
- *we propose a decentralized federated learning approach with an ensembler to enable anomaly detection on the IoT networks. The approach enables on-device training*
- Uses Long Short-Term Memory (LSTMs) and Gated Recurrent Units (GRUs)
- **Contributions of this paper:**
	- Enables on-device ML training with [[Federated Learning]]
	- Higher accuracy rates and minimized false alarms
	- Demonstrate benefits of [[Federated Learning]] with ensembler