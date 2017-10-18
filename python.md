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
