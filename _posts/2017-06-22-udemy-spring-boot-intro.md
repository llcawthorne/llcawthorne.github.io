---
layout: post
title: "Udemy - Spring Boot Intro"
date: 2017-06-22
tags: java spring video web
---

I figured since I am a professional Java programmer that I might as well
spent some time getting familiar with some Java technologies that I don't
get to use at work.  With this in mind, I purchased Udemy's "Spring Boot
Intro" course for $10 when they had a sale.

This course moved a lot quicker than the last course I took from Udemy.
It covered basic dependency injection in Spring in probably an hour or less,
where the last class focused on dependency injection fundamentals for the
entire time.  I appreciated the faster pace, as there's a lot of stuff
to cover with Spring Boot.  It handles autoconfiguring all the main projects
that make up Spring...  Spring MVC, Spring Rest, Spring Data, Spring Security,
etc.

This author made it really hard to code along with him.  He did things 
like restart a project with unknown initialzr settings in between
videos.  He also copied and pasted a lot of code, so you couldn't really
type along with him.  As long as you don't mind pausing and typing 
something in, it wasn't unworkable, but it got a little old.  I ended up
checking out his repo of code samples and following along with them.
He does have exercises at the end of each section, which are a good
chance to code some stuff up on your own.  He doesn't mention specifically
when he changes projects from the repo either, so it's a little hit and
miss making sure your looking at the right code that he's working on.

One nice thing is this guy used IntelliJ instead of Eclipse.  He admitted
that you need the paid for version to work with Spring, but just told
people to sign up for the 30 day trial.  Fortunately, I still have my student
license, so I had all the features to play along.  It might be annoying to
people that have already done the IntelliJ trial, since it makes it harder
to follow along.  Of course, he's pretty hard to follow along with as it is,
so using STS or Eclipse wouldn't be that much worse.  Anyway, I was excited
at first that he used IntelliJ, but then he switched to Eclipse STS halfway
through the videos.  I kept following along in IntelliJ.

I liked the Spring Boot way of doing apps.  It felt like convention over
configuration brought to the Java world, the way it autoconfigures so much
stuff based upon what it finds loaded in your class path.  I really liked
Spring Data, which allows you to pair up standard JPA entities with 
Repository interfaces that automatically generate the implementation with
queries based upon the names of the method defined in your interface.  
For example, if you make a method called `findByLastName(String lastName)` 
in your interface, you get the query you would expect for free.  The 
instructor didn't go into this, but it also works with QueryDSL predicates
to fill in the queries, which is pretty cool since I use QueryDSL at work. He
also showed how to do everything by hand with JDBC, but I liked the JPA
approach better.  He also showed that you can drop in mongo DB and swap
out Entity annotation for Document pretty easily in an app with very little
changes.  It was a weird choice doing JPA backed by a Microsoft SQL Server
database, and since I didn't feel like signing up for an Azure trial, I 
just kept using H2. 

I really liked the Dev Tools with live reload.  He showed that you have to
change a few settings in IntelliJ.  In the registry you check
compiler.automake.allow.when.app.running and in the 
Preferences->Build, Execution, Deployment->Compiler you check the 
Build project automatically.  Then you install a browser extension from
http://livereload.com/extensions/ and it will reload automatically when 
anything changes in your code. It isn't that much work really to save
hitting refresh all the time.  He doesn't use that in most of his projects,
but I kept it turned on in all the ones I did by hand.

I like Spring Security, but found the course's presentation of it to be 
a little light.  It does explain how you get free security headers, some XSS
prevention, and CSRF tokens just by including Spring Security, and in his
example he works up to a custom login form backed by a database (this time
MySQL) of users, but he stores the passwords in plain text, so his app
wouldn't be that useful a model to look at if I ever wanted to do this for
real.

The REST presentation was more thorough than it needed to be.  It seems
like every talk about REST has to go over what the different status codes
mean first thing.  Why not just link out to HTTP Status Cats website.
I want to know how he gets his JSON formatted so pretty in the browser.
I'm sure it's a plugin, but it isn't one I already have.  Oh, he finally
mentioned what it is during the REST videos.  "JSON Viewer" extension for
Chrome.  Nice.  Anyway, I thought REST frameworks were easy to setup when
we were doing them the hard way (RestController annotations and services), 
but it turns out you can get rid of your controllers and services and 
directly expose your repo through a default build REST API if you don't
need a lot of custom logic.  There's even a built in HAL Browser for
discovery and interaction with the API, if you choose to include it.
HAL Browser dependency comes from org.springframework.data and not 
org.springframework.boot.  That tripped me up for a minute in the exercises.

For the final series of lectures, he expects you to work along with him
starting from an initial setup.  We'll see if this works any better...  Nope!
He still does a lot of stuff off-screen between videos.  Anyway, the final
project is a blogging website.  It uses bootstrap to look good, thymeleaf
for the templates, spring data jpa for the database interaction, and 
spring security to enforce editing only by those with admin level privileges.
I still need to read the docs on thymeleaf templates to feel like I know
much about them, since he always provides the templates and doesn't explain
much.  They look pretty simple.  Extra attributes to HTML tags causes you
to override content that is present in the source and do other modificiations.
Like `<span sec:authentication="name">Guest</span>` will default to Guest,
but will override that value with the name of whoever is currently 
authenticated.  Judging from the upcoming titles, he's going to throw in
some validation, which is a topic he hasn't covered in the previous sections.

I couldn't get his instructions for customizing validation messages to work
at all.  I got validation working pretty good with the default error 
messages at least.  He claims you just need to put your custom messages
in a messages.properties file, but I did that and they didn't get picked up.
I assume I have to do something to get it to look in message.properties. 
Everyone on stack overflow with a related problem seems to be running WAR's, 
so those questions don't seem to apply to my setup.  I'll dig in the 
documentation later and see what's going on.
