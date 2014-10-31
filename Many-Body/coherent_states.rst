.. coherent_states

===============
Coherent States
===============

Boson Coherent State
--------------------

Single Boson operator
'''''''''''''''''''''
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
   \hat{b}\ket{b} &= \sum_n\hat{b}\ket{n}\frac{b^n}{\sqrt{n!}}
    =\sum_n \sqrt{n}\ket{n-1}\frac{bb^{(n-1)}}{\sqrt{n}\sqrt{(n-1)!}}
    =b\sum_n\ket{n}\frac{b^n}{\sqrt{n!}} = b\ket{b} \\
   \bra{\bar{b}}\hat{b}^\dagger &= \bra{\bar{b}}\bar{b}

The overlap between 2 states is

.. math::
  \braket{\bar{b}_1|b_2}=\sum_{n,m}\frac{\bar{b}_1^n}{\sqrt{n!}}\braket{n|m}
  \frac{b_2^m}{\sqrt{m!}} =\sum_n\frac{(\bar{b}_1 b_2)^2}{n!}=e^{\bar{b}_1 b_ 2}

The amplitude for a coherent state to be in a state of $n$ particles
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

The matrix elements of an operator, that is normal ordered, are described by:

.. math::
  \bra{\bar{b}_1}\hat{O}(\hat{b}^\dagger,\hat{b})\ket{b_2}
   = O(\bar{b}_1,b_2)e^{\bar{b}_1 b_ 2}

The unit operator is established as:

.. math::
  \hat{1} = \int \frac{d\bar{b}db}{2\pi i}e^{-\bar{b} b} \ket{b}\bra{\bar{b}}

Many boson operators
''''''''''''''''''''

The previous definition of a single boson operator coherent state can be extended to a
many states system in which one only needs to use the creation operators for
other states over a basis set $\{\ket{\alpha}\}$ finite or infinite.
As such a coherent state is established as:

.. math::
  \ket{\varphi} &= e^{b_1\hat{b}^\dagger_1}e^{b_2\hat{b}^\dagger_2}\cdots e^{b_p\hat{b}^\dagger_p} \cdots \ket{\emptyset} \\
   &=\exp(\sum_\alpha b_\alpha \hat{b}_\alpha^\dagger)\ket{\emptyset} \\
  \bra{\bar{\varphi}} &= \bra{\emptyset}\exp(\sum_\alpha \bar{b}_\alpha\hat{b}_\alpha)

This coherent states continue to be eigenstates of the annihilation operators

.. math::
  \hat{b}_\alpha\ket{\varphi} &= b_\alpha\ket{\varphi} \\
  \bra{\bar{\varphi}}\hat{b}^\dagger_\alpha &= \bra{\bar{\varphi}}\bar{b}_\alpha

also

.. math::
  \hat{b}^\dagger_\alpha \ket{\varphi}
   &= \hat{b}^\dagger_\alpha\exp(\sum_\alpha b_\alpha \hat{b}_\alpha^\dagger)\ket{\emptyset} \\
   &= \frac{\partial}{\partial b_\alpha} \exp(\sum_\alpha b_\alpha \hat{b}_\alpha^\dagger)\ket{\emptyset} \\
   &= \frac{\partial}{\partial b_\alpha} \ket{\varphi} \\
   \Rightarrow \bra{\bar{\varphi}}\hat{b}_\alpha &= \frac{\partial}{\partial \bar{b}_\alpha} \bra{\bar{\varphi}}

The commutator:

.. math::
  [\hat{b}_\alpha,\ket{\varphi}\bra{\bar{\varphi}}]=\left(b_\alpha - \frac{\partial}{\partial \bar{b}_\alpha}\right)\ket{\varphi}\bra{\bar{\varphi}}


And the many-particle closure relation is obeyed:

.. math::
  \hat{1} = \int \prod_\alpha \frac{d\bar{b}_\alpha db_\alpha}{2\pi i}e^{-\bar{b}_\alpha b_\alpha} \ket{\varphi}\bra{\bar{\varphi}}

Examples
""""""""
The distribution of particle numbers has the average value

.. math::
  \braket{\hat{N}} &= \frac{\braket{\bar{\varphi}|\hat{N}|\varphi}}{\braket{\bar{\varphi}|\varphi}} \\
   &=\frac{\sum_\alpha \braket{\bar{\varphi}|\hat{b}_\alpha^\dagger\hat{b}_\alpha|\varphi}}{\braket{\bar{\varphi}|\varphi}} \\
   &=\sum_\alpha \bar{b}_\alpha b_\alpha

and the variance

.. math::
  \braket{\delta N} &= \braket{\hat{N}^2} - \braket{\hat{N}}^2 \\
   &=\frac{\sum_{\alpha\beta} \braket{\bar{\varphi}|\hat{b}_\alpha^\dagger\hat{b}_\alpha \hat{b}_\beta^\dagger\hat{b}_\beta|\varphi}}{\braket{\bar{\varphi}|\varphi}} - \braket{\hat{N}}^2 \\
   &=\frac{\sum_{\alpha\beta} \braket{\bar{\varphi}|\hat{b}_\alpha^\dagger(\delta_{\alpha\beta} +
     \hat{b}_\beta^\dagger\hat{b}_\alpha)\hat{b}_\beta|\varphi}}{\braket{\bar{\varphi}|\varphi}} - \braket{\hat{N}}^2 \\
   &= \sum_\alpha \frac{\braket{\bar{\varphi}|\bar{b}_\alpha b_\alpha|\varphi}}{\braket{\bar{\varphi}|\varphi}}
    + \sum_{\alpha\beta} \frac{\bar{b}_\alpha\bar{b}_\beta b_\alpha b_\beta \braket{\bar{\varphi}|\varphi}}{\braket{\bar{\varphi}|\varphi}} - \braket{\hat{N}}^2\\
   &=\braket{\hat{N}}

Fermion Coherent State
----------------------
