---
layout: post
title: "Practical Vim, 2nd Edition - First Half"
date: 2017-05-22
tags: vim
---

Practical Vim is an excellent resource for tips and trick for using vim.
It focuses on core vim features, and doesn't spend any room talking about
plugins.  Aside from a few hints to how .vimrc settings might affect certain
commands, it doesn't spend any time telling you what to put in your .vimrc.
It does have an appendix about vimrc settings, in case you need some new ones.
The book is laid out as a series of 123 mostly standalone tips, although
they do follow a procession of least to most difficult within their
respective section.  The tips are split between 20 sections.  The book
doesn't attempt to go into Vimscript.  Overall, I found it a useful collection
of mostly non-obvious tips for using vim, and I feel like it has made me
more capable in using my editor of choice.

The author recommends skipping around rather than reading the book from
beginning to end, however, I still found the book quite readable.  The
tips vary in difficulty from very basic (Ex: Tip 47 is "Keep Your Fingers
on the Home Row" and covers h, j, k, and l) to fairly advanced (Ex:
Edit the Contents of a Macro).  I really enjoy the way the author doesn't
repeat any content readily available in the manual.  In the electronic copy,
he links any manual references to a website with the vim manual.  For people
reading along, he provides the proper keyword to use with :h in order to
lookup the topic via vim help.  This allows him to not spend a lot of time
on prerequisite info and get directly to useful tips.

Some tidbits that I've found useful so far are the keystrokes that he mentions
being available in Insert mode.  I never paid attention to the fact that you
can use <C-w> to delete back one word without leaving insert mode,
<C-r>{register} to quickly paste the contents of a register, and
<C-v>u{1234} to insert unicode character #1234, all without leaving insert
mode.  In both the previous examples, the selection in curly brackets is
replaced with just a register or just a four digit number, the curly brackets
are not typed literally.
I generally like hitting my keys one at a time while in vim, but
those are a couple of useful chords to use in insert mode.  I'm not sure
I'll use the unicode one often enough to remember it, but the other two
are pretty easy to remember and of general use.  There is no tip like
"Here are some keystrokes for Insert mode." but the author instead worked
providing these keystrokes into the explanation of how to do something.
The <C-r>{register} keystroke was provided in the "Paste from a Register
Without Leaving Insert Mode" tip which focused on it and <C-v>u{1234}
was from the "Insert Unusual Characters by Character Code" tip, but
the <C-w> keystroke was provided in the more general "Make Corrections
Instantly from Insert Mode" tip.

I learned a lot that I didn't know before in the section on Command-Line Mode.
As the author puts it, "Ex commands strike far and wide."  I was unaware of
how the range worked with ex commands and of the variety of ex commands
available.  There are commands to delete, yank, put, copy, move, join,
normal (execute Normal mode commands on a specified or range of lines),
substitute, and global (execute and ex command where a pattern matches).
I've used substitute a decent bit, but never remember knowing about the
others and how you can make them all work flexibly with a range without
having to move the cursor there first.  It's especially convenient that
you can use V to switch into visual line mode and select some lines, then
it will prepopulate the range of lines into your : for executing an Ex
command.  You can also use % to target the whole file with a command,
which is how I'm accustomed to working with substitute.  As an example,
`:%normal A;` will append a semicolon to every line in a file or
`%normal i//` will comment out every line in a file given a language
where `//` starts comments.  You can even write a script of Ex commands
and load it into vim with `:source {filename}`.

I also learned that in you can use `:edit %:h` to load the working directory
of the currently active buffer as a parameter to edit, and then tab complete
it to the name of another file in the same directory.  The book recommends
you alias `%%` to `%:h` since this is so handy.  That remap made it into my
vimrc.  You can even open a file in a nonexistant directory and then use
`:!mkdir -p %:h` to create the directory so you can save the file.

The only obvious problem I had with some of the content is that some of it
(like the EX commands) is too vim specific to work with vim emulators.
Anymore, I spend a lot more time using IdeaVIM in IntelliJ than I clock with
real vim, but that's largely a personal problem.  The author doesn't avoid
forward references, which is only a problem if you're trying to read the
book through rather than skip around as recommended.  Also, the author
sometimes punts further explanation to
[VimCasts](http://www.vimcasts.org/).  VimCasts is an excellent resource,
and the author of this book is the man behind the site, but I like having
explanations in the book I bought rather than having to look to outside
video for them.  In his defense, he only does it for some of the more
graphical tasks like splitting windows and such.  Also, around midway
through the book when it gets to motion keys, it feels like backtracking
to such simple topics to have a Tip 47 that covers h, j, k, and l keys
and keeping your hands on home row.  This leads to a number of other
rather simplistic motion tips that are not new to anyone that's used
vim very long.  Fortunately these are all kept to one chapter, Chapter 8.
The fact that these complaints are all pretty nitpicky goes to show
that overall, I didn't find many problems with this book.

In general, I especially enjoy how the author explains his thinking behind
the use of
certain commands.  He'll sometimes show how to do something in multiple
ways that use the same number of keystrokes, and then explain why one way
better fits the general vim mindset (which often means its better for
re-use via the . command).  He does a lot of this early on in the book,
but the tips later in the book he tends to show the one way to perform.

I'm only halfway through the book now, but this post is getting long
enough.  I'll go ahead and post what I've written about the first half
of the book, and add another post later if I find some awesome tips
worth mentioning in the latter half of this book.
