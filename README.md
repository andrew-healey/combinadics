# combinadics-fast

This package encodes and decodes the [Macaulay representation](https://en.wikipedia.org/wiki/Macaulay_representation_of_an_integer) of a k-combination.

It is useful for selecting distinct samples from a population.

## Install

```sh
pip install combinadics-fast
```

## Demo

```py
import math,random
from combinadics_fast import int_to_mac

population = ["Andrew","Alexys","Kaylie","Jamel","Hertha","Verna","Eli","Charles","Palma"]

# choose ten distinct samples from the population
sample_size = 5
num_samples = 10

num_possible_samples = math.comb(len(population),sample_size)

sample_hashes = random.sample(range(num_possible_samples),num_samples)

samples = []

for sample_hash in sample_hashes:
  name_indices = int_to_mac(sample_hash,sample_size)
  sample = [population[idx] for idx in name_indices]
  samples.append(sample)

print(samples)
# [
#   ['Andrew', 'Alexys', 'Kaylie', 'Jamel', 'Hertha'],
#   ['Alexys', 'Jamel', 'Verna', 'Charles', 'Palma'],
#   ['Andrew', 'Alexys', 'Hertha', 'Verna', 'Eli'],
#   ['Andrew', 'Alexys', 'Jamel', 'Hertha', 'Verna'], 
#   ['Jamel', 'Hertha', 'Eli', 'Charles', 'Palma'], 
#   ['Alexys', 'Jamel', 'Hertha', 'Verna', 'Palma'], 
#   ['Andrew', 'Kaylie', 'Jamel', 'Verna', 'Palma'], 
#   ['Alexys', 'Kaylie', 'Verna', 'Eli', 'Charles'], 
#   ['Kaylie', 'Jamel', 'Verna', 'Charles', 'Palma'], 
#   ['Andrew', 'Kaylie', 'Verna', 'Eli', 'Charles']
# ]

```
