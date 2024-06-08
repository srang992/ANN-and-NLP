*Part of Speech(PoS) Tagging*
=============================
Tagging is a kind of classification that may be defined as the automatic assignment of description to the tokens. Here the descriptor is called tag, which may represent one of the part-of-speech, semantic information and so on.

Now, if we talk about Part-of-Speech (PoS) tagging, then it may be defined as the process of assigning one of the parts of speech to the given word. It is generally called POS tagging. In simple words, we can say that POS tagging is a task of labelling each word in a sentence with its appropriate part of speech. We already know that parts of speech include nouns, verb, adverbs, adjectives, pronouns, conjunction and their sub-categories.

Most of the POS tagging falls under Rule Base POS tagging, Stochastic POS tagging and Transformation based tagging.

*Stochastic POS Tagging*
************************
Another technique of tagging is Stochastic POS Tagging. Now, the question that arises here is which model can be stochastic. The model that includes frequency or probability (statistics) can be called stochastic. Any number of different approaches to the problem of part-of-speech tagging can be referred to as stochastic tagger.

The simplest stochastic tagger applies the following approaches for POS tagging −

* *Word Frequency Approach*

In this approach, the stochastic taggers disambiguate the words based on the probability that a word occurs with a particular tag. We can also say that the tag encountered most frequently with the word in the training set is the one assigned to an ambiguous instance of that word. The main issue with this approach is that it may yield inadmissible sequence of tags.

* *Tag Sequence Probabilities*

It is another approach of stochastic tagging, where the tagger calculates the probability of a given sequence of tags occurring. It is also called n-gram approach. It is called so because the best tag for a given word is determined by the probability at which it occurs with the n previous tags.

*Properties of Stochastic POST Tagging*
***************************************
Stochastic POS taggers possess the following properties −

* This POS tagging is based on the probability of tag occurring.

* It requires training corpus

* There would be no probability for the words that do not exist in the corpus.

* It uses different testing corpus (other than training corpus).

* It is the simplest POS tagging because it chooses most frequent tags associated with a word in training corpus.

*Hidden Markov Model*
*********************
An HMM model may be defined as the doubly-embedded stochastic model, where the underlying stochastic process is hidden. This hidden stochastic process can only be observed through another set of stochastic processes that produces the sequence of observations.

**Example**

For example, a sequence of hidden coin tossing experiments is done and we see only the observation sequence consisting of heads and tails. The actual details of the process - how many coins used, the order in which they are selected - are hidden from us. By observing this sequence of heads and tails, we can build several HMMs to explain the sequence. Following is one form of Hidden Markov Model for this problem −

.. figure:: ../images/hidden_markov_model.jpg
        :align: center

We assumed that there are two states in the HMM and each of the state corresponds to the selection of different biased coin. Following matrix gives the state transition probabilities −

.. math::

         A=\begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix}

Here,

* :math:`a_{ij}` = probability of transition from one state to another from i to j.

* :math:`a_{11} + a_{12}` = 1 and :math:`a_{21} + a_{22}` =1

* :math:`P_{1}` = probability of heads of the first coin i.e. the bias of the first coin.

* :math:`P_{2}` = probability of heads of the second coin i.e. the bias of the second coin.

We can also create an HMM model assuming that there are 3 coins or more.

This way, we can characterize HMM by the following elements −

* N, the number of states in the model (in the above example N =2, only two states).

* M, the number of distinct observations that can appear with each state in the above example M = 2, i.e., H or T).

* A, the state transition probability distribution − the matrix A in the above example.

* P, the probability distribution of the observable symbols in each state (in our example P1 and P2).

* I, the initial state distribution.

*Use of HMM for POS Tagging*
****************************
The POS tagging process is the process of finding the sequence of tags which is most likely to have generated a given word sequence. We can model this POS process by using a Hidden Markov Model (HMM), where **tags** are the **hidden states** that produced the **observable output**, i.e., the **words**.

Mathematically, in POS tagging, we are always interested in finding a tag sequence (C) which maximizes −

**P(C|W)**

Where,

C = :math:`C_{1}, C_{2}, C_{3}... C_{T}`

W = :math:`W_{1}, W_{2}, W_{3}, W_{T}`

On the other side of coin, the fact is that we need a lot of statistical data to reasonably estimate such kind of sequences. However, to simplify the problem, we can apply some mathematical transformations along with some assumptions.

The use of HMM to do a POS tagging is a special case of Bayesian interference. Hence, we will start by restating the problem using Bayes’ rule, which says that the above-mentioned conditional probability is equal to −

.. math::

        \frac{P(C_{1},..., C_{T}) \times P(W_{1},..., W_{T} | C_{1},..., C_{T})}{P(W1,..., WT)}

We can eliminate the denominator in all these cases because we are interested in finding the sequence C which maximizes the above value. This will not affect our answer. Now, our problem reduces to finding the sequence C that maximizes −

.. math::

        P(C_{1},..., C_{T})\times P(W_{1},..., W_{T} | C_{1},..., C_{T})  \;\text{(1)}

Even after reducing the problem in the above expression, it would require large amount of data. We can make reasonable independence assumptions about the two probabilities in the above expression to overcome the problem.

*First Assumption*
******************
The probability of a tag depends on the previous one (bigram model) or previous two (trigram model) or previous n tags (n-gram model) which, mathematically, can be explained as follows −

.. math::

         P(C_{1},..., C_{T}) = Π_{i=1..T} P(C_{i}|C_{i-n+1}…C_{i-1})  &&\text{(n-gram model)}\\~\\

         P(C_{1},..., C_{T}) = Π_{i=1..T} P(C_{i}|C_{i-1})  &&\text{(bi-gram model)}

The beginning of a sentence can be accounted for by assuming an initial probability for each tag.

.. math::

        P(C_{1}|C_{0}) = P_{initial} (C_{1})

*Second Assumption*
*******************
The second probability in equation (1) above can be approximated by assuming that a word appears in a category independent of the words in the preceding or succeeding categories which can be explained mathematically as follows −

.. math::

        P(W_{1},..., W_{T} | C_{1},..., C_{T}) = Π_{i=1..T} P(W_{i}|C_{i})

Now, on the basis of the above two assumptions, our goal reduces to finding a sequence C which maximizes

.. math::

        Π_{i=1...T} P(C_{i}|C_{i-1})\times P(W_{i}|C_{i})

Now the question that arises here is has converting the problem to the above form really helped us. The answer is - yes, it has. If we have a large tagged corpus, then the two probabilities in the above formula can be calculated as −

.. math::

        P(C_{i=VERB}|C_{i-1=NOUN}) = \frac{\text{(# of instances where Verb follows Noun)}}{\text{(# of instances where Noun appears)}}  &&\text{(2)}\\~\\

        P(W_{i}|C_{i}) = \frac{\text{(# of instances where Wi appears in Ci)}}{\text{(# of instances where Ci appears)}}  &&\text{(3)}
