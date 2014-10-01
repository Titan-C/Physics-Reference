.. second_quantization

===================
Second Quantization
===================

Fock space
----------

Calling $H_N$ the Hilbert space with $N$ particles ($H_j = \otimes_{i=1}^j 
H_j$) define

.. math::
   \mathcal{F} = \oplus_{j=0}^{+\infty} H_j

the direct sum of all Hilbert spaces with 0,1,2, etc particles. This space is 
the Fock space.


Creation and Annihilation  operators
------------------------------------

For each state $\alpha_i$ of 
the single particle complete basis, the Creation and Annihilation operators 
will increase or decrease by one the number of particles in this particular 
state.

Bosons
''''''

.. math::
   a^\dagger_j|n_1,\cdots,n_i,\cdots,n_\Omega\rangle &= \sqrt{n_i + 1} |n_1,\cdots,n_i+1,\cdots,n_\Omega\rangle \\
   a_j|n_1,\cdots,n_i,\cdots,n_\Omega\rangle &= \sqrt{n_i} |n_1,\cdots,n_i-1,\cdots,n_\Omega\rangle \\

Commutator relations
""""""""""""""""""""

.. math::
   [a_i,a^\dagger_j] & = \delta_{ij} \\
   [a^\dagger_i,a^\dagger_j] &= 0 \\
   [a_i,a_j] &=0
   

Fermions
''''''''
.. math::
   c^\dagger_j|n_1,\cdots,n_i,\cdots,n_\Omega\rangle &= (1-n_i)(-1)^\epsilon_i |n_1,\cdots,n_i+1,\cdots,n_\Omega\rangle \\
   c_j|n_1,\cdots,n_i,\cdots,n_\Omega\rangle &= n_i(-1)^\epsilon_i |n_1,\cdots,n_i-1,\cdots,n_\Omega\rangle \\

Using $\epsilon_i = \sum_{j=1}^{i-1} n_j$ and $\epsilon_0 = 0$, a phase factor 
to guaranty the anti-symmetric character of the wave-functions under particle 
permutationexchange

Anti-commutation relations
""""""""""""""""""""""""""

.. math::
   \{c_i,c^\dagger_j\} & = \delta_{ij} \\
   \{c^\dagger_i,c^\dagger_j\} &= 0 \\
   \{c_i,c_j\} &=0

One body operators
------------------

Starting with an operator for single particle $O^{(1)}$, that acts on the 
complete single particle basis set it is obtained.

.. math::
   O = \sum_{\alpha,\beta} \langle\alpha|O^{(1)}|\beta\rangle c_\alpha^\dagger 
   c_\beta

It's the transition from one state $\alpha$ into state $\beta$ for the one
particle. But acting on all particles on each state by the operators, and 
leaving the other quantum numbers invariant. $O$ acts on vectors of Fock Space.

Example
'''''''

Take the particle density at $\vec{r}_0$. The single particle operator is 
$\rho(\vec{r}_0)^{(1)} = \ket{\vec{r}_0} \bra{\vec{r}_0}$. Then to 
build the many particle density and including spin just take:

.. math::
   \rho(\vec{r_0}) &= \sum_{r,\sigma,r',\sigma'}
   \braket{ \vec{r}\sigma | \vec{r}_0} 
   \braket{ \vec{r}_0 | \vec{r}'\sigma'} 
   c^\dagger_{r\sigma}c_{r'\sigma'} \\
   &=  \sum_{r,\sigma,r',\sigma'}
   \delta(\vec{r}- \vec{r}_0)   \delta(\vec{r}- \vec{r}_0)
   \delta_{\sigma\sigma'}   c^\dagger_{r\sigma}c_{r'\sigma'} \\
   &=c^\dagger_{r_0\uparrow}c_{r_0\uparrow} + 
   c^\dagger_{r_0\downarrow}c_{r_0\downarrow}