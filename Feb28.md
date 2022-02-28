
# CS 286 Lecture Notes, Feb 28
Communication Models 

## Euclidean Disk Model
Communication quality is mapped to distance between two agents.

* Communication Control: Mnimizing some function $\Psi(\mathbf{x})$ of the robot states $\mathbf{x}$ such that some communication constraint is protected. The control input is $\dot{\mathbf{x}}(u)$
* Idea: To control end-to-end connectivity, this paper co-optimizes the control of positions $\mathbf{x}$ with the control of communication routes $\alpha$.

### Determining Directional Signal Quality
* We can normally use multi-antenna receivers to determine the angle with which the signal arrived by looking at phase shifts.
* If we only have 1 antenna, we can move and sample. SAR (Synthetic Aperture Radar)

1. $V_{\theta max}$ 
2. Confidence $\sigma_{ij}$: capture variance around $\theta_{max}$ due to noise and/or multipath 

### Communication-as-a-Sensor
* We can sense over communication links
* 