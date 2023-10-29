# Abstract

### <u>Dynamic Voronoi Partitions</u>

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


