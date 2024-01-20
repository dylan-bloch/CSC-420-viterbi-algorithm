# CSC-420-viterbi-algorithm
This repository is the final project for my Artificial Intelligence class. 

This explains what the Viterbi Algorithm is as well as how it operates. We go over the math behind the algorithm and then there is a sample data set with Viterbi implemented.  

## What is the Viterbi Algorithm? 
The Viterbi algorithm is a dynamic programming algorithm that allows us to compute the most probable path or the most likely sequence of hidden states that results in a sequnce of observed events.

The Viterbi Algorithm is a more efficint method of solving similar problems that can be solved using a Hidden Markov Model. 
Hidden Markov Models are used to compute the most likely sequence of unobservable states that result in the observed state we see. The unobservable states are called hidden states.

In a Hidden Markov Model there are transition probabilities which are the probabilities of a hidden state based on another hidden state. 
Each hidden state then has an affect on the observed state and the probabilitty of observing an observed state given a hidden state is called the emission probability.

The Hidden Markov Model should seem brute force. Inefficient is another word. 
The Viterbi algorithm is what solves the Hidden Markov Model's straightforwardness and makes that process more efficient.

## Ultimate Question to be Answered 

A patient visits three days in a row, and the doctor discovers that the patient feels normal on the first day, cold on the second day, and dizzy on the third day.

The doctor has a question: what is the most likely sequence of health conditions of the patient that would explain these observations? This can be answered by the Viterbi algorithm.

Explanation of Code

The function viterbi takes the following arguments:

obs is the sequence of observations,['normal', 'cold', 'dizzy']
states is the set of hidden states, ['healthy', 'fever']
start_p is the start probability
trans_p are the transition probabilities
emit_p are the emission probabilities.
'V' is a list that will store Viterbi values. It starts with an empty dictionary in the list to store the values at time step 0.

Then for each 'st' in the 'states' list the algorithm computes the initial Viterbi value for that state at time step 0.

This value is calculated as the product of the initial state probability and the emission probability for the first observation. ((start_p[st]) * (emit_p[st][obs[0]])).

Then we run the Viterbi algorithm for the remaining time steps.

Inside the loop for the time steps the algorithm appends an empty dictionary to the 'V' list for the current time step.

For each state 'st' at time step 't' the algorithm calculates the maximum transition probability from the previous time step. 'max_tr_prob' is initialized with the first state in the 'states' list.
It then iterates over the other states and updates 'max_tr_prob' if a higher transition probability is found.

Then we get to the dptable function who's main goal is to print a table of the Viterbi values. It prints a header with the time step indices then prints the probabilities that correlate with each time step.

The last thing the code is going to do is print the most likely sequence of states and its associated maximum probability.
