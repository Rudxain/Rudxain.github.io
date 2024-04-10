# Types of palindrome
For the entirety of this article:
- "[Palindrome](https://en.wikipedia.org/wiki/Palindrome)" will be referred to as "P" for short.
- We'll be using the generalized definition of P, where we refer to items/elements rather than characters.
- "str" := "string", an ordered list of items (**not just chars**).
- `+` is the concatenation operator.
- When reading TypeScript source code, assume the following [prelude](https://doc.rust-lang.org/reference/names/preludes.html#language-prelude) "header":
```ts
// this already exists in Rust & Python
/** shallow equality */
const eq = <T,>(a: T[], b: T[]) =>
	a.every((v, i) => v === b[i])

const is_p = <T,>(ls: T[]) =>
	eq(ls, ls.toReversed())
```

## Anti
Anti-P is a str that when reversed, its normalized (relative) [HD](https://en.wikipedia.org/wiki/Hamming_distance) is `1` with respect to the original str. Example: "abcd" => "dcba". Another (more algorithmically efficient) definition, is that every entry-wise pair must be different.

Algorithm in Rust and TS, respectively:
```rust
use core::iter::zip;

fn anti_p<T: Eq>(ls: &[T]) -> bool {
	zip(ls, ls.iter().rev())
	.all(|(v, r)| v != r)
}
```
```ts
const anti_p = <T,>(ls: T[]) =>
	ls.every((v, i) => v !== ls[ls.length - 1 - i])
```

## Co
Co-P (AKA "mutually-palindromic pair"), is a pair of strs that become P when concatenated _in some arbitrary way_, and are said to be "copalindromic". Note that each _aren't necessarily_ P independently.

If A and B are co-P, then it can be safely assumed that they are at least *weakly co-P:*
```ts
const ord_co_p = <T,>(a: T[], b: T[]) =>
	is_p(a.concat(b))

const weak_co_p = <T,>(a: T[], b: T[]) =>
	ord_co_p(a, b) || ord_co_p(b, a)
```

### Ord Co-P
Ordinal co-p. These are order-specific:
```ts
/** both orders */
const biord_co_p = <T,>(a: T[], b: T[]) =>
	ord_co_p(a, b) && ord_co_p(b, a)

/** only 1 specific order */
const monord_co_p = <T,>(a: T[], b: T[]) =>
	ord_co_p(a, b) && !ord_co_p(b, a)

/** any exclusive order */
const xord_co_p = <T,>(a: T[], b: T[]) =>
	ord_co_p(a, b) != ord_co_p(b, a)
```

### Strong Co-P
A pair of Ps that are also _bi-ordinal_ co-P:
```ts
const strong_co_p = <T,>(a: T[], b: T[]) =>
	is_p(a) && is_p(b) && biord_co_p(a, b)
```

### Isometric Co-P
Is a pair where each str has the same length. Example: "abcd" & "dcba" become "abcddcba" or "dcbaabcd", which are both Ps, so the original pair is SCP.

### Anisometric Co-P
Is a pair where each string has different lengths. Example: "abc" & "ddcba" become "abcddcba" or "ddcbaabc", such that only the former is P, therefore the original pair is ACP.

Note that it's possible for an ACP to have both concats be P: "0" + "00" => "000" (regardless of order). This is a trivial case.

## Sub
A sub-P is a str which contains at least 1 substring of length>1 that is P. The substring must be a `slice`, that is, each item must be adjacent (no gaps). Strs of len<=1 are never sub, by definition.

Every P is also a **strong sub-P**, because every P can be sliced in such a way that the result is also P, so SSP doesn't deserve its own category.

### Full sub
A fully sub-P has **all of its possible slices** being P.

## Permut
A str which has at least 1 permutation that is P.

### Full permut
A str where **all permutations** are P.

## Open questions
- Is it possible to construct an [ICP](#isometric-co-p) where only 1 of the 2 possible concats is P?
- Is it possible to construct a non-trivial [ACP](#anisometric-co-p), where both possible concats (distinct or not) is P. What about the added requirement that both _concats must be distinct_?
