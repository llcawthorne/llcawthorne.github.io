---
title: 'Go Language Opinions'
date: '2026-09-12T18:00:00-04:00'
draft: false
tags: [go, opinions]
---

Go's tooling is what stuck with me the most. gofmt is flawless, even on case
statements, no matter how hard I try to trick it, it always formats the file
correctly. Cross-compilation with GOOS/GOARCH is excellent, shipping a
single self-contained binary is genuinely nice to hand off, and the command
line tooling is great too. I like that the implementation stays transparent
instead of hiding behind framework magic, and I prefer simple structs with
methods over deep inheritance hierarchies. *Head First Go* gave me real
confidence with the language, and *Powerful Command-Line Applications in Go*
taught me a lot about building command-line apps, even in languages other
than Go, like how easy it is to write a markdown previewer when the standard
library gives you so much for free, and to always check out a new language's
argument-parsing frameworks early. Even `//` comments felt natural to me.

Some of it is more neutral than a selling point. I appreciate Go's minimalism
as a deliberate design choice even though it isn't really my target use case.
Google's involvement makes me a little cautious. Binary size and startup time
don't matter much for what I build, and skipping a GC isn't a selling point
when I'm not doing systems programming.

I'm moving on from Go for now. Kotlin is more professionally applicable to
me, and it works as a better Java without leaving the JVM. Real app
development projects in Kotlin and Swift give me concrete motivation that Go
doesn't, and honestly my language list just needed trimming.

I might come back to it, though. *Distributed Systems in Go* looks like the
most transparent way to see microservice patterns without Spring hiding the
mechanics, and *Learn Go with Tests* looks good for picking up TDD patterns.
The books will still be there, and Go isn't going anywhere.

After trying ktlint in Kotlin, I'm even more impressed with how reliable and
fast gofmt is. It's a benefit of working with such a simple language. ktlint
flags errors well but regularly gets stymied and unable to fix the file, so I
have to either fix it manually or ignore the error. Formatting is more
consistent in IntelliJ though, which is the main place I do Kotlin work. This
is just something that bugs me when I type in book code in Vim, and Kotlin
book code isn't even formatted to ktlint's specs either, whereas Go code
everywhere looks pretty much the same. I still have to deal with Go's odd
capitalization rules for function names, but at least everything else looks
reliably good.
