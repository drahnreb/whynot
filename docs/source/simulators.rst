.. _simulators:

Simulators
==========
WhyNot provides a large number of simulated environments from fields ranging
from economics to epidemiology. Each simulator comes equipped with a
representative set of causal inference experiments and will export a uniform
Python interface that makes it easy to construct new causal inference
experiments in these environments.

The simulators in WhyNot can be split into two main categories: system
dynamics models which use differential equations to model interactions between
different components of a system over time and agent-based models which
represent a system as a collection of interacting, heterogeneous agents. Below
we describe the set of simulators currently available in WhyNot.

*Disclaimer:* The simulators in our work are not intended to be realistic
models of the world, but rather realistic models of the technical difficulties
that the real world poses for causal inference. In many cases, the simulators
present in WhyNot have been disputed and criticized as models of the real
world.

Overview
--------
Dynamical systems based simulators:

* :ref:`adams-hiv-simulator`
* :ref:`dice-simulator`
* :ref:`zika-simulator`
* :ref:`opioid-simulator`
* :ref:`world3-simulator`
* :ref:`world2-simulator`
* :ref:`lotka-volterra-simulator`
* :ref:`delayed-impact-simulator`
* :ref:`credit-simulator`

Agent-based simulators:

* :ref:`incarceration-simulator`
* :ref:`civil-violence-simulator`
* :ref:`schelling-simulator`

Others:

* :ref:`lalonde-simulator`

Adding more simulators to WhyNot is easy and allows one to take advantage of
WhyNot tools for rapidly creating and running new causal inference experiments.
For more information, see :ref:`adding-a-simulator`. For additional API
reference, including specification of simulator states, configurations, and
supported interventions, see :ref:`Simulator API <simulator_api>`.


.. _adams-hiv-simulator:

HIV Treatment Simulator 
^^^^^^^^^^^^^^^^^^^^^^^
The HIV treatment simulator is a differential equation simulator of HIV treatment based on

Adams, Brian Michael, et al.  *Dynamic multidrug therapies for HIV: Optimal and
STI control approaches.* North Carolina State University. Center for Research in
Scientific Computation, 2004.

The Adams HIV model has a set of 6 state and 20 simulation parameters to
parameterize the dynamics. We omit listing all of them here and refer the reader
to the API documentation (:ref:`hiv`) for more details.


.. _dice-simulator:

Dynamic Integrated Climate Economy Model (DICE)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
`The Dynamice Integrated Climate Economy Model (DICE)
<https://en.wikipedia.org/wiki/DICE_model>`_ is a computer-based integrated
assessment model developed by 2018 Nobel Laureate William Nordhaus that
“integrates in an end-to-end fashion the economics, carbon cycle, climate
science, and impacts in a highly aggregated model that allows a weighing of the
costs and benefits of taking steps to slow greenhouse warming."

The DICE model has a set of 26 state and 54 simulation parameters to
parameterize the dynamics. We omit listing all of them here and refer the
reader to the API documentation (:ref:`dice`) for more details.

.. _zika-simulator:

Zika Epidemic Prevention Simulator
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The Zika simulator is dynamical systems model of transmission and control of the
Zika virus disease. The simulator is based on:

Momoh, Abdulfatai A., and Armin Fügenschuh. "Optimal control of intervention
strategies and cost effectiveness analysis for a Zika virus model." Operations
Research for Health Care 18 (2018): 99-111.

The intended purpose of the model was to study the efficacy of various
strategies for controlling the spread of the Zika virus: the use of treated
bed nets, the use of condoms, a medical treatment of infected persons, and the
use of indoor residual spray (IRS). The dynamics of the Zika model govern the
evolution of 9 state variables, and the simulator has four control variables
and 20 simulation parameters. See :ref:`zika` for precise details.


.. _opioid-simulator:

Opioid Epidemic Simulator
^^^^^^^^^^^^^^^^^^^^^^^^^
The opioid epidemic simulator is a system dynamics model of the US opioid
epidemic developed by `Chen et al.
<https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2723405>`_ (JAMA,
2019). The model is calibrated based on past opioid use data from the Center
for Disease Control and was developed to simulate the effect of interventions
like reducing the number of new non-medical users of opioids on future opioid
overdose deaths in the United States. The simulator is a time-varying
differential equations model in 3 variables. For a complete description of the
model, please refer to the appendix of `Chen et al.
<https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2723405>`_, and
see :ref:`opioid` for more details about the state variables and simulation
parameters.


.. _world3-simulator:

World3
^^^^^^
`World3 <https://en.wikipedia.org/wiki/World3>`_ is a systems dynamics model
commissioned by the Club of Rome in the early 1970s to illustrate the
interactions between population growth, industrial development, and the
limitations of the natural environment over time.

The model is a differential equation model with 12 state variables and 245
algebraic equations governing their evolution over time. See :ref:`world3` for a
complete description of the state variables and parameters.


.. _world2-simulator:

World2
^^^^^^
World 2 is a systems dynamics model developed by `Jay Forrester
<https://en.wikipedia.org/wiki/Jay_Wright_Forrester>`_ to demonstrate the
tension between industrial growth and natural resource limitations. The model
is a precursor to the World3 model and, although it was used to study similar
questions, it represents different dynamics.

The model is a system of differential equations in 5 variables corresponding to
quantities and 43 algebraic equations governing their evolution over time.
See :ref:`world2` for a complete description of the state variables and parameters.


.. _civil-violence-simulator:

Civil Violence Simulator
^^^^^^^^^^^^^^^^^^^^^^^^
Civil Violence is an agent-based model of civil violence `introduced by Joshua
Epstein in 2002 <http://www.pnas.org/content/99/suppl_3/7243>`_. The model was
originally used to study the complex dynamics of decentralized rebellion and
revolution and to examine the state's efforts to counter these dynamics. The
model consists of two types of actors: agents and cops. Agents are
heterogeneous, and their varied features make them more or less likely to
actively rebel against the state. The rich dynamics of the model emerge from
the interaction between agents and between agents and cops: agents are more
likely to begin rebel if other agents start to rebel, and the cops attempt to
arrest rebelling agents. See :ref:`civil_violence` for a complete description of
the agents and the simulation parameters.

The implementation of this simulator is taken from the `examples
<https://github.com/projectmesa/mesa/tree/master/examples>`_ of the `mesa
library <https://github.com/projectmesa>`_.

.. _incarceration-simulator:

Incarceration Simulator
^^^^^^^^^^^^^^^^^^^^^^^
The incarceration simulator is based on the paper:

    Lum K, Swarup S, Eubank S, Hawdon J. *The contagious nature of
    imprisonment: an agent-based model to explain racial disparities in
    incarceration rates*.
    J R Soc Interface. 2014;11(98):20140409. `doi:10.1098/rsif.2014.0409
    <https://dx.doi.org/10.1098%2Frsif.2014.0409>`_

The paper proposes an agent-based model that models incarceration as
"contagious" in the sense that social ties to incarcerated individuals lead to
a higher risk of being imprisoned. The simulation occurs on a fixed set of
agents with a fixed set of social ties. What varies is the randomness with
which incarceration is passed on and randomness in sentence length. Transition
probabilities, and the sentence length distribution are based on real data.
The paper shows that higher-on-average sentence lengths for black individuals
than for whites lead to a disparity in incarceration rates that resembles the
one observed in the United States.


.. _lotka-volterra-simulator:

Lotka-Volterra Model
^^^^^^^^^^^^^^^^^^^^
Lotka-Volterra is a classical differential equation model of the interactions
between predator and prey in a single ecosystem. The model was originally
developed to understand and explain perplexing fishery statistics during World
War I, namely why the hiatus of fishing during the war led to an observed
increase in the number of predators.

For more details, see `Scholl 2012
<https://pdfs.semanticscholar.org/f314/7c9d2e43aafc492852f552990a3b21315ca5.pdf?_ga=2.132703694.1945084113.1556061073-1443175395.1541897531>`_.

The simulator is system of ordinary differential equations in two variables.
For a complete description of the dynamics, see
`here
<https://scipy-cookbook.readthedocs.io/items/LoktaVolterraTutorial.html>`_. The
state and simulator parameters are detailed in :ref:`lotka_volterra`.

.. _delayed-impact-simulator:

Delayed Impact Simulator
^^^^^^^^^^^^^^^^^^^^^^^^
The Delayed Impact is a lending simulator is based on the paper:

    Liu, L., Dean, S., Rolf, E., Simchowitz, M., & Hardt, M. (2018, July).
    Delayed Impact of Fair Machine Learning. In International Conference on
    Machine Learning (pp. 3156-3164). Chicago.

The paper proposes a simple lending model in which individuals apply for
loans, a lending institution approves or denies the loan on the basis of the
individual's credit score, and subsequent loan repayment or default in turn
changes the individual's credit score. Credit scores and repayment probabilities
are based on real FICO data. In this dynamic setting, the paper shows that
static fairness criterion do not necessarily promote improvement over time and
can indeed cause active harm.

.. _credit-simulator:

Credit Simulator
^^^^^^^^^^^^^^^^
The credit simulator is based on the paper:

    Perdomo, Juan C., Tijana Zrnic, Celestine Mendler-Dünner, and Moritz Hardt.
    "Performative Prediction." arXiv preprint arXiv:2002.06673 (2020).

The simulator reprises on a model of strategic classification in which
an institution classifies the creditworthiness of loan applicants, and agents
react to the institution’s classifier by manipulating their features to increase
the likelihood that they receive a favorable classification. The underlying
data comes from a Kaggle credit scoring dataset, though the agent response model
is synthetic.  The model was originally used to qualitatively analyze the
long-run properties of repeated retraining of classifiers in the face of
strategic adaptation.


.. _schelling-simulator:

Schelling Model
^^^^^^^^^^^^^^^
The `Schelling model
<https://www.stat.berkeley.edu/~aldous/157/Papers/Schelling_Seg_Models.pdf>`_
is a classic agent-based model originally used to illustrate how weak
individual preferences regarding one's neighbors can lead to global
segregation of entire cities. In the model, individuals prefer to live where
at least some fraction of their neighbors are the same race as they are and
will move if this constraint is not met. As this process is iterated, an
originally well-mixed city rapidly becomes segregated by group.

**Agents**
The agents in Schelling's model are labeled either Type 0 or Type 1,
corresponding to members of the majority or minority class.

**Simulation Parameters**

* Grid size (height, width)
* Agent density
* Percentage of minority agents
* Homophily
* Education boost (how much receiving ``education`` decreases homophily)
* Percentage of agents receiving education

The implementation of this simulator is taken from the `examples <https://github.com/projectmesa/mesa/tree/master/examples>`_ of the `mesa library <https://github.com/projectmesa>`_.

.. _lalonde-simulator:

LaLonde Synthetic Outcome Model
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The Lalone simulator is based on data from `Robert LaLonde's 1986 study
<https://www.jstor.org/stable/1806062>`_ evaluating the impact of the National
Supported Work Demonstration, a labor training program, on post-intervention
income levels. Since the actual function mapping the measured covariates to
the observed outcomes is unknown, we instead simulate random functions of
varying complexity on the data to generate synthetic outputs. This procedure
allows us to generate causal inference problems with response surfaces of
varying, but known complexity.

In the Lalonde data, the function mapping covariates :math:`X` to outcome
:math:`Y` is unknown, and it is impossible to simulate ground truth. Therefore,
following `Hill et al. <https://arxiv.org/abs/1707.02641>`_, we replace the
true outcome :math:`Y` with one generated by functions :math:`f_0, f_1`,
corresponds to control and treatment, as follows. Let :math:`W` denote
treatment assignment.
Then,

.. math::
    f_0(X) = Y(0),
    f_1(X) = Y(1),
    Y = Y(W).


