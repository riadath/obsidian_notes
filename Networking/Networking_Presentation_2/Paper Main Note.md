# Abstract

### What we're trying to do
- Considering the vehicle position and velocity formulate a min-max optimization problem in order to optimize
	- Computation Capability
	- Transmission Power
	- Local Model Accuracy to get min cost in worst case of FL
- The formulated problem is a [[Nonlinear Programming]] problem subdivided into two problems
	- **For resource allocation:** Lagrangian Dual + Subgradient Projection method
	- **local model accuracy:** And adaptive harmony algorithm

# Introduction

### Challenges to be sol

#### <u>Service Switching between edge servers</u>
In the context of vehicular edge computing (VEC), service switching between edge servers refers to the process of vehicles moving between the coverage areas of different edge servers while still maintaining their connection to the network. As vehicles move along the road, they may move out of the coverage area of one edge server and into the coverage area of another. When this happens, their connection to the network is transferred from one edge server to another, allowing them to maintain a continuous connection to the network
