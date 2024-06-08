*Finite State Transducer*
=============================
A finite-state transducer (FST) is a finite-state machine with two memory tapes, following the terminology for Turing machines: an input tape and an output tape. This contrasts with an ordinary finite-state automaton, which has a single tape. An FST is a type of finite-state automaton that maps between two sets of symbols.[1] An FST is more general than a finite-state automaton (FSA). An FSA defines a formal language by defining a set of accepted strings, while an FST defines relations between sets of strings.

An FST will read a set of strings on the input tape and generates a set of relations on the output tape. An FST can be thought of as a translator or relater between strings in a set.

In morphological parsing, an example would be inputting a string of letters into the FST, the FST would then output a string of morphemes.

*Formal Construction*
*********************
Formally, a finite transducer T is a 6-tuple (Q, Σ, Γ, I, F, δ) such that:

* Q is a finite set, the set of states;

* Σ is a finite set, called the input alphabet;

* Γ is a finite set, called the output alphabet;

* I is a subset of Q, the set of initial states;

* F is a subset of Q, the set of final states; and

* :math:`\delta \subseteq {Q}\times(\sum \cup \epsilon)\times(\tau \cup  \epsilon)\times Q` (where ε is the empty string) is the transition relation.

We can view (Q, δ) as a labeled directed graph, known as the transition graph of T: the set of vertices is Q, and :math:`(q,a,b,r) \in \delta` means that there is a labeled edge going from vertex ``q`` to vertex ``r``. We also say that ``a`` is the ``input label`` and ``b`` the ``output label`` of that edge.

.. Note::
         This definition of finite transducer is also called letter transducer (Roche and Schabes 1997); alternative definitions are possible, but can all be converted into transducers following this one.

Define the *extended transition relation* :math:`\delta*` as the smallest set such that,

* :math:`\delta \subseteq \delta*`

* :math:`(q,\epsilon,\epsilon,q) \in \delta* \forall q \in Q`

* whenever :math:`(q,x,y,r) \in \delta* and (r,a,b,s) \in \delta then (q,xa,yb,s) \in \delta*`.

The extended transition relation is essentially the reflexive transitive closure of the transition graph that has been augmented to take edge labels into account. The elements of :math:`\delta*` are known as paths. The edge labels of a path are obtained by concatenating the edge labels of its constituent transitions in order.

The behavior of the transducer T is the rational relation [T] defined as follows: x[T]y if and only if there exists :math:`i \in I` and :math:`f \in F` such that 
:math:`(i,x,y,f) \in \delta*`. This is to say that T tranduces a string :math:`x \in \sum*` into a string :math:`y \in \tau*` if there exists a path from an initial state to a final state whose input label is x and whose output label is y.

*Weighted Automata*
-------------------
Finite State Transducers can be weighted, where each transition is labelled with a weight in addition to the input and output labels. A Weighted Finite State Transducer (WFST) over a set K of weights can be defined similarly to an unweighted one as an 8-tuple T=(Q, Σ, Γ, I, F, E, λ, ρ), where:

* :math:`Q,\sum,\tau,I,F` are defined as above

* :math:`E \subseteq Q \times (\sum \cup \epsilon) \times (\tau \cup \epsilon) \times Q \times K` (where :math:`\epsilon` is the empty string) is the finite set of transitions;

* :math:`\lambda:I \mapsto K` maps initial states of weights; 

* :math:`\rho:F \mapsto K` maps finite states to weights.

In order to make certain operations on WFSTs well-defined, it is convenient to require the set of weights to form a semiring. Two typical semirings used in practice are the log semiring and tropical semiring: nondeterministic automata may be regarded as having weights in the Boolean semiring.
