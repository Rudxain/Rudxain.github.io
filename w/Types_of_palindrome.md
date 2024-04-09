# Types of palindrome
> [!note]
> For the entirety of this article, "[palindrome](https://en.wikipedia.org/wiki/Palindrome)" will be referred to as "P" for short

For this article, we'll be using the generalized definition of P, where we refer to items/elements rather than characters.

## Anti
Anti-P is a string that when reversed, its normalized (relative) [HD](https://en.wikipedia.org/wiki/Hamming_distance) is `1` with respect to the original string. Example: "abcd" => "dcba". Another (more algorithmically efficient) definition, is that every element is different entry-wise.

Algorithm in Rust and Typescript, respectively:
```rust
use core::iter::zip;

fn anti_p<T: Eq>(ls: &[T]) -> bool {
    zip(ls, ls.iter().rev()).all(|(v, r)| v != r)
}
```

```ts
const anti_p = <T,>(ls: T[]) =>
    ls.every((v, i) => v !== ls[ls.length - 1 - i])
```

## Co
Co-P (AKA "mutually-palindromic pair"), is a pair of strings that become P when concatenated, and are said to be "copalindromic". Note that each _aren't necessarily_ P independently.

Algorithm in TS:
```ts
// this is unnecessary in Rust & Python
/** shallow equality */
const eq = <T,>(a: T[], b: T[]) =>
    a.every((v, i) => v === b[i])

const is_p = <T,>(ls: T[]) => eq(ls, ls.toReversed())

// notice that only 1 of 2 possible concats is checked
const co_p = <T,>(a: T[], b: T[]) => is_p(a.concat(b))
```

There are 2 sub-types, explained below...

### Isometric Co-P
Is a pair where each string has the same length. Example: "abcd" & "dcba" become "abcddcba" or "dcbaabcd", which are both Ps, so the original pair is SCP.

> I'm unsure if it's possible to construct an ICP where only 1 of the 2 possible concats is P. This is an open question, can you prove/disprove it?

### Anisometric Co-P
Is a pair where each string has different lengths. Example: "abc" & "ddcba" become "abcddcba" or "ddcbaabc", such that only the former is P, therefore the original pair is ACP.

Note that it's possible for an ACP to have both concats be P: "0" + "00" => "000" (regardless of order). This is a trivial case.

> I'm unsure if it's possible to construct a non-trivial ACP, where both possible concats (distinct or not) is P. This is an open question, can you prove/disprove it? What about the added requirement that both _concats must be distinct_?
