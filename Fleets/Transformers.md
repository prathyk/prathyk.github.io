# One-Hot Encoding
Take a vector of 'n' dimensions where 'n' is the size of the vocabulary. Turn on a bit to represent a word in the vocabulary. 

![[Pasted image 20240301154139.png]]

## Dot Product
Dot product produces a scalar by multiplying two vectors pair-wise and adding them up. 

* Dot Product of two one-hot words is 1 only if they are the same word

## Matrix Multiplication

Dot Product is the fundamental operation which makes matrix multiplication possible. 
![[Pasted image 20240301155421.png]]

* If each row in 'A' is a word and each column in 'B' represents the relative weights, then the multiplication represents various combinations. 
* If 'A' is a list of words and 'B' is a transpose of list of qualities, in the multiplication, each row gives overall summation of all qualities for that row
* In this case another perspective is to see that 'A' defines the address of what to lookup in 'B'

## First order sequence model

For the below Markov chain model (first order, which takes only one preceding word to predict the next word)...
![[Pasted image 20240301161009.png]]

the following matrix multiplication shows how we can lookup for words after 'my'
![[Pasted image 20240301161110.png]]

The following is a transition matrix using Markov's second order chain to predict next word given two prior words for the sentences:

- _Check whether the battery ran down please._
- _Check whether the program ran please._

![[Pasted image 20240301161430.png]]

## Second order Markov chain with skips

To predict what comes after 'ran' we need to look back 8 words:
- _Check the program log and find out whether it ran please._
- _Check the battery log and find out whether it ran down please._

We can create a transition matrix of second order by considering, for each word all its preceding words one at a time...

![[Pasted image 20240301162401.png]]

From the above diagram can we find out what comes after 'ran'? Now we need to lookup multiple rows with where the recent word is 'ran' and that 'ran' is preceded by some other ealier word in the sentence. Now for those rows add up all the votes. Select that word which has the highest votes. 

Now if you apply masking to filter out everything except 'battery, ran' and 'program, ran' rows, then you have a matrix which gives very confident answer. 

## Essential idea of Attention
If the most recent word is 'ran', we can predict the next word if we know the difference between 'battery, ran' and 'program, ran'. 'ran' is one word with specific spelling but it is polymorphic because it take multiple meanings according to the context. How can we find out which 'ran' is being referred here. 

The context obviously should depend on the previous words that already occurred in the input because the current task is to predict next word (given the previous words). Attention is a Neural network model which tries to learn this complex relationships between 'next' word and recent word and prior words. 

# What makes transformers tick?

1. Computers (GPUs) are optimized for fast matrix multiplication
2. Each step in the architecture can use gradient descent. 
3. The science of neural networks is creating building blocks which are differentiable but the art of it is to compose them in such a way that gradient descent does not change too quickly and is roughly the same magnitude in every direction. 

## Attention equation as a matrix multiplication
![[Pasted image 20240302150339.png]]
'Q' represents the feature to lookup. 'K' is a set of all masks possible. QK^T is lookup to find relevant mask for this feature. Remember, how we used a mask to filter out only 'program, ran' and 'battery, ran' from list of all possible bi-grams. 

How do we create the features matrix? It is easy to build a neural network which can predict co-occurrence of words in sentences. It can be single-word, two-word or n-word features. 
![[Pasted image 20240302151304.png]]

If all words in the sentence are inputs, then you can easily 'm' outputs to discover 'm' features each of which can be a combination of any number of words. How do we optimize this to find the best of features? We optimize this with a cost function which predicts the next word. 

### Pieces of Attention - till now
Up until now we used three constructs:
1. A `Q` vector which represents the query or feature of interest. It is one-hot encoding of the recent word in the simplest case. The most recent word plays a major role in predicting the next word. 
2. A `K` matrix which is list of all masks. Learned via a neural net. We use `Q` to lookup the most relevant mask which helps filter noise when we lookup the transition table
3. A transition matrix which can be used to find the next word. 
