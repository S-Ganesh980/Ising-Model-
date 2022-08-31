# Ising-Model-
 Implementing 2-dimensional Ising model using the Metropolis algorithm and NUMBA 

 Here we will try to solve the two dimensional Ising model using the Metropolis Algorithm which is specifically designed to get to the equilibrium state of the magnetic lattice at a particular temperature. 

 A system of magnetic particles can be modeled as a linear chain in one dimension or a lattice in two dimension, with one molecule or atom at each lattice site $i$. To each particle a magnetic moment is asigned that is represented by a discrete variable $\sigma_i$. Each spin $\sigma$ can only have a value of $\sigma_i = \pm 1$. If the spins are aligned, then, $\sigma_i. \sigma_j = +1 $, otherwise, $\sigma_i. \sigma_j = -1 $. 
 A system of two spins is considered to be in a lower energetic state if the two magnetic moments are aligned, otherwise, it is considered to be in a higher energy state. Due to this interaction, the system tends to align all magnetic moments in one direction in order to minimize enrgy. If nearly all magnetic moments point in the same direction, the arrangement of particles behave like a macroscopic magnet. 
 
 Transition from an ordered to a disordered state is called Phase transition. A ferromagnet at temperature above the critical temperature is in a disordered state. In the Ising model, this corresponds to a random distribution of spin values. However, below the critical temperature, nearly all spins are aligned even in the absence of an externally applied magnetic field. 
 
 Due to the existence of an exact analytical solution, the Ising model has a myraid of applications: 
 1. Ising model is an effective model to study financial systems in which decision making plays an important role. In [1], the dynamics of the stock market was studied by looking at entropy, stock returns and correlation length to study the
characteristics of stock market during crash. 
 2. To describe DNA structures in biopolymers [2]
 3. One dimensional Ising model can be used to study the spread of diseases, to model the speed of contamination. The spin in the context would refer to the people infected/not infected. [3]

To solve the Ising model, here we first consider a system(lattice of particles) which is in thermal equilibrium with it's surroundings. The probability of being in state $\mu$ with energy $E_\mu$ is $$p_{\mu}= \frac{1}{Z} e^{-\beta E_{\mu}}$$ where $\beta$ is the Boltzmann's distribution($\beta = \frac{1}{kT}$, k= Boltzmann's constant and T= temperature of the surroundings), $Z$ is the partition function. 

A system in any surrounding changes until it reaches equilibrium. At equilibrium, a condition called 'detailed-balance', which is as follows, must hold. $$p_\mu P(\mu \rightarrow \nu) = p_\nu P(\nu \rightarrow \mu)$$ where $P(\mu \rightarrow \nu)$ is the probability of going from state $\mu$ to $\nu$. 

The total energy of an Ising model is: $$E_{\mu}= \Sigma_{<i,j>} -J \sigma_i \sigma_j$$ where $J$ is the constant of proportionality and $\Sigma$ signifies the sum over nearest neighbours for all lattice points. Thus, according to the detailed-balance equation, 
$$\frac{P(\mu \rightarrow \nu)}{P(\nu \rightarrow \mu)} = \frac{p_{\nu}}{p_{\mu}} = e^{-\beta(E_\nu - E_\mu)}$$.

To summarize, our lattice which is initially in a random state is going to change when placed in a temperature bath until it attains equilibrium in accordance with the equation of detailed balance. We have to manually code the transition probabilities, this is where the Metropolis Algorithm comes into action. Ultimately, the goal is to find the equilibrium state at a particular temperature. 





References: 

[1] DYNAMICS OF STOCK MARKET,
USING ISING MODEL
Lisha DAMODARAN
 and K. M. UDAYANANDAN
 
 [2] M. Leung, F. Choo, and B. Tong. “Application of modified Ising model to the helix-coil
transition of DNA molecules”. In: Biopolymers. 16(6):1233-44 (1977)


[3] I. Mello et al. “Epidemics, the Ising-model and percolation theory: a comprehensive
review focussed on Covid-19”. In: Physica A p. 125963 (2021).
