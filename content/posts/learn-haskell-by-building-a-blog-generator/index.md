---
title: 'Learn Haskell by Building a Blog Generator'
date: '2026-10-30T06:00:00-04:00'
draft: false
tags: [haskell, book-review]
---

[*Learn Haskell by Building a Blog Generator*](https://learn-haskell.blog/) is a
free online book that teaches Haskell through a single project, a small static
blog generator. It's short, around 150 pages if you export it to PDF, and that's
a big part of its appeal. I read it during a week when my laptop was in the
shop, as a bounded, finishable side project to fill the gap while my main
Haskell books (*The Haskell Book* and *Haskell by Example*) were on hold.

Instead of teaching concepts in a neat progression and then applying them, the
book introduces Haskell features only when the project needs them. You build an
HTML printer library, design a small custom markup language and a parser for it,
glue the two together into a working converter, and then add error handling and
support for multiple files, pass configuration through an environment, and
finish up with tests and generated documentation. The HTML side is built as a
small embedded domain-specific language (EDSL), and it's really pleasant to use.
Along the way the book makes some smart, practical design points, like keeping
implementation details in an `Html.Internal` module while exposing a clean
public API with an explicit export list, and using `newtype` to keep raw strings
and HTML from getting mixed up.

What worked best is that you end up with a real, working tool instead of a pile
of toy exercises, and that makes the concepts stick in a way pure explanation
doesn't. Records, recursion, `Either` for error handling, and passing an
environment through a program all show up because the project needs them, so
their purpose is obvious. Threading configuration through the program was my
first hands-on look at the Reader pattern and monad transformers, well before my
other books covered them in depth. The testing chapter uses `hspec` with
automatic test discovery, which was nice to work with, and it left me with a
much better impression of Haskell testing than the cruder harness in another
book I was reading at the time. It also takes a worthwhile detour into
`optparse-applicative` instead of hand-rolling argument parsing.

The later chapters thin out, though. The testing chapter only tests one module
and leaves the rest as optional practice, and the documentation chapter is
brief, so both feel like they were written in more of a hurry than the core
project chapters. At least one example didn't compile as written either, since
the Reader chapter needed an `mtl` import the text never mentions, which is easy
to fix but is the kind of thing that stalls a beginner. The generator also reads
its own simple markup language instead of Markdown. For a tutorial this short,
that's the practical choice, since writing a full Markdown parser would swallow
the book, but it does limit how useful the finished tool is. And I read it in a
three-day binge, which it's short enough to allow, but I'd recommend spreading
it out so the material has time to sink in.

I wouldn't replace Hugo with the generator. It lacks the stuff you take for
granted in a mature static site generator, like nice themes and extensions, and
all my existing posts are written in Markdown instead of its custom markup, so
porting them over would be a pain. That's not really the point, though. The
point is learning Haskell by building something real, and the book does that
well.

Overall it's a short, practical, and enjoyable introduction to building a real
program in Haskell. Its biggest strength is that every concept shows up attached
to a reason to use it, and its weaknesses are mostly at the end, where testing
and documentation get thinner treatment, plus the occasional example that
doesn't compile as written. It works best alongside a more thorough book that
explains the theory the project leans on.

Full [book notes](https://github.com/llcawthorne/book-notes/blob/main/haskell/blog-generator/book-notes.md).
