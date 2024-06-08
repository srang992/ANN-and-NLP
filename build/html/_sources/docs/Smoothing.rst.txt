*Smoothing*
===========
Smoothing techniques in NLP are used to address scenarios related to determining probability / likelihood estimate of a sequence of words (say, a sentence) occuring together when one or more words individually (unigram) or N-grams such as bigram :math:`(\frac{w_{i}}{w_{i-1}})` or trigram :math:`(\frac{w_{i}}{w_{i-1}w_{i-2}})` in the given set have never occured in the past.

Here, we will go through a quick introduction to various different smoothing techniques used in NLP in addition to related formulas and examples. The following is the list of some of the smoothing techniques:

1. **Laplace smoothing: Another name for Laplace smoothing technique is add one smoothing.**

2. **Additive smoothing**

3. **Good-turing smoothing**

4. **Kneser-Ney smoothing**

5. **Katz smoothing**

6. **Church and Gale Smoothing**

*Why Smoothing Techniques?*
***************************
Based on the training data set, what is the probability of “cats sleep” assuming bigram technique is used? Based on bigram technique, the probability of the sequence of words “cats sleep” can be calculated as the product of following:

:math:`P(cats sleep) = P(\frac{cats}{<s>})\times P(\frac{sleep}{cats})\times P(\frac{</s>}{sleep})`

you will notice that :math:`P(\frac{sleep}{cats}) = 0`. Thus, the overall probability of occurrence of “cats sleep” would result in zero (0) value. However, the probability of occurrence of a sequence of words should not be zero at all.

This is where various different smoothing techniques come into the picture.

*Laplace(Add-One-Smoothing)*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
In Laplace smoothing, 1 (one) is added to all the counts and thereafter, the probability is calculated. This is one of the most trivial smoothing techniques out of all the techniques.

Maximum likelihood estimate (MLE) of a word :math:`w_{i}` occuring in a corpus can be calculated as the following. N is total number of words, and :math:`count(w_{i})` is count of words for whose probability is required to be calculated.

**MLE**: :math:`P(w_{i}) = \frac{count(w_{i})}{N}`

After applying Laplace smoothing, the following happens. Adding 1 leads to extra V observations.

**MLE**: :math:`P_{Laplace}(w_{i}) = \frac{count(w_{i}) + 1}{N + V}`

Similarly, for N-grams (say, Bigram), MLE is calculated as the following:

:math:`P(\frac{w_{i}}{w_{i-1}}) = \frac{count(w_{i-1}, w_{i})}{count(w_{i-1})}`

After applying Laplace smoothing, the following happens for N-grams (Bigram). Adding 1 leads to extra V observations.

**MLE**: :math:`P_{Laplace}(\frac{w_{i}}{w_{i-1}}) = \frac{count(w_{i-1}, w_{i}) + 1}{count(w_{i-1}) + V}`

*Additive Smoothing*
^^^^^^^^^^^^^^^^^^^^
This is very similar to “Add One” or Laplace smoothing. Instead of adding 1 as like in Laplace smoothing, a delta(δ) value is added. Thus, the formula to calculate probability using additive smoothing looks like following:

:math:`P(\frac{w_{i}}{w_{i-1}}) = \frac{count(w_{i-1}, w_{i}) + \delta}{count(w_{i-1}) + \delta|V|}`

*Good-Turing Smoothing*
^^^^^^^^^^^^^^^^^^^^^^^
Good Turing Smoothing technique uses the frequencies of the count of occurrence of N-Grams for calculating the maximum likelihood estimate. For example, consider calculating the probability of a bigram (chatter/cats) from the corpus given above. Note that this bigram has never occurred in the corpus and thus, probability without smoothing would turn out to be zero. As per the Good-turing Smoothing, the probability will depend upon the following:

* In case, the bigram (chatter/cats) has never occurred in the corpus (which is the reality), the probability will depend upon the number of bigrams which occurred exactly one time and the total number of bigrams.

* In case, the bigram has occurred in the corpus (for example, chatter/rats), the probability will depend upon number of bigrams which occurred more than one time of the current bigram (chatter/rats) (the value is 1 for chase/cats), total number of bigram which occurred same time as the current bigram (to/bigram) and total number of bigram.

The following is the formula:

For the unknown N-grams, the following formula is used to calculate the probability:

:math:`P_{unknown}(\frac{w_{i}}{w_{i-1}}) = \frac{N_1}{N}`

In above formula, N1 is count of N-grams which appeared one time and N is count of total number of N-grams

For the known N-grams, the following formula is used to calculate the probability:

:math:`P(\frac{w_{i}}{w_{i-1}}) = \frac{c*}{N}`

where 

.. math::

        c*=(c + 1)\times\frac{N_{i+1}}{N_{c}}

In the above formula, c represents the count of occurrence of n-gram, :math:`N_{c+1}` represents count of n-grams which occured for c + 1 times, :math:`N_{c}`represents count of n-grams which occured for c times and N represents total count of all n-grams.

*Kneser-Ney Smoothing*
^^^^^^^^^^^^^^^^^^^^^^
In Good Turing smoothing, it is observed that the count of n-grams is discounted by a constant/abolute value such as 0.75. The same intuiton is applied for Kneser-Ney Smoothing where absolute discounting is applied to the count of n-grams in addition to adding the product of interpolation weight and probability of word to appear as novel continuation.

:math:`P_{Kneser-Ney}(\frac{w_{i}}{w_{i-1}}) = \frac{max(c(w_{i-1},w_{i} – d, 0))}{c(w_{i-1})} + \lambda(w_{i-1})*P_{continuation}(w_{i})`

where λ is a normalizing constant which represents probability mass that have been discounted for higher order. The following represents how λ is calculated:

.. math::
        
        \lambda(w_{i-1}) = \frac{d\times|c(w_{i-1},w_{i})|}{c(w_{i-1})}

*Katz Smoothing*
^^^^^^^^^^^^^^^^
Good-turing technique is combined with interpolation. Outperforms Good-Turing by redistributing different probabilities to different unseen units.

*Church and Gale Smoothing*
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Good-turing technique is combined with bucketing.

* Each n-gram is assigned to one of serveral buckets based on its frequency predicted from lower-order models.

* Good-turing estimate is calculated for each bucket.

