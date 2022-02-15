# CS 286 Lecture 6
Consensus:
* Leader follower algorithms 
* Gradient Descent
* Introduction to consensus

Consensus for mobile (dynamic) networks: 
- Center and shape of a formation
- Rendezvous
- Probability of finding a target of interest
- Flocking

($v_1$)---($v_2$)---($v_3$)

$$a=\begin{bmatrix} 0 & 1 & 0\\
1 & 0 & 1\\
0 & 1 & 0 \end{bmatrix}$$

$$x_{i}(k+1) = x_i(k) + \epsilon \sum_{j \in \mathcal{N}_i}a_{ij}(x_j(k)-x_i(k))$$
Initial states: $x_1(0)=x_2(0)=x_3(0)=1$. Then $x_1(1)=x_2(1)=x_3(1) = 1$. Fixed point.

Fully connected graph with initial values $x_1 = 1$, $x_2 =0$, $x_3 = 2$ with $\epsilon =\frac{1}{3}$. Thus
$$x_1(1) = 1 + \epsilon \left[-1 + 1\right]= 1$$
$$x_2(1) = 0 + \frac{1}{3} \left[1 + 2\right]= 1$$
$$x_3(1) = 2 + \frac{1}{3} \left[-2 -1\right]= 1$$

Initial graph: $$x_1(1)=\frac{2}{3}, x_2(1) = 0 + 1= 1, x_{3}(1) = \frac{4}{3}$$
$$x_1(2) = \frac{7}{9}, x_2(2) = 1, x_{3}(3) = \frac{11}{9}$$