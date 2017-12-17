---
layout: post
title: Coin Flipping Simulation
---


# Simulating Coin Flips
---
When teaching anyone about probability, one of the most accessible and obvious examples of a random event is a coin flip.  I created a coin flipping simulation to show how the short-run and long-run behavior differs and forms the basis of the concept of probability.  The definition of probability according to the Annotated Teacher's Editio: The Practice of Statistics textbook is
```
The probability of any outcome of a chance process is a number between 0 and 1 that describes the proportion of times the outcome wuld occur in a very long series of repetitions (Tabor, 2014).
```

Using the example of a coin flip, I will create several simulations in Python to show differences between short-run and long-run probability.


```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
plt.rcParams['figure.figsize'] = 12, 8
```


```python
np.random.seed(123)

all_probs = []

for j in range(5):
    heads_prob = []
    heads_total = 0.0
    
    for i in range(1,11):
        flip = np.random.randint(0,2)
        
        if flip == 0:
            heads_total +=1.0
            
        heads_prob.append(heads_total / float(i))
        
    plt.plot(heads_prob, label = j + 1)
    
    all_probs.append(heads_prob)
    

plt.show()

#all_probs_t = np.transpose(np.array(all_probs))
#print(all_probs_t)
#plt.plot(all_probs_t)
#plt.show()
```


![png](output_2_0.png)

