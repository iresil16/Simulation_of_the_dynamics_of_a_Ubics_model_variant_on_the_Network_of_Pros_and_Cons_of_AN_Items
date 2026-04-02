# Ubics Variant Simulation on a Network of Pros & Cons of AN Items

This repository contains a NetLogo implementation of a **Ubics model variant** applied to a Network of Pros and Cons of AN Items. 

The code was developed starting from the original implementation available at https://github.com/hvdmaas/zeromatters/tree/main. It has been revisited and extended with additional parts that can be identified in the code by searching for the sections labeled `addition_i`, where `i` denotes the different additions introduced in this variant. These extensions allow the exploration of additional scenarios and emergent behaviors on an empirical network structure.

The simulation must be run within the NetLogo environment.(https://www.netlogo.org/)



##  Model Overview

The model simulates a ternary spin system where each node can take values:

- -1 (negative state)  
- 0 (neutral state)  
- +1 (positive state)

The dynamics are governed by the Metropolis algorithm.


##  Ubics Variant Hamiltonian

The implemented model is a variant of the Ubics model, characterized by the following Hamiltonian:

$$
H(\mathbf{x}) = - \sum_{\langle i,j \rangle} \sigma \omega_{ij} x_i x_j - \sum_i \tau x_i - \sum_{\langle i,j \rangle} \alpha (x_i^2 - 1)\alpha (x_j^2 - 1).
$$


- **σ (sigma)**: global coupling parameter  
- **w₍ᵢⱼ₎**: edge weights (range [-1, 1])  
- **τ (tau)**: external field  
- **α (alpha)**: controls the tendency toward neutral states  
- **xᵢ ∈ {-1, 0, +1}**: node states  

### Important differences from the original Ubics model:

- The interaction term is **modulated by weights w₍ᵢⱼ₎**, introducing heterogeneous interactions.
- In some scenarios, **only the sign of the weights is used** (sign matrix variant), while in others the **weighted matrix** is used.
- The inclusion of weights allows the model to represent both **positive and negative relationships** in the network.

## Network

The simulations are performed on a custom network representing a **Network of Pros and Cons of AN Items**, with connections estimated from data.

Two versions are used:

- `MyCustomNetwork` → uses sign-based interactions  
- `MyCustomNetworkWeighted` → uses weighted interactions (w₍ᵢⱼ₎ ∈ [-1, 1])



##  Scenarios

Additional scenarios introduced in this variant are defined under the `addition_4` section of the code.

Each scenario fixes the model parameters and varies one control parameter over time to observe phase transitions.

### 1. Double / Pinched Hysteresis (τ variation)

- Varying parameter: **τ**

Scenarios:
- `"P: My Custom Network: Double or pinched hysteresis (tau) with Ubics variant"`
- `"S: My Custom Network Weighted: Double or pinched hysteresis (tau) with Ubics variant"`



### 2. Bifurcation (Temperature variation)

- Varying parameter: **temperature (T)**

Scenarios:
- `"Q: My Custom Network: Bifurcation (temperature) with Ubics variant"`
- `"T: My Custom Network Weighted: Bifurcation (temperature) with Ubics variant"`



### 3. Tricritical Transition (α variation)

- Varying parameter: **alpha (α)**

Scenarios:
- `"R: My Custom Network: Tricritical transition (alpha) with Ubics variant"`
- `"U: My Custom Network Weighted: Tricritical transition (alpha) with Ubics variant"`



## How to Run

1. Open the `.nlogo` file in NetLogo  
2. Select one of the predefined scenarios  
3. Run the simulation  
4. Observe:
   - Magnetization over time  
   - Network configurations  
   - Phase transitions  



##  References

- van der Maas, H. L., Borsboom, D., & Waldorp, L. (2026). *The statistical physics of psychological networks: Zero matters*. Psychological Review.
- Original implementation:  
  https://github.com/hvdmaas/zeromatters/tree/main



## Notes

- This repository contains a **variant of the Ubics model** adapted to incorporate:
  - weighted interactions
  - empirical network structure
  - additional simulation scenarios
- The goal is to explore how these modifications affect emergent phenomena compared to the original model.
