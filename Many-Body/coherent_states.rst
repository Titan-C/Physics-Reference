.. coherent_states

===============
Coherent States
===============

Boson Coherent State
--------------------

Single Particle
'''''''''''''''
Start defining a bosonic state element of the Fock space, which is an eigenstate
of the annihilation operator. As such $\hat{b}\ket{b} = b\ket{b}$ and it can be
constructed in the form:

.. math::
   \ket{b} &= e^{b\hat{b}^\dagger}\ket{\emptyset}
   = \sum_n \frac{b^n}{n!} (\hat{b}^\dagger)^n\ket{\emptyset}
   = \sum_n\ket{n}\frac{b^n}{\sqrt{n!}} \\
   \bra{\bar{b}} &= \bra{\emptyset}e^{\bar{b}\hat{b}}
   = \sum_n \frac{\bar{b}^n}{n!} \bra{\emptyset}(\hat{b})^n
   = \sum_n\frac{\bar{b}^n}{\sqrt{n!}}\bra{n}

Then it is clear the corresponding eigenstate

.. math::
   \hat{b}\ket{b}= \sum_n\hat{b}\ket{n}\frac{b^n}{\sqrt{n!}}
    =\sum_n \sqrt{n}\ket{n-1}\frac{bb^{(n-1)}}{\sqrt{n}\sqrt{(n-1)!}}
    =b\sum_n\ket{n}\frac{b^n}{\sqrt{n!}} = b\ket{b}

The overlap between 2 states is

.. math::
  \braket{\bar{b}_1|b_2}=\sum_{n,m}\frac{\bar{b}_1^n}{\sqrt{n!}}\braket{n|m}
  \frac{b_2^m}{\sqrt{m!}} =\sum_n\frac{(\bar{b}_1 b_2)^2}{n!}=e^{\bar{b}_1 b_ 2}

The probability amplitude for a coherent state to be in a state of $n$ particles
is

.. math::
   A(b) = \braket{n|b}=\frac{b}{\sqrt{n!}}

And the normalized probability to be in a state $\ket{n}$ is give by

.. math::
   p(n) = \frac{|\braket{n|b}|^2}{\braket{\bar{b}|b}} = \frac{(\bar{b}b)^n}{n!}e^{-\bar{b}b}

.. plot::

  import numpy as np
  import matplotlib.pyplot as plt
  from scipy.misc import factorial

  n = 7
  m = np.arange(2.5*n)
  p_n = n**m*np.exp(-n)/factorial(m)
  plt.bar(m-0.5, p_n)
  plt.xlabel('\$n\$')
  plt.ylabel('\$p(n)\$')
  plt.xlim([-0.6,m[-1]+1])
  plt.title('Probability distribution fo a coherent state with \$\\bar{b}b=n_0=7\$')

Fermion Coherent State
----------------------
