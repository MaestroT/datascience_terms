# Information Entropy

## What Is Information Theory?

[Information theory](https://en.wikipedia.org/wiki/Information_theory) is a field of study concerned with quantifying information for communication.

It is a subfield of mathematics and is concerned with topics like data compression and the limits of signal processing.

A foundational concept from information is the quantification of the amount of information in things like events, random variables, and distributions.

Quantifying the amount of information requires the use of probabilities, hence the relationship of information theory to probability.

## Calculate the Information for an Event

Quantifying information is the foundation of the field of information theory.

The intuition behind quantifying information is the idea of measuring how much surprise there is in an event. Those events that are rare (low probability) are more surprising and therefore have more information than those events that are common (high probability).

* **Low Probability Event** : High Information ( *surprising* ).
* **High Probability Event** : Low Information ( *unsurprising* ).

We can calculate the amount of information there is in an event using the probability of the event. This is called “ *Shannon information* ,” “ *self-information* ,” or simply the “ *information* ,” and can be calculated for a discrete event *x* as follows:

* information(x) = -log( p(x) )

Where *log()* is the base-2 logarithm and *p(x)* is the probability of the event  *x* .

The choice of the base-2 logarithm means that the units of the information measure is in bits (binary digits). This can be directly interpreted in the information processing sense as the number of bits required to represent the event.

The calculation of information is often written as  *h()* ; for example:

* h(x) = -log( p(x) )

The negative sign ensures that the result is always positive or zero.

## Calculate the Entropy for a Random Variable

We can also quantify how much information there is in a random variable.

For example, if we wanted to calculate the information for a random variable *X* with probability distribution  *p* , this might be written as a function  *H()* ; for example:

* H(X)

In effect, calculating the information for a random variable is the same as calculating the information for the probability distribution of the events for the random variable.

Entropy can be calculated for a random variable *X* with *k* in *K* discrete states as follows:

* H(X) = -sum(each k in K p(k) * log(p(k)))

That is the negative of the sum of the probability of each event multiplied by the log of the probability of each event.
