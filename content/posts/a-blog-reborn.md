---
title: 'A Blog Reborn'
date: '2026-08-04T17:07:11-04:00'
draft: false
tags: [blog, haskell, clojure, elixir, web-frameworks]
---

So, I haven't been blogging for about ten years. To tell the truth, I spent
all day programming, so when I got off work, I spent my time reading history
or philosophy or anything else not computer related. I can see from my
previous posts that I was experimenting with video and had started reading
Agile Web Development with Rails. Well, I'm still a full stack web developer,
so I could do worse than looking back at the web framework that really started
it all. So I will read Agile Web Development with Rails 8 and get a taste of
convention before configuration. That doesn't really fit with the new title
of the blog, but it's still something I want to do, so I will get it done.
I was interested in functional programming and different approaches to web
development 10 years ago, and have never fully explored either, so I'm picking
up where I left off with a slightly updated approach.

## Haskell

But let's talk about the new title. It is "Senior Software Engineer Learns
Functional Programming." One of the last things I did but never blogged about
was try to learn Haskell. I started with the venerable
[The Haskell Book](https://haskellbook.com/). I read a bit over half and
realized I still couldn't program much of anything in Haskell. This was after
spending previous effort learning functional programming. I learned some
Scala and the syntax of Clojure and felt ineffectual with both aside from
being able to use Scala as a better Java, so that's what led me to Haskell
to learn functional programming right. Well, I still want to do that. I didn't
think I wanted to really, but I spent some time reading *Advanced Functional
Programming with Elixir* and it made a perfectly good case for why Haskell is
a better programming language and featured a style that was not idiomatic
Elixir but instead very Haskell inspired, and it got me interested again. So
I'm not going to start over with The Haskell Book and try to re-learn
programming from first principles. Instead I am going to read
*Haskell by Example* which is more hands on and dip into the explanations of
*The Haskell Book* whenever I need more theory. I'm also about halfway
through [*Learn You a Haskell*](https://learnyouahaskell.github.io/) which
I started over vacation, since I'm finding my intuition for working with
linked lists has degraded.

## Elixir

The subtitle of the blog is "With explorations in
Haskell, Elixir, and Clojure". I've already read two Elixir books on the
basics of the language (reviews upcoming) and I have every intention of
spending more time with Elixir. The books I read didn't even touch on the cool
Actor model and OTP stuff that makes Elixir unique. It's not the best language
for learning to deal with immutable values since it allows you to rebind
variables, which feels a bit like cheating. Sure the data structure itself is
immutable, but you just end up pointing the same variable at the updated
copy. Haskell won't let you get away with that. I understand since the
variables aren't global and are local to the Actors working behind the scenes
it is safe even for concurrent code, but I intend to learn how to deal with
immutable data structures bound once to a name. So I will definitely spend
some time away with Haskell but eventually get back to Elixir. It overlaps
my other goal of trying web frameworks thanks to Phoenix, so my two big
projects ("Learn Functional Programming" and "Try Web Frameworks") actually
meet.

## Clojure

I have also bought the most recent edition of *Programming Clojure* and
*Clojure Brain Teasers* and plan to spend time with it again. I read
*Getting Clojure* and *Living Clojure* and *Clojure for the Brave and True*
years ago, and I felt pretty comfortable with the syntax of the languages and
all the parentheses, but I never was able to use it for much. So after I
spend some time writing code with Haskell, I'll spend some time with Clojure
again and see if I can do anything cool with it. I'm a Java developer by trade,
so its position on the JVM feels quite welcome, and once I learn idiomatic
functional coding in a language where I can't back off and call Java code,
maybe it will be accessible to me. I'll probably spend a while with Haskell
and then Elixir first though. I do want to play around with Ring to try
writing my webapps with a minimalist Clojure library.

## Web Frameworks

Back to the web frameworks though... I was going to dive into *Agile Web
Development with Rails 8* and try Ruby. Then I will read through *Django 5
by Example*. This builds up four sizable projects which I plan to steal.
I don't really like any dynamic language all that much, but I do normally
prefer Python to Ruby for its usefulness with AI and its sensible stance
on one way to do things and lack of going crazy with metaprogramming. I have
every intention of stealing the Django projects to reimplement in other
frameworks to serve my own curiosity. First in Rails, then move on to the next
stop. So then I can read *Programming Elixir* and *Programming Phoenix
Liveview* to try doing a web framework. How do I plan to make time for all this?
Well, I think I can wrestle with Haskell for at most 30-60 minutes a day, so
my time beyond that can be spent toying with web frameworks which requires
less cognitive load. After Phoenix, there's other options. I can try writing
a typed API in Haskell with Servant or do something with Yesod. I also wouldn't
mind reading *Distributed Services in Go* and trying the same projects as
microservices. I happen to like Go for being so simple that you can't hide
anything behind the language. I've recently read two books on it (reviews
forthcoming) and feel pretty comfortable with it. Aside from that, I wouldn't
mind trying an Angular frontend with a backend in another language, since we
actively use Angular in the new project at work. And I'm not opposed to trying
React to just see the difference. Obviously, all JavaScript Single-Page
Applications are more the rage now than old school web frameworks like Rails,
and it fits my interests of seeing different ways to do things. I also have
been toying around with Kotlin and would love an excuse to go back, so I would
like to try Spring with Kotlin for the big enterprise way of doing a web
framework along with Ktor for a lighter weight framework in the same language.
I could code Spring in Java, but I do like not coding in Java when I'm away
from work and find Kotlin a fun alternative. Spring and Angular are probably
the most professionally relevant interests that I'll be pursuing, but it's
obvious that I'm not trying to maximize for utility. I do really think it
very clever that the new project at work is leaning into a modern Angular UI
with a Java backend instead of using any of the trainwreck front end projects
available on the Java platform. JSF was bad enough to make me never want to
see a Java frontend again. Anyway, that's as far as I've thought
these two projects through, but if I make it that far with them, I'll have
a better idea of what I want to do next. Put together, they should keep me
busy for a while, and assuming I don't give up blogging for ten years or so
again, it will give me something to blog about.

## Why Now?

Why do I think blogging will catch on this time? Well, what made me give up
my side projects and blogging before was primarily being burnt out on spending
all day coding at work to get off and do more of it at night. Now that my kid
is older and I've got more time to focus on personal development, I figured
why not fire the blog back up so I can shout my book reviews and whatnot into
the void. Aside from that, work has us leaning a lot more on AI for writing
code these days, so it's as good an excuse as any to keep my own skills sharp
with some side projects. I've also been rather good lately at putting my mind
to stuff and keeping it going.
I lost about 40 pounds and run 10K every day I don't lift weights. So maybe
I can stay focused on something intellectual too. Also, I still run over an
hour most days a week, which gives me a great opportunity to listen to a
history audiobook or fictional work, so it isn't like I'm giving up my hobby
reading. I'm just cutting into other spare time with a new project. As a busy
dad, I really get 1-2 hours of free time that I'm not working out most days,
so it's easy to spend 30-60 minutes on Haskell and the remainder if there is
any on something else. Or so I think. We'll see if this blog rebirth lasts.
So far, I've read about 8 technical books that I'll end up posting reviews
for, so I already have more content than I had last time before
discontinuing it, and it seems something fun to do. I've already been reading
a minimum of 30 minutes a day for over a year, and often for hours, so I'm just
going to read different stuff.

I didn't put this in the first draft, because it feels kinda silly to get
inspired by a book about a famous person, but there's also another thing
that motivated me to do more programming on the side. I listened to the
audiobook on Steve Jobs while I was running. Really, I don't care that much
about Steve Jobs and still don't after listening to his life story. He
definitely had vision and did good things with Apple, and I'm writing this
on a Mac so can't complain about the results, but I consider him more of
a visionary businessman than a real hacker. I liked Isaacson's biography
of Benjamin Franklin and figured Steve Jobs would be another accessible work
by him for my runs. But you can't read about the founding of Apple without
encountering Woz. A true engineer that would've gladly made computers and
gave them away, because he loved tinkering with circuitboards. I don't really
care about circuitboards either; I've always been a software guy. But being
exposed to a story with that type of passion reminded me I used to be
passionate about computers.

I've always had a bit of a love-hate relationship with Apple. I still have
Linux on my desktop PC and am a proud member of the Columbia Linux User's
Group despite not attending meetings all that often.
The early Apple computers were toys with no CLI and one button mice
because multiple buttons are confusing. But after OS X was reborn with BSD
under the hood and a full fledged terminal, I found that having a computer
that mostly worked with the default configuration and
actually looked pretty good made it easier for me to focus
on writing code and not spend so much time tinkering around with Linux. I
learned from the Steve Jobs book that the first Macs were expandable
because Woz thought people should be able to tinker with their own computers.
Maybe I would've liked those better than the Macs at school.

Anyway, back to passion, I didn't take my computer apart and hide all the
pieces because I thought it would be faster when I put it back together
hours later. I did it because I wanted to learn how a computer was put
together (I didn't know I wasn't really a hardware guy back then; I honestly
prefer buying them off the shelf now).
I also didn't learn C and relational databases because I thought they would be
profitable (although database knowledge is the gift that keeps on giving).
I loved solving problems in C in the middle of the night on my hand-me-down
computer. I didn't found an ISP in the 90's to get rich quick,
I founded it to have fast Internet access and to have cool problems to
figure out. Likewise, I didn't make straight A's in school because I
expected it to help my
job prospects. No one cares about my GPA. I loved the material! It was
fascinating to learn about algorithms, operating systems, and, after
programming so long, compilers. Somewhere along the way, it just became work
like any other job. So it's a combination of factors: having more free time
now that my kid's a little older, work leaning harder on AI for the actual
code these days so I want to keep my own chops sharp on the side, a refound
passion for programming inspired by a rather unlikely source, and the fact
I've been reading every day over a year anyway, so why not make it technical.
I still don't know functional programming beyond how to apply a good
map and filter, and I still haven't tried a lot of different web frameworks.
They're all likely to be better than the Java EE/Spring hybrid monstrosity
that I work on most of the time. Almost anything beats JSF.

And as an aside, this will probably be my last time trying to learn
"functional programming". If I try to learn the secrets of Haskell again
and bounce off, I am just going to adopt Go as my programming language of
choice and write lots of simple procedural code with structs and `err`
checks every other line. As an old school C hacker and Perl scripter before
they bolted on OOP, it feels quite natural to write straightforward procedural
code, but I'm trying to work outside my comfort zone even if I think the
benefits of functional programming might be overpromised.

But I really kinda understood the point of functional programming with
*Advanced Functional
Programming with Elixir*, and all those `err` checks in Go grated at
my nerves, so the beauty of being able to chain a bunch of calls together then
deal with errors or results at the end was quite appealing to me. Monads
aren't really the Elixir way though. Your average Elixir programmer would
do some simple pattern matching to catch `:err` and deal with it instead, but
*Advanced Functional Programming with Elixir* featured a Haskell inspired
functional programming library and monads. And while I wasn't ultimately
convinced of the utility of the Reader or Effect monads (I'm open to learning
more about those in Haskell, and I will have to anyway if I spend time with
it), I really liked Maybe and liked Either even more. Even Java has Option,
but Either is a lot more useful. Plus parallel validations with Applicative
were kinda cool. They weren't a reason to re-learn programming, but I'll take
them along with my Either and roll with it a bit.

## Conclusion

So that's it. The blog is reborn. I've got one project that meshes with the
title of learning functional programming. I have another of trying web
frameworks that has some limited overlap built in and picks up where the
blog left off. I transferred my old posts over and rebuilt the site in Hugo
and moved over what I could from the old Jekyll files. And I've written a
very long coming back
post plus already have a stash of book reviews in my Obsidian. So I guess
I'm back and doing this for now and we'll see where it goes. I may get
tired of posting updates here and just read the books, but I like having
somewhere to collect my thoughts and review what I read.
