#iot #fdl
# <u>Abstract</u>

### <u>Summary</u>
The abstract of this research paper that proposes a federated learning-based anomaly detection approach to proactively recognize intrusion in IoT networks using decentralized on-device data. The approach uses federated training rounds on<mark style="background: #BBFABBA6;"> Gated Recurrent Units </mark>(GRUs) models and keeps the data intact on local IoT devices by sharing only the learned weights with the central server of the FL. The approach’s ensembler part aggregates the updates from multiple sources to optimize the global ML model’s accuracy. The experimental results demonstrate that this approach outperforms the classic/centralized machine learning (non-FL) versions in securing the privacy of user data and provides an optimal accuracy rate in attack detection. 


### <u>Important Terms</u>

###### <u>Federated Learning</u>
Federated learning is a way of training machine learning models without having to share the data samples. Instead, each device or node trains a local model on its own data and only sends the model parameters to a central server. The server then combines the parameters from different nodes to create a global model that is shared by all nodes. This way, the data privacy and security of each node is preserved, and the communication cost is reduced. Federated learning can be useful for applications that involve sensitive or decentralized data, such as healthcare, smart home, or industrial IoT

#### <u>Gated Recurrent Unit</u>
GRUs are a type of recurrent neural network (RNN) that can process sequential data such as text, speech, and time-series data. They are similar to <mark style="background: #BBFABBA6;">Long Short-Term Memory (LSTM) networks</mark>, but they have a simpler structure and fewer parameters. GRUs use two gates, called the update gate and the reset gate, to control the information flow and the memory state of the network. The update gate decides how much of the previous memory state to keep or forget, and the reset gate decides how much of the previous memory state to use for computing the new memory state. GRUs can learn long-term dependencies and avoid the vanishing gradient problem that affects basic RNNs. GRUs are useful for many applications such as music modeling, speech recognition, handwriting recognition, and natural language processing
<u>Links</u> : https://www.geeksforgeeks.org/gated-recurrent-unit-networks/



