*Finite State Automata*
=======================
The term automata, derived from the Greek word "αὐτόματα" meaning "self-acting", is the plural of automaton which may be defined as an abstract self-propelled computing device that follows a predetermined sequence of operations automatically.

An automaton having a finite number of states is called a Finite Automaton (FA) or Finite State automata (FSA).

Mathematically, an automaton can be represented by a 5-tuple (Q, Σ, δ, q0, F), where −

* Q is a finite set of states.

* Σ is a finite set of symbols, called the alphabet of the automaton.

* δ is the transition function

* q0 is the initial state from where any input is processed (q0 ∈ Q).

* F is a set of final state/states of Q (F ⊆ Q).

*Relation between Finite Automata, Regular Grammars and Regular Expressions*
****************************************************************************
Following points will give us a clear view about the relationship between finite automata, regular grammars and regular expressions −

* As we know that finite state automata are the theoretical foundation of computational work and regular expressions is one way of describing them.

* We can say that any regular expression can be implemented as FSA and any FSA can be described with a regular expression.

* On the other hand, regular expression is a way to characterize a kind of language called regular language. Hence, we can say that regular language can be described with the help of both FSA and regular expression.

* Regular grammar, a formal grammar that can be right-regular or left-regular, is another way to characterize regular language.

Following diagram shows that finite automata, regular expressions and regular grammars are the equivalent ways of describing regular languages.

.. figure:: ../images/regular_grammars.jpg
        :align: center

*Types of Finite State Automation (FSA)*
****************************************
Finite state automation is of two types. Let us see what the types are.

*Deterministic Finite automation (DFA)*
****************************************
It may be defined as the type of finite automation wherein, for every input symbol we can determine the state to which the machine will move. It has a finite number of states that is why the machine is called Deterministic Finite Automaton (DFA).

Mathematically, a DFA can be represented by a 5-tuple (Q, Σ, δ, q0, F), where −

* Q is a finite set of states.

* Σ is a finite set of symbols, called the alphabet of the automaton.

* δ is the transition function where δ: Q × Σ → Q .

* q0 is the initial state from where any input is processed (q0 ∈ Q).

* F is a set of final state/states of Q (F ⊆ Q).

Whereas graphically, a DFA can be represented by diagraphs called state diagrams where −

* The states are represented by vertices.

* The transitions are shown by labeled arcs.

* The initial state is represented by an empty incoming arc.

* The final state is represented by double circle.

* **Example of DFA**

	Suppose a DFA be

* Q = {a, b, c},

* Σ = {0, 1},

* q0 = {a},

* F = {c},

* Transition function δ is shown in the table as follows −

         +----------------+----------------------+-----------------------+
         |Current State   |Next State for Input 0|Next State for Input 1 |
         +================+======================+=======================+
         |A               |a                     |B                      |
         +----------------+----------------------+-----------------------+
         |B               |b                     |A                      |
         +----------------+----------------------+-----------------------+
         |C               |c                     |C                      |
         +----------------+----------------------+-----------------------+

The graphical representation of this DFA would be as follows −

.. figure:: ../images/graphical_representation.jpg
        :align: center

*Non-deterministic Finite Automation (NDFA)*
********************************************
It may be defined as the type of finite automation where for every input symbol we cannot determine the state to which the machine will move i.e. the machine can move to any combination of the states. It has a finite number of states that is why the machine is called Non-deterministic Finite Automation (NDFA).

Mathematically, NDFA can be represented by a 5-tuple (Q, Σ, δ, q0, F), where −

* Q is a finite set of states.

* Σ is a finite set of symbols, called the alphabet of the automaton.

* δ :-is the transition function where δ: Q × Σ → 2 Q.

* q0 :-is the initial state from where any input is processed (q0 ∈ Q).

* F :-is a set of final state/states of Q (F ⊆ Q).

Whereas graphically (same as DFA), a NDFA can be represented by diagraphs called state diagrams where −

* The states are represented by vertices.

* The transitions are shown by labeled arcs.

* The initial state is represented by an empty incoming arc.

* The final state is represented by double circle.

* **Example of NDFA**

Suppose a NDFA be

* Q = {a, b, c},

* Σ = {0, 1},

* q0 = {a},

* F = {c},

* Transition function δ is shown in the table as follows −

         +----------------+----------------------+-----------------------+
         |Current State   |Next State for Input 0|Next State for Input 1 |
         +================+======================+=======================+
         |A               |a,b                   |B                      |
         +----------------+----------------------+-----------------------+
         |B               |C                     |a,c                    |
         +----------------+----------------------+-----------------------+
         |C               |b,c                   |C                      |
         +----------------+----------------------+-----------------------+

The graphical representation of this NDFA would be as follows −

.. figure:: ../images/graphical_represent.jpg
        :align: center


