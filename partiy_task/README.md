Parity task Generator

What is parity task?\
A parity bit, or check bit, is a bit added to a string of binary code to ensure that the total number of 1-bits in the string is even or odd [Wikipedia](https://en.wikipedia.org/wiki/Parity_bit)

40-bit parity task dataset used in [Mollifying Networks](https://openreview.net/forum?id=r1G4z8cge)

```
def parity_batch(input_length, batch_size):
    xs = [np.random.randint(0, 2, input_length) for _ in range(batch_size)]
    xs.append(np.ones(shape=input_length, dtype=int))
    ys = [[0] if np.sum(x) % 2 == 0 else [1] for x in xs]
    return xs, ys
```

```
import numpy as np
np.random.seed(seed=config.seed)
d_dim = config.parity_length
X, y = parity_batch(config.parity_length, 2000)
X_val, y_val = parity_batch(config.parity_length, 500)
```