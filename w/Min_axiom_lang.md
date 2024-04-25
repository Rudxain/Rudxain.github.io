# Reduced Axiom Language
A **Reduced Axiom Set Language** or **Minimal Axiom System Lang**, is a lang that's specified in terms of a minimal (not necessarily the absolute minimum) amount of simple axioms. Such langs tend to define most of their features as part of their core/standard libraries, rather than being opaque implementations embedded in the grammar.

Another definition is that these langs have an axiom-to-construct ratio very close to 0, implying they have many concepts derived from a small set of axioms.

## Examples
- [λ-C](https://en.wikipedia.org/wiki/Lambda_calculus). This is the "textbook definition" of a RASL. Nothing can beat it.
- [Hackett](https://github.com/lexi-lambda/hackett/blob/e90ace9e4a056ec0a2a267f220cb29b756cbefce/README.md?plain=1#L32)
- 🦀Rs: [Tris explains it better than me](https://github.com/0atman/noboilerplate/blob/main/scripts/32-rust-is-written-in-rust.md) ([video](https://youtu.be/v6RxJsk8otY))
- Gleam: [`Bool`](https://github.com/gleam-lang/gleam/discussions/1026#discussioncomment-598813)
- [Ada](https://github.com/Rudxain/Rudxain/blob/863b648fb846b2549309ec62161764f1ba4c4009/README.md?plain=1#L66-L73)
- [FlipJump](https://esolangs.org/wiki/FlipJump)

## Non-examples
- JavaScript/TypeScript and CoffeeScript. The lang is complex and its [std-lib](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects) is "anemic".
- Python
- Java (I guess?)
- [brainfuck](https://esolangs.org/wiki/brainfuck). Yes, it's a [tur-tar](https://en.wikipedia.org/wiki/Turing_tarpit), but it has many unnecessary operators.

## Criticism
The concept of RASL is fuzzy and context-sensitive, and thereby open to interpretation. Even I have no idea what it is 💀
