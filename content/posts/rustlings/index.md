---
title: "Rustlings"
date: '2026-11-20T06:00:00-05:00'
draft: false
tags: [rust, tools, programming, book-review]
---

I worked through Rustlings as a companion to *The Rust Programming Language*
(TRPL), specifically the Brown University interactive version. TRPL is
notoriously theory-heavy and practice-light, and you can easily spend an hour
reading dense chapters on ownership, lifetimes, or trait bounds without writing
a single line of standalone code. Rustlings exists to bridge that specific gap.
It's a 94-exercise compiler-driven drill where you run the watcher in a
terminal, it fails on an exercise, and you edit the file until the compiler and
tests go green.

If you're reading TRPL or another conceptual text, it's a useful companion. It
serves roughly the same purpose as the comprehension quizzes in Brown's
interactive edition to keep you honest and prove you were actually paying
attention to the chapter you just finished. But if you're learning Rust through
a project-oriented book like *Command-Line Rust* or *100 Exercises to Learn
Rust*, it's largely unnecessary, since the early sections on variables,
primitive types, functions, and if statements are completely trivial and you'll
already be doing much heavier lifting in real projects.

Where Rustlings genuinely earned its keep was in the later sections,
particularly the conversion exercises. TRPL barely touches `From` and `Into`,
which is a notable omission for beginners, and Rustlings forces you to implement
`From`, `FromStr`, `TryFrom`, `TryInto`, `AsRef`, and `AsMut`. You quickly see
how standard library conventions click together, like how implementing
`FromStr` unlocks `.parse::<YourType>()` everywhere for free, and implementing
`From` on error types unlocks clean `?` operator propagation without nested
match pyramids. It also highlights subtle differences that books often gloss
over, like how `as` integer casting silently truncates high bits while
`.try_into()` uses the type system to catch out-of-range values and return a
`Result`, or how multi-arm macros require semicolons rather than commas between
arms, and how `collect()` infers the destination container purely from return
type annotations.

The tooling itself is completely frictionless. The watcher compiles on save,
advances automatically when tests pass, and it's a nice touch that the solutions
stay empty until after you solve the problem yourself. Most exercises take
thirty seconds, and the few that took longer weren't conceptually difficult so
much as exercises in getting used to Rust's strictness, like learning when slice
destructuring binds an element as `&&str` instead of `&str` and balancing
references until the compiler is happy. It's not going to teach you software
architecture or how to structure large crates, but as a quick drill to build
syntactic muscle memory and get comfortable reading `rustc` diagnostics
alongside TRPL, it does its job well.

Full [book notes](https://github.com/llcawthorne/book-notes/blob/main/rust/rustlings/book-notes.md).

