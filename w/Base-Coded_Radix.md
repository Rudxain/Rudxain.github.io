# Base-Coded Radix
BCR is a family of radix-to-numeral encodings (such as [BTTs](https://en.wikipedia.org/wiki/Binary-to-text_encoding)) for positional numeral systems. The most well-known members being [BCD](https://en.wikipedia.org/wiki/Binary-coded_decimal) and [BCT](https://en.wikipedia.org/wiki/Ternary_numeral_system#Binary-coded_ternary).

These encodings make it possible to efficiently operate on radix `N` raw data and numeric values, while sacrificing "minimal" memory (especially the "packed" variants).

## Equivalence
Binary-coded-octal is just binary segmented in fixed-size triplets of bits, for the same reason ternary-coded-nonary is just ternary in pairs of trits: It's all about [powers](https://en.wikipedia.org/wiki/Exponentiation).

This implies **modern computers use binary-coded-base0x100**, because the [smallest addressable unit](https://en.wikipedia.org/wiki/Byte) is an _octet of bits_
