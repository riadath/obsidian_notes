##### ChatGPT Chat : https://chat.openai.com/share/b0809537-201d-4d1a-a077-171fd751135e

# Abstract

#### <u>Dynamic Voronoi Partitions</u>
Dynamic Voronoi is a technique used in the proposed cooperative exploration approach for multiple mobile robots to minimize duplicated exploration areas by assigning different target locations to individual robots. [It is developed using dynamic Voronoi partitions](http://wiki.ros.org/dynamicvoronoi) [1](http://wiki.ros.org/dynamicvoronoi).
The Voronoi diagram is a partition of a plane into regions close to each of a given set of objects. [Voronoi diagram - Wikipedia](https://en.wikipedia.org/wiki/Voronoi_diagram#:~:text=In%20mathematics%2C%20a%20Voronoi%20diagram,%2C%20sites%2C%20or%20generators).

# Introduction

### <u>Problems</u>
Most exploration methods were designed for single robots and had limitations in exploring large unknown areas.

### <u>Contributions of this paper</u>
1. A Voronoi-based exploration strategy is developed to coordinate a multi-robot team effectively in exploring an unknown area
2. A collision avoidance algorithm with deep reinforcement learning is proposed to navigate the robot to the target
3. The feasibility of the proposed cooperative exploration strategy is validated by real-world experiments using wheeled mobile robots

#### <u>Buzz words and Abbreviations</u>

1. **FEP (Frontier Exploration Planning)**: FEP is a global exploration planner that helps a robot identify unexplored frontiers in an environment. It focuses on selecting areas on the frontier of explored space for further exploration.
    
2. **NBVP (Next-Best-View Planning)**: NBVP is a local exploration planning technique that determines the best next viewpoint for a robot to gather information. It's often used in conjunction with FEP to guide a robot in exploring its immediate surroundings.
    
3. **Heuristic Information Gain-Based NBVP**: This approach combines the principles of NBVP with heuristics based on information gain. It aims to find the next best view for a robot while considering factors like information content and efficiency, improving exploration in 3-D unknown environments.



# Technical Background

### The Voronoi Cell $Vor(R_i)$ is defined by
$Vor(R_i)=\{q \in Q \ \ | \ \ \lVert q-p_i \rVert \le \lVert q-p_j \rVert,\forall R_j \in N_{R_i}\}$

### Hierarchical control architecture

![[Pasted image 20231029213948.png | 500x420]]

### Collision Avoidance Problem Formulation
### $v_t = f(l_t,p_t,v_{t-1})$
- where $l_t$ is the laser range data at time step t 
- $p_t$ stands for the relative position of the target,
- $v_{t-1}$ denotes the velocity command at the last time step

### Coordination Algorithm for Explorer Robots
we will define the utility function for frontier points $k$ assigned to the robot $R_i$ as
![[Pasted image 20231031035846.png]]

## <u>Deep Reinforcement Learning Setup</u>

### Observation and Action Space
