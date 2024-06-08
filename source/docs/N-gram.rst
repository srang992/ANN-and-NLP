*An Introduction to N-gram*
============================
In this part we are going to learn about N-grams, a concept found in Natural Language Processing ( aka NLP). First of all, let’s see what the term ‘N-gram’ means. Turns out that is the simplest bit, an N-gram is simply a sequence of N words. For instance, let us take a look at the following examples.

1. San Francisco (is a 2-gram)
2. The Three Musketeers (is a 3-gram)
3. She stood up slowly (is a 4-gram)

Now which of these three N-grams have you seen quite frequently? Probably, **“San Francisco”** and **“The Three Musketeers”**. On the other hand, you might not have seen **“She stood up slowly”** that frequently. Basically, **“She stood up slowly”** is an example of an N-gram that does not occur as often in sentences as Examples 1 and 2.

Now if we assign a probability to the occurrence of an N-gram or the probability of a word occurring next in a sequence of words, it can be very useful. Why?

First of all, it can help in deciding which N-grams can be chunked together to form single entities (like **“San Francisco”** chunked together as one word, **“high school”** being chunked as one word).

It can also help make next word predictions. Say you have the partial sentence ``“Please hand over your”``. Then it is more likely that the next word is going to be ``“test”`` or ``“assignment”`` or ``“paper”`` than the next word being ``“school”``.

It can also help to make spelling error corrections. For instance, the sentence ``“drink cofee”`` could be corrected to ``“drink coffee”`` if you knew that the word ``“coffee”`` had a high probability of occurrence after the word ``“drink”`` and also the overlap of letters between ``“cofee”`` and ``“coffee”`` is high.
As you can see, assigning these probabilities has a huge potential in the NLP domain.

Now that we understand this concept, we can build with it: that’s the N-gram model. Basically, an N-gram model predicts the occurrence of a word based on the occurrence of its N – 1 previous words. So here we are answering the question – how far back in the history of a sequence of words should we go to predict the next word? For instance, a bigram model (N = 2) predicts the occurrence of a word given only its previous word (as N – 1 = 1 in this case). Similarly, a trigram model (N = 3) predicts the occurrence of a word based on its previous two words (as N – 1 = 2 in this case).

Let us see a way to assign a probability to a word occurring next in a sequence of words. First of all, we need a very large sample of English sentences (called a corpus).

For the purpose of our example, we’ll consider a very small sample of sentences, but in reality, a corpus will be extremely large. Say our corpus contains the following sentences:

* He said thank you.

* He said bye as he walked through the door.

* He went to San Diego.

* San Diego has nice weather.

* It is raining in San Francisco.

Let’s assume a bigram model. So we are going to find the probability of a word based only on its previous word. In general, we can say that this probability is (the number of times the previous word ‘wp’ occurs before the word ‘wn’) / (the total number of times the previous word ‘wp’ occurs in the corpus) =

 **(Count (wp wn))/(Count (wp))**

Let’s work this out with an example.
To find the probability of the word “you” following the word “thank”, we can write this as P (you | thank) which is a conditional probability.
This becomes equal to:

**=(No. of times “Thank You” occurs) / (No. of times “Thank” occurs)** 
**= 1/1** 
**= 1**

We can say with certainty that whenever “Thank” occurs, it will be followed by “You” (This is because we have trained on a set of only five sentences and “Thank” occurred only once in the context of “Thank You”). Let’s see an example of a case when the preceding word occurs in different contexts.

Let’s calculate the probability of the word “Diego” coming after “San”. We want to find the P (Diego | San). This means that we are trying to find the probability that the next word will be “Diego” given the word “San”. We can do this by:

**=(No of times “San Diego” occurs) / (No. of times “San” occurs)** 
**= 2/3** 
**= 0.67**

This is because in our corpus, one of the three preceding “San”s was followed by “Francisco”. So, the ``P (Francisco | San) = 1 / 3``.
In our corpus, only “Diego” and “Francisco” occur after “San” with the probabilities 2 / 3 and 1 / 3 respectively. So if we want to create a next word prediction software based on our corpus, and a user types in “San”, we will give two options: “Diego” ranked most likely and “Francisco” ranked less likely.

Generally, the bigram model works well and it may not be necessary to use trigram models or higher N-gram models.


