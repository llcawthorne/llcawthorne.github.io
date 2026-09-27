---
title: 'Kotlin from Scratch'
date: '2026-09-26T21:00:00-04:00'
draft: false
tags: [kotlin, book-review]
---

![Kotlin from Scratch cover](images/cover.jpg)

Brief summary: math/computational projects (Euclid, Sieve, Fibonacci, physics
sims, fractals, sorting, A*), no extension functions, limited language features
in intro chapters, good for drilling `val` instincts. Not idiomatic Kotlin.

Good typing practice and some genuinely interesting math/algorithms, but
disappointing as a source of good Kotlin code. Chapters 1-2 covered language
fundamentals in almost as much depth as all of *Head First Kotlin*, but that depth
never returned. Nothing past chapter 2 touches generics, sealed classes,
delegation, or coroutines. Chapter 3 was a whole detour into JavaFX I didn't ask
for and won't need for Android/Swift, though I don't regret typing it (the
Stage/Scene boilerplate turned into a genuinely cool spiral, and the Gradle
multi-module setup fights taught me more about the build system than the book
itself did).

The author's code quality was the real letdown. He leans on mutable `var`s and,
worse, global mutable state constantly, the genetic algorithm chapter had
`tournament()` calls with zero parameters that still returned different results
every time because they were secretly reaching into global population state plus
randomness. No referential transparency, no way to reason about a call site
without reading the function body. Comments were often pure noise too (`// Run the genetic algorithm`
above `runGA()`). Project 16 was missing an entire function (confirmed later in
ERRATA, not my mistake), so I pulled that one from the GitHub companion repo
instead of fighting a broken example.

The `fold`/`map` chapter was a similar letdown in a different way, it only
reached for the classic textbook trio (sum a list, calculate a product,
concatenate strings), nothing that actually shows off what the tool is for. I
ended up chewing on a much better example on my own: finding all subsets of a
set (the power set), which I worked out mostly by instinct (accumulate subsets
so far, and for each new element, union in every existing subset with that
element added) before ever hitting `fold` as the idiomatic way to express it.
Even where the book _does_ introduce a genuinely powerful construct, it plays it
safe with examples that don't demonstrate the range. One thing the book did get
right, worth noting since it's easy to assume otherwise coming from Java: its
package-naming guidance ("join multiple words or use camelCase") checks out
against the official Kotlin coding conventions, which explicitly allow both.

Skipped typing the Modeling/Simulation and Fractals chapters (more JavaFX, more
of the same mutable-state pattern) and skimmed them from GitHub instead.
Sorting/searching (chapter 7) was the cleanest code in the book, fewer `var`s,
properly scoped rather than global, though in-place sorting algorithms are
supposed to mutate so that's not really a knock.

Genetic algorithms (ch. 8) and particle swarm/ant colony (ch. 9) were the
highlight, typed three GA variants (toy problem, knapsack, multivariate equation
solving via the "weasel program" Shakespeare quote demo) by hand, then took the
GitHub shortcut for PSO and the TSP ant simulation once I'd already internalized
the pattern. PSO actually beat the GA on the Eggholder problem, fewer
generations, found a solution GA never did in multiple runs, didn't get stuck in
the same local optimum GA kept falling into.

Bottom line: worth the read for the algorithms and the typing reps, not for the
Kotlin. Wouldn't recommend it as a "here's good idiomatic Kotlin" reference.

Full [book notes](https://github.com/llcawthorne/book-notes/blob/main/kotlin/kotlin-from-scratch/book-notes.md).
