---
title: 'Grokking Simplicity'
date: '2026-10-16T06:00:00-04:00'
draft: false
tags: [functional-programming, book-review]
---

![Grokking Simplicity cover](images/cover.jpg)

*Grokking Simplicity* by Eric Normand teaches the difference between actions,
calculations, and data as a way to reason about mutation and side effects, and
it works better as a vocabulary book than a technique book. If you've already
internalized what `map`, `filter`, and `reduce` are for, and I mean really
internalized it and not just being able to write the syntax, most of the core
material is going to read as confirmation of things you already believe instead
of new information. The higher-order function chapters and the copy-on-write
chapters fall right into that bucket. They're clearly and patiently explained,
and useful for someone who's never had the difference between mutating and
copying spelled out, but they're slow going if you've been burned by shared
mutable state enough times to already distrust it on instinct.

The best material is outside that core. The architecture chapters cover both
stratified design and the onion model, and they were solid and worth having
read, though not so revelatory that I'm in a hurry to go through them again. The
concurrency chapters were the standout. They introduce a diagramming technique
for reasoning about timelines and ordering that I hadn't run into before and
thought was really creative, and it's a lot different from the usual "just use
locks or actors and hope" approach most books take. Those are the chapters I'd
go back to if a project involving concurrency comes up, since it's the kind of
technique you have to actually apply before it sticks.

The biggest miss for me was the immutable data chapters. I went in hoping for
advice on using immutable data structures in single-binding languages, the
discipline of writing code where a name, once bound, stays bound. What I got was
mostly copy-on-write technique, demonstrated with JavaScript objects that get
rebound on every update. That's a reasonable way to teach it in a language like
Elixir where rebinding is idiomatic, but it doesn't really carry over to the
habit I was actually after, which is reaching for `val` by default in Kotlin, or
treating a Haskell declaration as a one-time mathematical definition instead of
a variable that just happens not to change. The chapter shows you how to build
the immutable structure, but it doesn't really show you how to live in a
codebase that treats bindings as permanent.

Overall, it's a fast, well-explained, easy read that's clearly aimed at someone
running into these ideas for the first time. If that's not you, you'll skim more
than you expect, but the concurrency material deserves a second look, and the
architecture chapters were worth reading once, even if they weren't essential.
