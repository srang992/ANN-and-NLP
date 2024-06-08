*Automata – What is it?*
========================
The term "Automata" is derived from the Greek word "αὐτόματα" which means "self-acting". An automaton (Automata in plural) is an abstract self-propelled computing device which follows a predetermined sequence of operations automatically.

An automaton with a finite number of states is called a Finite Automaton (FA) or Finite State Machine (FSM).

*Formal definition of a Finite Automaton*
--------------------------------------------
An automaton can be represented by a 5-tuple (Q, ∑, δ, q0, F), where −

* Q is a finite set of states.

* ∑ is a finite set of symbols, called the alphabet of the automaton.

* δ is the transition function.

* q0 is the initial state from where any input is processed (q0 ∈ Q).

* F is a set of final state/states of Q (F ⊆ Q).

*Related Terminologies*
^^^^^^^^^^^^^^^^^^^^^^^^
1. **Alphabet**

* *Definition* − An alphabet is any finite set of symbols.

* *Example*  − ∑ = {a, b, c, d} is an alphabet set where ‘a’, ‘b’, ‘c’, and ‘d’ are symbols.

2. **String**

* *Definition* − A string is a finite sequence of symbols taken from ∑.

* *Example*  − ‘cabcad’ is a valid string on the alphabet set ∑ = {a, b, c, d}

3. **Length of a String**

* *Definition* − It is the number of symbols present in a string. (Denoted by |S|).

* *Examples* −

If S = ‘cabcad’, |S|= 6

If |S|= 0, it is called an empty string (Denoted by λ or ε)

4. **Kleene Star**

* *Definition* − The Kleene star, ∑*, is a unary operator on a set of symbols or strings, ∑, that gives the infinite set of all possible strings of all possible lengths over ∑ including λ.

* *Representation* − ∑* = ∑0 ∪ ∑1 ∪ ∑2 ∪……. where ∑p is the set of all possible strings of length p.

* *Example* − If ∑ = {a, b}, ∑* = {λ, a, b, aa, ab, ba, bb,………..}

5. **Kleene Closure / Plus**

* *Definition* − The set ∑+ is the infinite set of all possible strings of all possible lengths over ∑ excluding λ.

* *Representation* − ∑+ = ∑1 ∪ ∑2 ∪ ∑3 ∪...

                      ∑+ = ∑* − { λ }

Example − If ∑ = { a, b } , ∑+ = { a, b, aa, ab, ba, bb,...}

6. **Language**

* *Definition* − A language is a subset of ∑* for some alphabet ∑. It can be finite or infinite.

* *Example* − If the language takes all possible strings of length 2 over ∑ = {a, b}, then L = { ab, aa, ba, bb }
