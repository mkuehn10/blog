---
layout: post
title: Coin Flipping Simulation
---
When teaching anyone about probability, one of the most accessible and obvious examples of a random event is a coin flip.  I created a coin flipping simulation to show how the short-run and long-run behavior differs and forms the basis of the concept of probability.  The definition of probability according to the Annotated Teacher's Editio: The Practice of Statistics textbook is

>The probability of any outcome of a chance process is a number between 0 and 1 that describes the proportion of times the outcome wuld occur in a very long series of repetitions (Tabor, 2014).


Using the example of a coin flip, I will create several simulations in Python to show differences between short-run and long-run probability.


```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
plt.rcParams['figure.figsize'] = 12, 8
```


```python
def coin_flip_simulation(simulations = 5, trials = 10):
    final_probabilities = []
    for i in range(simulations):
        heads_probabilities = []
        
        number_of_heads_total = 0.0
        
        for j in range(1, trials + 1):
            if np.random.randint(0, 2) == 0:
                number_of_heads_total += 1.0
                
            heads_probabilities.append(number_of_heads_total / float(j))
        
        plt.plot(heads_probabilities)
        final_probabilities.append(heads_probabilities[-1])
        
    plt.title(str(simulations) + ' Runs of ' + str(trials) + ' Coin Flips')    
    plt.show()
    print('Largest probability after ' + str(trials) + ' flips: ' + str(max(final_probabilities)))
    print('Smallest probability after ' + str(trials) + ' flips: ' + str(min(final_probabilities)))
    print('Median probability after ' + str(trials) + ' flips: ' + str(np.median(final_probabilities)))
    
np.random.seed(123)

coin_flip_simulation()
```


![_config.yml]({{ site.baseurl }}/images/coinflip1.png)


    Largest probability after 10 flips: 0.7
    Smallest probability after 10 flips: 0.4
    Median probability after 10 flips: 0.6


The preceding code creates a function that runs 5 total simulations of flipping a coin 10 times.  The function keeps a running probability of the number of heads after each coin flip.  The plot shows how the running probability total varies over the 5 simulations and 10 coin flips in each simulation.  In the short-run of only flipping the coin 10 times, a wide array of probabilities result (from 0.4 to 0.7).  This shows that probability in the short-run has much more variability than the long-run probability.

The following is the result of conducting the same simulation using more coin flips per simulation.


```python
coin_flip_simulation(trials = 100)
```


![_config.yml]({{ site.baseurl }}/images/coinflip2.png)


    Largest probability after 100 flips: 0.5
    Smallest probability after 100 flips: 0.42
    Median probability after 100 flips: 0.47
