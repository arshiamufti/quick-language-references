i should add to this

## A bunch of bit stuff I should have remembered but /shrug whatever

(recap: one byte = 8 bits = 2 nibbles)

32 bits = one word of memory for 32-bit systems

```bash
0000 0000 0000 0000 0000 0000 0000 0000
^ MSB                                 ^ LSB
```

* [Bitwise operations](https://en.wikipedia.org/wiki/Bitwise_operation)
  * `>>` is arithmethic left shift. The result of `a >> b` is everything in `a` shifted left by `b` places -- equivalent to multiplying by 2^n (assuming no overflow). So `1 >> 2 = 0000 0001 >> 2 = 0000 0100 (4)`
* [Operators in C, C++](https://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B)

