- class definition

```python
class Blah:
     def __init__(self, x):
         self.val = x
         self.something = None
         self.something_else = None
```

- [enumerate](https://docs.python.org/2/library/functions.html#enumerate)

```python
for i, x in collection:
  element = collection[i]
  x == element # returns true
```

- deep copy

```python
import copy

copy.deepcopy(thing)
```

- sets: create using `set()`, use `frozenset`s if you want immutable sets (useful if you want sets of sets because sets cannot contain mutable objects)
- random string stuff: `lower()`, `isalnum()`, `len()` etc
- sorting tuples: `merged = sorted(some_collection_of_tuples, key = lambda x: x[0])`
- dictionaries: `dict.get(key, default_value)` -> returns `default_value` if `key not in dict`
- this `*` thing:
     - say `m = [[1, 2], [3, 4], [5, 6]]`. Then `zip(*m)` is equivalent to `zip([1, 2], [3, 4], [5, 6])` so `*` allows us to specify multiple arguments (lists) as one (list of lists).
     
     ```python
     >>> zip([1, 2], [3, 4], [5, 6])
     [(1, 3, 5), (2, 4, 6)]
     ```
- reversing a list: either do `list(reversed(the_list))` or `the_list[::-1]`
     - traversing a reversed range: `for i in reversed(range(10)) # 9, 8, ..., 0`

**infinity**

```
positive_inf = float("inf")
negative_inf = float("-inf")

# can be compared to other numbers (ints, floats, doubles)
```

**collections (ordered dict, deques) | (docs)[https://docs.python.org/2/library/collections.html]*
