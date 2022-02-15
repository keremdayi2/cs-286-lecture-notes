# CS 286 February 2nd notes

Major themes in hw1:
* Basic individual rules give rise to macro action via composition
* Global information (typical in centralized implementations) vs. local information
* Task allocation and optimality

**Last time**: how individual controllers give rise to group behavior. Mathematical abstractions for representing large groups. Gradient Based control. Implementation in hardware.

Graphs encode relationships between robots (communication and control).

Individual dynamics: $x_k(t) \to x_k(t+1)$. $f: X \times U \to X$.

Last lecture: we looked at one potential definition of $f$, potential based control. $x_k(t+1) = x_k(t) + \delta \frac{\partial f}{\partial x}$ where $f$ is a potential function. Let $u = \frac{\partial f}{\partial x}$. 

**Today**: we will look at heterogenous systems and task allocation. We will look at questions and functions of optimality.

Leader election: specialized nodes, somewhere in between centralized and decentralized.

### Is homogeneity is a good thing?
* Easier to program
* ABC (Asymmetric Broadcast Control)
### What about heterogeneity?
* Specialized robots with specialized sensors 

Heterogeneity in different papers:
* Task allocation paper: capabilities & hardware (cost and quality)
* Leader follower: differences in information (the leaders had the capability of following a trajectory)

In task allocation: $X$ is assignment. Sources of complexity in multi-robot systems:
1. Larger team size
2. Heterogeneity of robots and tasks

Fundamental question: which robot should execute which task to achieve a global goal?
* The problem has different levels of difficulty
    * In the case where there is an unmatched number of robots and tasks, if $M$ the number of tasks is greater than $N$ the number of robots, this requires a lookahead.
    * What is optimality? Formulate an optimization problem and solve it to get an "optimal" assignment

### Target Tracking Example for Task Allocation
Given $m$ workers, $n$ prioritized jobs, $u_{ij}$ utility estimate. 

*Goal*: Assign workers to jobs to maximize utility. In the tracking case, $u_{ij}=-d(q_i, q_j)$, utility is the negative distance from a target.

Other examples: Ride sharing,

**Discrete:** deliver this package to room 101
**Continuous:** monitor building entrace for intruders

**Task independece**: strong assumption but sometimes holds (current paper)

What happens if:
* $m = n$
* $m < n$
* $m > n$
* $n$ is dynamic

### Taxonomy for MRTA
* Single Task Robot (ST) 
* Multi Task Robot (MT)
* Single Robot Task (SR)
* Multi Robot Task (MR)
* Instantaneous Assignment (IA)
* Time-extended Assignment (TA)

## Optimization Framework
* Utility function: cost, performance, etc...
Utility function: expected quality of task execution given method and equipment
* Expected resource cost

**Utility**: the link between control and optimization

Total utility:
$$U = \sum_{i=1}^{m}\sum_{j=1}^n a_{ij}U_{ij}w_j$$
where $a_{ij}$: assignment of robot $i$ to task $j$ (1 or 0), $U_{ij}$ utility gained by the completion of task $j$ by robot $i$, $w_j$ weight of job to prioritize.
* Constraints: Task independence, temporal dependence

### Two Important Concepts
* Centralized vs. Distributed solutions
    * Solution time
    * Communication overhead
    * Dependence on team size 
* Optimality:
    * Centralized solutions can solve optimally

**Optimality**: Why Important? Reason about the quality of our solution
* Greedy vs Optimal: Tie back to last class, is gradient descent optimal? No!
* Bounds of optimality: Idealized case (can arrive at optimal solutions) vs. Full complexity case (optimal solution must be approximated). 
* Concept of $\alpha$ competitiveness

Algorithm 1: Linear program OR Distributed auction algorithm. Complexity $\mathcal{O}(mn^2)$

Algorithm 2: Broadcast of Local Eligibility (BLE) (2-competitive)

### Dynamic Tasks: What if tasks are randomly injected into the system over time?
Algorithm 3: MURDOCH assignment algorithm:
1. When a task is introduced, assign it to the most fit robot that is currently available (Algorithm 1)

Without more information, it is impossible to create a better algorithm.

### ST, SR, TA (time extended)
* More tasks that robots $m > n$
* Model of how tasks will arrive
* Robots' future utilities for tasks

Algorithm 4: Optimality: 3-competitive (online greedy bound)
1. Optimally solve the initial $m\times n$ assignment
2. Use greedy algorithm to assign remaining tasks in an on-line fashion, as robots become available
* Real life example: Uber pool?

### Example: IKEA assembly
* Approach: "Coalition formation"
* Split the set of robots into task-specific coalitions.

**Breaking the problem down**: Use a known algorithm that is optimal for a simpler problem, to produce a suboptimal solution to a hard problem.
* Making the partition allows us to break the problem down and solve it.
* Greedy algorithm appears again!
