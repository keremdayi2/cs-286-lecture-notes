# CS 286 Lecture 9: Realistic Considerations

### Recap of Basic Theory Concepts
* How to encode relationships between agents, information and control: Graphs
* Key *link* between optimization and control for multi robot-system (Gradient descent optimziation)
    * Identify a cost/utility function
    * Optimize the function over robot state (that we control)
    * Performance guarantees
* Types of controllers
    * Gradient Descent, easy to implement 
    * Linear programs
    * Mixed integer programs
    * Neural Networks
* Desirable properties of the choice of optimization
    * Can be distributed
    * Can be solved quickly (time complexity)
    * Solution type (global, local, etc.)
    * Performance guarantees?
### Realistic Considerations
1. Major vulnerabilities not discussed in previous papers

2. Ideas for how to address these vulnerabilities

3. How are today's papers different?

**Today**: Role of assumptions as we consider challenges that these systems face in the real world:
* Unreliable communication, Security considerations, uncertainty.

> Theory + Practice = Impact

