# Types of Turing completeness
[The definition of a TM](https://en.wikipedia.org/wiki/Turing_machine#Formal_definition) doesn't require looping or recursion, this is what I call _"weak" TC_. _"Self-propelling" TC_ are machines that do looping or recursion on their own, they don't need a force (external to the system) that repeatedly applies the transition function.

> [I coined the terms here](https://github.com/microsoft/TypeScript/issues/14833#issuecomment-2689599227)

It should be obvious that almost everything (including the universe itself) is (at least) weakly TC (see [this](https://beza1e1.tuxen.de/articles/accidentally_turing_complete.html) and [this](https://mattrickard.com/accidentally-turing-complete))

Many people misuse "TC" to refer to [BSM](https://esolangs.org/wiki/Bounded-storage_machine)s. A BSM is only a finite-memory approximation of a TM, so a BSM is only TC _in practice, not theory_. However, [there's merit](https://gavinhoward.com/2024/03/what-computers-cannot-do-the-consequences-of-turing-completeness/#mathematical-vs-practical) to this comparison.

# See also
[LBA](https://en.wikipedia.org/wiki/Linear_bounded_automaton)
