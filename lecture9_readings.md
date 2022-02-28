# Paper 1: Robust Control for Mobility and Wireless Communication in Cyber-Physical Systems with Applications to Robot Teams
## Communication aware mobility control
1. How to translate robot positions into information about the point-to-point rates
2. How the cyber-physical control loop utilize point-to-point connectivity information in order to ensure end-to-end network integrity
3. How to deal with uncertainty in the information about point-to-point channels between individual pairs of robots

**Model 1**: Identify connectivity with proximity and LOS visibility.
* Keep the point-to-point connections connected
* Advantage: second largest eigenvalue (fiedler value) of the laplacian and k-connectivity are computationally tractable
    * Computational complexity is similar to communication-unaware networks
* Disadvantage: Binary connectivity is not realistic. We should rather consider the probability of information transfer

**Model 2**: Use the probability of delivery objective function
* Similar to **Model 1**, but use weighted graph to denote the probabilities
* Advantages: similar complexity benefits to model 1

The initial control loop proposed restricts mobility to ensure connectedness based on these models. However, this is not truly cyber-physical as we do not use the advantages of physical systems to ensure connectivity.

## Robust Cyber-physical control
We need to look at achievability of target end-to-end communication rates.
* However, achievability of end-to-end rates cannot be guaranteed because of rate uncertainties, so we can redefine survivability in terms of probability of end-to-end rates exceeding their basal rates.
