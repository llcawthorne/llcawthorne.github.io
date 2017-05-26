---
layout: post
title: "Practical Vim, 2nd Edition - Second Half"
date: 2017-05-22
tags: vim
---

So, I promised I'ld mention what goodies I find in the second half of
Practical Vim, 2nd Edition.  Here they are.

## Chapter 10, Copy and Paste

First, the repetition of the insert mode `<C-r>{register}` command later
in the book was something I found useful.  I think that's a pretty handy
way to paste the contents of a register.
I never knew that `"+` let's you access the system clipboard
either.  If you put the two together, you can quickly paste from the system
clipboard without leaving insert mode with `<C-r>+`.  The fact that yank
stores a copy of what it copies in the `0` register is pretty handy too.
Nice to have an alternate way to access the last yank if I've clobbered it.

## Chapter 11, Macros

Most of the macros chapter was fairly new to me.  I knew the basics of how to
record and playback macros, and have used them before when in native vim and
not using an emulator.  But I've never given macros intense thought or tried
to be terribly clever with them.  He goes into the idea of crafting resilient
reusable macros in some depth in the tips focused on them and covers a handful
of macro best practices.  As he puts it, "The golden rule is this: when
recording a macro, ensure that every command is repeatable."

The author sums up macro advice with the phrase "Normalize, Strike, Abort"
The first question to ask when crafting a macro is, "where am I, where
have I come
from, and where am I going."  Make sure the cursor is positioned so the
next command does as expected where expected.  You shouldn't use the
mouse when recording a macro, so make sure to take advantage of the full
range of available motion commands to maneuver to the right location to
strike.  If a motion fails while a macro is executing, Vim will abort the
rest of the macro.  This is a feature!  You don't want to execute your
command when you aren't in the right location.  Motions can act as a simple
test as to whether or not the macro should be executed.  Remember that
search is a motion too.  You can do a lot with a macro that uses the `n`
key to go to the next search item and perform an action.  Once no matches
remain, `n` will fail and the macro will stop.

Tip 67 points out how a simple two key macro can be useful to move and perform
the dot command multiple times.  You can't repeat with dot, and if you could
the number would either repeat the move multiple times or repeat the dot
multiple times in the same place, so a simple macro of a movement command
and dot is a clever trick tie a move and repeat together and replay it
multiple times.  Again, you can count on the motion failing at the end if
you choose the right motion, so you don't have to worry about the exact
count.  The example is as follows:

> {start}
> x = "("+a+","+b+","+c+","+d+","+e+")";

And we want to change it to:

> {goal}
> x = "(" + a + "," + b + "," + c + "," + d + "," + e + ")";

And it can be achieved with the following keystrokes:

1. `f+`
1. `s + <Esc>`
1. `qq;.q`
1. `22@q`

That's much simpler than adding the spaces around the + marks by hand.
Since the `f+` movement will fail after we are out of +'s, it is safe
to run the macro 22 times.  The author admits to being lazy like this
often.  22 is his go to repeat number, since 2 is the same key as
@ to run the macro.  That's a great example of making use of "Abort".

Appending keystrokes to macros works just like appending yanks to registers.
`qA` will append commands on the end of the macro in register a.  That's a
small but handy tip for getting more from macros.  The next tip covers how
to apply a macro to a series of files, either with `:argdo normal @a` or by
manually advancing with `:next` to act across the argument list.  The example
he uses is a pretty handy one of wrapping several classes in a module
declaration and adding proper indentation.  The next tip seems handy, but I
doubt it's general enough use for me to remember it.  It covers how to prepend
an incrementing line count to multiple lines.  The final tip of the chapter
covers the fact that you can put a macro from a register, then edit the
macro text, then yank the macro back to the register.  An interesting option
for editing macros!  One note is to be careful to use a character-wise
yank like `"ay$"`, or else you might get an extra <CR> at the end of
your macro.

## Chapter 12 - Matching Patterns and Literals

First off, I learned the handy tidbit that using `\c` in a search pattern
causes it to ignore case, and `\C` to be case sensitive, regardless of
`ignorecase` settings.  You can put them anywhere in the pattern, including
just tacking them on the end.  I like the default `smartcase` where if you
include an uppercase letter it is case sensitive, otherwise not.

The `\v` switch anywhere in a regex makes it "very magic", or more like what
you might be used to from Perl, Python, or Ruby.  It makes all characters
assume a special meaning except for "_", letters, and numbers,
so you don't need to escape all your braces,
brackets, and parentheses.  It makes the difference between
`#\([0-9a-fA-F]\{6}\|[0-9a-fA-F]\{3}\)` and
`\v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})` to match CSS color codes, a regex
that can be made slightly even better using the `\x` hex class as
`\v#(\x{6}|\x{3})`.  The `\V` or `verynomagic` option makes a search
only search by the literal meaning of symbols provided, even `.`, `*`,
and `?`.  Only the `\` character has special meaning in a `verynomagic`
search.  So ultimately, both the `\v` and `\V` search options are
terribly useful and worth remembering.  A good example of the `\V` option
is searching for "a.k.a." with `/\Va.k.a.` instead of `/a\.k\.a\.`
I think the argument has won me over well enough to use `\v` most of
the time and `\V` on special occassions.

Another handy fact for regular expressions is that in `verymagic` search
mode, the `&lt;` and `>` keys match word boundaries.  So a search for
`\v<the>` will find all the "the" occurrences without any "their" or
"these" being matched.  It goes on to cover some ways to handle search
field terminators in the final tip of the chapter.

## Chapter 13 - Searching, 14 - Substitution, 15 - Global Commands

I didn't find anything in these to chapters particularly worthwhile, except
the fact that you can leave the search part of a substitute command blank
to use whatever the last successful search was as the pattern.  That
decouples findint the right search pattern from the overall substitute
command, and you normally want to search first anyway to make sure you
got your pattern right before making changes.   The search and replace
across a project tip was possibly useful.  Everything about the global
command was new to me and worth playing with.

## Chapter 16 - Index and Navigate Source Code with ctags

This  whole chapter is about ctags and was all new to me.  It looks like an
excellent way to get the ability to jump to definitions in vim.  Apparently
I've been living under a rock, since I was unaware of this feature.  This
looks like a key step into making Vim into a development environment instead
of just an editor.

## Chapter 17 - Compile Code and Navigate Errors with the Quickfix List

The quickfix and location lists seem handy, assuming you map navigating them
to something more convenient than typing `:cnext` and `:cprev`.  I'll have
to checkout the unimpaired plugin he mentions that makes the quicklist
navigable by `[q` and `]q`.  It has a number of other handy mappings, so it's
worth checking out instead of just putting the one set of mappings in my
vimrc.  I think I'll use the Tip 108 that has you make `:make` run JSLint
and populate the quickfix list with any linting errors.  I didn't fully 
understand how to do it from the tip, but this github project looks useful:
[vim-nodelist](https://github.com/bigfish/vim-nodelint).

## Chapter 18 - Search Project-Wide with grep, vimgrep, and Others

There's so many neat random things in this book.  Today I learned that there's
a version of grep optimized for programmers called ack.
[Ack](https://beyondgrep.com/).  To relate it back to vim, the book explains
how to make the vim `:grep` command use ack instead, but then tells you not
to, since there is an ack plugin for vim
[ack.vim](https://github.com/mileszs/ack.vim)
that will use it with the `:ack` command.

## Chapter 19 - Dial X for Autocompletion

There's plugins for better autocompletion than what's built in.  It looks like
you can complete based off ctags with `&lt;C-x>&lt;C-]>` or use 
`&lt;C-x>&lt;C-i>` to complete based off your imports in various languages.
Generic autocompletion is based off `&lt;C-n>` and is probably best of the
built-ins.  You use `&lt;C-n>` and `&lt;C-p` to choose next  or previous.

## Chapter 20 - Find and Fix Typos with Vim's Spell Checker

This one starts out simple, with how to use the built in spell checker.  First
think I learned is that `z=` on a misspelled word will bring up suggestions
and `[s` and `]s` let you jump between misspelled words.  I was able to try
those out successfully while writing this blog post.  `zg` adds a word to the
spell file, which worked great to add "blog".  Apparently, you can fix
misspelled words without leaving Insert mode with `&lt;C-x>s` to
enable autocomplete misspelled mode.  It will jump you back to the last
misspelled word and offer suggestions from the dictionary.  Pretty handy!

## Summary

Overall, I think I picked up more tips than I can reasonably integrate into
my workflow at once from my first reading of Practical Vim, Second Edition.
That's why I put a lot of them here on my blog, to remind me to try them
out.  I believe there's still enough that I didn't mention to make the book
worth another read, or at least a re-read several spots in it.  I highly
recommend it if you are already comfortable using Vim and want to pickup
tricks to take your Vim workflow to the next level.


