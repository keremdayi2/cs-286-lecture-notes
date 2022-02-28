# February 16 Lecture Notes
### Last Time:
* Consensus performance guarantees
* Role of the graph
### Today's Goals
* Coverage:
* Tying it all together - coverage, consensus, and potential fields
* Convex vs. non-convex optimization problems and what this means for distributed robotics problems
* Think about: role of assumptions

### The coverage Problem:
* We have some operating environment and we want to deploy our agents such that they provide a uniform coverage of that environment.
* *Male Tilapia Fish*: 
* Robots exploring a building
* Search and rescue

Prior results not well suited to the multi robot problem
* They were centralized, limited size problems
* Known static environments
* The ability to handle dynamic environments.
## Discussion of paper
* Algorithm properties:
    * Adaptive, Distributed, Asynchronous, Verifiably asymptotically correct
* $W_i$'s partition the polygonal environment

$$Q: \text{Convex polytope in } \mathbb{R}^n$$

* The importanc function $\phi$ denotes how important it is to provide coverage to each point in the polygon.

$$H(P,W) = \sum_{i=1}^{n}\int_{W_i}f(\|p-q_i\|\phi(q)dq$$

1) Minimize cost with respect to sensor locations, $p$

$W_i$'s are a partition of $Q$. Claim: The optimum position for each agent is the center of its Voronoi region:

$$V_i = \left\{a \in Q : \|q-p_i\| \leq \|q-p_j\|, \forall j \neq i\right\}$$
* Design a controller that converges to this optimum.

$$H_V(P) = \int_{Q} \min_{j= 1,2,\dots,n}f(\|q-p_i\|)\phi(q)dq$$

Then, 
$$\frac{\partial H}{\partial p_i}(P) = 2M_{V_i}(p_i - C_{V_i})$$
$M_{V_i}$ is the mass of the voronoi partition. $C_{V_i}$ is the centroid of the voronoi partition. $\dot{p}_i = u_i$. Thus, $u_i = -k_{prop}(p_i-C_{V_i}$).

* Simple controller leads to stable and optimal solution.

### Unifying Geometric, Probabilistic, and Potential Field Approaches to Multi-Robot Deployment
$$g(...) = \left(\sum_{i=1}^{n}f(p_i, q)^\alpha\right)^{\frac{1}{\alpha}}$$
**Paper Assumptions**: 
* Robots know their locations
* Robots know the environment
* Assume convex environment
* 