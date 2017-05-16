---
layout: post
title: "AWDWR 5.1 - 01 - Introduction"
date: 2017-05-16
tags: ruby rails awdwr51 web
---

So, what do I have to blog about?  I'm always trying out new stuff and reading
books, so I figure I'll talk about that.  I happen to have just gotten a 
beta copy of 
[Agile Web Development with Rails 5.1](https://pragprog.com/book/rails51/agile-web-development-with-rails-5-1)
and since my Ruby and Rails 
experience from my r&eacute;sum&eacute; is a little rusty, I figure I'll
read that and blog about the experience.  Starting this site using Jekyll
has made me think about Ruby lately anyway.  It's been many years since I've 
read "Agile Web Development with Rails", and I think it was the version that
covered Rails 1.2, so this should be a pretty new experience for me; both a 
great refresher and an introduction to what is new in the Rails world these
days. 

The obvious question is why rails when I could play with the hot new 
Javascript framework.  Well, I've played with React some, along with Ember,
and Angular.  I might go back to messing with them and blog about the 
results later.  Right now, I'm just in a Ruby/Rails mood.  I've always liked
how the Ruby community seems to emphasize good programming practices that
carry over to any language you work in, and I recall the Agile Web Development
book being a good source of sound programming advice.  As a side note, I 
understand that the book now includes information on doing a Javascript
front-end with a Rails backend, so I'll get in some Javascript before I'm
through.

The introduction is well paced.  The parts I feel worth mentioning are
it's argument that "Rails Simply Feels Right", which I am inclined to agree
with.  I've always thought of Rails as the cadillac of web frameworks.
There's a lot of ways to do the same old CRUD in other frameworks, it's 
just rails has polish and a certain thoughtfulness of layout that makes it
all click.  It achieves a level of conciseness thanks to "Convention over
configuration", adhering to the philosophy of DRY (Don't Repeat Yourself),
and the natural conciseness of the Ruby programming language (a trait that
I miss a lot now in my job, where my Java code tends to include a lot of
boiler plate by necessity).  

The introduction shares a link to the guiding philosophy of
Rails, the [Rails Doctrine](http://rubyonrails.org/doctrine/).  It can be
argued that the Rails Doctrine is what makes Rails continue to be a strong
choice as a web framework, even though it's no longer the new darling on
the block, and as an aside is also one of the reasons I favor Ember of the
Javascript frameworks, since the Ember community were obviously
heavily influenced by the Ruby/Rails community.  The number one item on the
Rails Doctrine is "Optimize for programmer happiness".  This is lifted 
straight from Ruby, but is still something that many languages don't put
among the considerations, much less as a guiding principle.  I forgive them
for taking a shot at one of my other favorite language mottos, Python's
"one and preferably only one way to do something", which I also believe has
it's place.  But I get their meaning that having a choice of ways to express
a solution and being able to choose among them adds a certain bit of
artistry to the craft of programming.

I really appreciate the 2nd principle of the Rails doctrine, "Convention over 
Configuration".  Right now, my primary day job is working on an app that's
been around for 15 years, and it seems for every problem encountered the 
people came up with a way from scratch for how to handle it.  There's no
conventional way to do anything.  But as the author says, "Part of the Rails’ 
mission is to swing its machete at the thick, and ever growing, jungle of 
recurring decisions that face developers creating information systems for 
the web."  Sane defaults make a lot of things possible with little effort, 
as is shown by the demo app in the next chapter.  Just like the Principle of
Least Surprise, it begs the question of "Sane (or least surprise) to who?",
but in general the framework itself is built with enough consistency that 
once your steeped in its general way of doing things, they make sense as a 
whole.  I endorse the idea that freedom from choice is sometimes exactly
what is needed, rather than freedom of choice to do it a different way. 
"A place for everything and everything in its place. Constraints liberate 
even the most able minds."  This is the same type of consistency that 
Python's motto helps provide, but with some wiggle room left for expression
in implementation.

I could go on analyzing tenets of the Rails Doctrine, but let's get back to 
the book.  I will argue that I sometimes feel "monkey patching" is more
power than programmers need, even if it allows some cool tricks.  But I 
haven't used it much.  It just seems a nightmare that you might end up
having to look at someone's legacy code down the line where they completely
misused it and nothing makes sense.  But then again, I like having sharp
knives in my kitchen too.  I just don't have to cook after many other chefs.
Even good programmers sometimes make questionable decisions when pushed for
time assuming the language allows certain shortcuts.  It's the sharp knives
offered by Ruby and Rails that sometimes make me want to stick to the easy
consistency of Python and Django, even if they require a little more 
boilerplate to accomplish similar tasks.

I did promise to get back to the book.  It points out also that "Rails is 
Agile".  It's too easy to forget the core tenets of Agile development; they
become easily lost to a focus on the ceremonies of Agile.  The book restates
the four preferences of the Agile Manifesto:

* Individuals and interactions over processes and tools
* Working software over comprehensive documentation
* Customer collaboration over contract negotiation
* Responding to change over following a plan

As someone who works at an organization that is permanently mid-transition
between doing things waterfall and approaching them with more agility, I 
like to remember the core philosophy of the Agile Manifesto and ask if the
particular procedure we're seeking to follow embodies those ideas.  It's 
too easy for the core ideas to get lost in the ceremony of scrums and 
sprint planning meetings and the artifacts of burndown charts.

Who is this book for?  It's aimed at application programmers who want to 
build and deploy web based applications.  It's fine if your new to Rails, 
and it might be fine even if your new to Ruby.  My Ruby is rusty enough 
that I had to review at 
[Learn X in Y Minutes](https://learnxinyminutes.com/docs/ruby/), 
but that's a good sign I should
be alright.  I have a whole catalog of [Exercism](http://exercism.io/) 
problems that I worked in Ruby to review with too, in the worst case.  This
book is more about how to get things done, and doesn't attempt to act as
a detailed reference book.  There's online API references for that type of
stuff.

That was just the introduction!  We'll be a bit quicker now.  Especially 
since the first chapter is all about getting setup.  It has useful 
instructions for a variety of platforms, including working from a vagrant 
box or using the cloud9 online IDE.  I figure that I like having a recent
version of ruby around at the command line anyway, so I followed the OS X
instructions and used homebrew (which I already had installed).  I'm 
tempted to try Cloud9 sometime, especially since a quick Google tells me 
that it does have Vim keybindings.  Maybe some other time.  It looks like
in addition to rails, we need yarn and chromedriver.  I don't have yarn
installed yet, as I've just used npm for packages, and I'm looking forward
to using chromedriver from Ruby.  I use selenium and chromedriver at work
to do end-to-end testing of some of my applications, so I'm used to working
with chromedriver in Java.  I needed to uninstall rvm to get the new version
of ruby on my OS X box.  It seems that rbenv is the book's preferred way
for managing multiple Ruby's these days.

On an unrelated note, when did OS X get the ability to remap Caps Lock to
Escape without addons?  I always used to use Seil and Karbiner, but they 
quit working in the latest version of OS X.  I was about to try Karbiner
Elements, but when I checked modifier keys under Keyboard in System
Preferences, I saw that it had Caps Lock there and an Escape option.
Sorry to toss this in the middle of everything else, but it's really been 
bugging me in Vim to not have my Caps Lock act as Escape.  Unless I stay
on a Ruby kick, the next book I review might be 
[Practical Vim](https://pragprog.com/book/dnvim2/practical-vim-second-edition).  I
believe I saw the second edition was on 
[Safari Books](https://www.safaribooksonline.com/) the other day.
Sorry for the aside,
but I got distracted while waiting for homebrew to update all my packages.

Back to the book.  After covering installing in the environment of your
choice, along with some advice for when/if things go wrong, we get to
Chapter 2, "Instant Gratification".  In this chapter, we'll make a quick
demo app to get our feet wet with Rails.  I've put the demo app with
completed exercises up at [demo51](http://github.com/llcawthorne/demo51).
I'll cover Chapter 2 next blogpost, this one is already getting pretty 
large.
