# CS 286 Lecture Notes: February 14
### Announcements:
List team members on sign-up sheet.

### Last time:
* Introduction to consensus
* Different types of consensus
    * Just agreement? (rendezvous for example)
    * Agreement to a particular value (average consensus for example)
* When can we guarantee it will work
* Discrete time consensus:
$$x_{i}(k+1) = x_{i}(k) + \epsilon \sum_{j=1}^{n} a_{ij}(x_j(k)-x_i(k))$$
Average is $\overline{x} = \frac{\mathbf{11}^T}{n}x(0)$ ($11^T$ is an $n \times n$ matrix of ones).

**Q:** Can consensus be written as a gradient descent problem?

$\dot{x}=-Lx(t)$.

Quadratic disagreement function:
$$\varphi(x) = \frac{1}{2} x^T L x= \frac{1}{2}\sum_{(i,j) \in E} a_{ij}(x_j-x_i)^2$$
If $L$ is positive definite, the function $\varphi$ is convex.

Fiedler Value: 2nd smallest eigenvalue of $L$

Relation to Connectivity: 2nd smallest eigenvalue non-zero. $L$ captures the graph type.

**Performance guarantees**: 
* Does my consensus algorithm converge?
* Rate: how quickly we can converge?

### Metrics of Interest:
* Convergence
    * Oscillation around consensus caused by adversarial nodes
    * Switching networks, switching nodes inputting information only at particular times
* To what value are we converging?
    * Average
    * Convex Hull (the smallest polytope that contains all of the initial states)
    * Min, Max

### Graph Theory Review
* Balanced graph:
    * In degree = Out degree
* Strongly Connected Graph
    * In a digraph, there is a path from node $i$ to node $j$ for every $i \neq j$
* Graph Laplacian vs. Connectivity
    * For undirected graphs, the second smallest eigenvalue > 2 means the graph is connected
    * For directed graphs, if $G$ is strongly connected, then $\mathrm{rank}(G) = n-1$.
$$0 =\lambda_1 \leq \lambda_2 \leq \lambda_3 \leq \dots \leq 
\lambda_n 
\leq 2\Delta, \text{ where  } \Delta = \max_{i}d_i$$

**Small world network**
**Balanced Digraph**: A node $v_i$ of a digraph is balanced iff its in-degree and out-degree are equal:
$$\sum_{j}a_{ij}=\sum_{j}a_{ji}, \forall i $$
* Easier case: Undirected graph --> connected --> average consensus
* Harder case: Directed --> Balanced and Strongly Connected --> Average Consensus
* Even harder case: Switching topology --> Union of graphs over time connected -->

$$\|\varphi(t)\| \leq \|\varphi(0)\|\exp(-\lambda(\hat{G})t)$$

### Two Ways to achieve Fast Convergence:
1) Control the graph topology (example: small world networks)
2) Design the consensus weights

In Fast Linear Iterations (FLI) paper, design the weight matrix such that convergence is fastest. Can the global properties of the graph be computed locally?