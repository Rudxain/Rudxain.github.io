# Absolute ratio
Defined as the [quotient](https://en.wikipedia.org/wiki/Quotient) between the maximum and minimum [absolute-values](https://en.wikipedia.org/wiki/Absolute_value) of both input arguments.

## Applications
It can be used to guarantee that integer division is always greater than 0, which "preserves" the information of the operands.

## Implementation
[PFP](https://en.wikipedia.org/wiki/Pure_functional_programming)-style code in Python:
```py
from typing import Final, Callable
# there's `TypeVar` but `//` forces us to `def` 2 APIs

fabs_ratio: Final[Callable[[float, float], float]] = lambda x, y, /: (
	lambda x, y: max(x, y) / min(x, y)
)(abs(x), abs(y))

iabs_ratio: Final[Callable[[int, int], int]] = lambda x, y, /: (
	lambda x, y: max(x, y) // min(x, y)
)(abs(x), abs(y))
```
