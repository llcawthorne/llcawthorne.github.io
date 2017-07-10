---
layout: post
title: "O'Reilly Spring Framework Essentials"
date: 2017-06-26
tags: java spring video web
---

This time I'm working on reinforcing some of the Spring and Spring Boot
knowledge I've picked up from other videos, while seeing if I can learn
a couple of new tricks while at it.  I'm watching 
[Spring Framework Essentials](https://www.safaribooksonline.com/library/view/spring-framework-essentials/9781491942680/) through my Safari Books Online membership.
It's presented by Ken Kousen, who often hosts the Groovy Podcast.  He has a
series of three Groovy videos in Safari Books Online that I wouldn't mind
going through sometime in the future.  The video series runtime is 5 hours,
14 minutes and it has a five star rating from 35 reviewers.  Not bad, let's 
see what it covers.

So, these videos are going to focus on the core Spring Framework.  So we
won't be getting back into Spring Data or even Spring MVC in this video
series.  It says that it will talk a little about Spring Boot, since that's
the general way to get projects started these days.  "One thing that you'll
notice about the Spring Framework, is that they never met a class or package
name too long."  Tell me about it.  Spring makes you appreciate autocomplete.
He uses gradle to manage projects, which is fine.  Maven or gradle are both 
fine options.

He did a fine demonstration of basic injection in 
XML, annotations, and Java config setup and quick intro to aspect
oriented programming that included an example of the `@Around` advice.  Then
he gave a quick introduction to Spring testing.  Finally someone that doesn't
ignore testing.  It turns out you can annotate you test class with 
`@RunWith(SpringJUnit4ClassRunner)` to have Spring aware tests, and you 
can add the `@ContextConfiguration(classes = AppConfig.class` so that you
have a cached ApplicationContext shared between tests in the class and the
ability to `@Autowire` any of your beans.  You can even `@Autowire` an
`ApplicationContext ctx` variable to inject a reference to your 
ApplicationContext to use in tests to fetch beans you don't autowire.  The
fact that `@ContextConfiguration` takes a classes argument lets you have a
different configuration class for tests than the running application if
necessary.  You can also add the `@Transactional` annotation to your test 
class to make all your tests occur in a transaction that gets rolled back
after test completion.  His toy app that he used to demonstrate early 
principles didn't have any database interaction to show-off transactional
tests, but this is the part of the course that he switches from a toy app
to something a little more complicated.  He also mentions that the Spring
pet-clinic demo app makes good use of transactional tests.

The new application has a Service and a Repository interface.  Instead of
using Spring Data, he does all the database operations with an in-memory
and a JDBC implementation.  Everything is marked `@Transactional` at the
Service level.  He had to makea  "transactionManager" Bean and use an 
`@EnableTransactionManagement` on his Configuration class, neither of which
I recall being required when doing a Spring Boot app with `@Transactional`.
The JDBC is using the Spring JDBC Template and is a lot cleaner than straight
JDBC.  The JDBC Template does a lot of work for you.  For example, the 
following one-liner works for getting a count: `int rowCount = 
this.jdbcTemplate.queryForObject("select count(*) from t_actor"),
Integer.class);`  I like the way he looks up what he is talking about in the
online API, the same way you likely would when programming with the various
API elements.  He shows off using "test" and "prod" profiles to differentiate
between an H2 in-memory database and an Apache data connection pool backed
by MySQL.  Each repository method with the JDBC Template ends up being two
to four lines long, depending upon what he's try to do.  Pretty simple, but
not as simple as not defining implementation methods with Spring Data JPA.

Yay!  More testing.  This time we're testing repositories.  Just set the
annotations on the test class and annotate the test profile, then autowire
the repository and your good to go.  Each test is transactional, so they
roll back changes at the end of each test.  He uses Hamcrest matchers, so
he can make assertions like `assertThat(accounts.size(), is(3));`, which 
flows a bit better than standard assertEquals.  He points out that since
he is using gradle he can show the really cool gradle test report.  The
tests he ran were all quick, even with firing up and setting up the 
in-memory database.  First one took half a second, but the all six of them
took less than a second total.  He succeeded in exercising all his 
repository methods and making sure they worked as expected.

I was wrong that we weren't going into Spring Data.  He reimplements his
repository using Spring Data JPA for the next project.  Spring Data JPA
repositories are just interfaces.  You get queries generated for free based
upon how you name the methods in the interfaces.  You can also use the 
`@Query` annotation above a method in the interface to give it a custom
query if the autogenerated language can't handle what your after.  He defined
the JpaVendorAdapter and LocalContainerEntityManagerFactoryBean manually in
the Java Spring configuration file, which normally weren't require with 
Spring Boot.  It's interesting to see how this is all done by hand, and it
isn't that much in total lines of configuration.  He didn't use the feature
of Spring Data JPA to allow repository autogeneration of methods and just 
defining an interface.  Instead he defined a JpaAccountRepository that
implemented its various methods directly through an EntityManager.  He does
use `@PersistenceContext` annotation to inject his EntityManager.  Most of
the methods now are one or two lines long.  He did have to add JPA
annotations to his entity class, but most of them defaulted through good 
name selection for class and fields.  Only `@Entity` on the class and `@Id`
on the primary key field actually needed to be added to the domain object.
He shows that you can use the same service with the JPA repository as was
used with the JDBC Template repository, since he designed the methods to 
take the same arguments.  He uses the same tests also, which makes sense as
the interface and expected outputs are the same.

I forgot to mention it earlier, but this presenter uses IntelliJ for 
everything.  Always nice to see!  Oh, he was just using JPA in the last 
project.  The next project is where he's adding in Spring Data to get 
the free implementations of DAO methods.  So, it turns out he uses Spring
Data for the last 12 minute segment of the presentation, and then switches
to showing the same app with Spring Boot for the last 15 minutes of the
presentation.  The app keeps getting simpler each time he introduces
more Spring features.  He actually extended JpaRepository for his 
repository, where I am more accustomed to seeing CrudRepository or 
PagingAndSortingRepository extended.  JpaRepository extends both.  He had
to change the method names in his service and tests to match the ones 
freely given by having an interface extend on of the Spring Data interfaces, 
but got to delete a lot of code that was the repository class implementation
and previous repository interface which was more complicated.  Interesting
to see that his tests run quicker now too, taking a little under 0.4 seconds.
He's still using an H2 in-memory database for testing and setting it up
with the same sql scripts.  He points out that all his earlier work really
was unnecessary.  The final project is to show how much of his configuration
he can get rid of also by using Spring Boot.  It's still interesting to 
know how to do it by hand, since everything we've seen is still happening
under the hood in Spring Boot.

So, at the end, he claims that a Spring Boot focused course is coming.  I
don't see it as available yet.  He had mentioned earlier this video course
would be the start of a series.  I really enjoyed Ken's presentation, and
would definitely watch more in this series by him.  It was a neat change
seeing Spring used for non-web apps.  I hope in the future videos he shows
off Spring MVC though, because Spring makes some nice web apps too.  He
recommends the book Spring Boot in Action at the end, but I found that book
fairly worthless.  The source code for it didn't match up with what was 
described in the text.  Maybe now that I actually have a grasp on some of
this stuff, it would be useful and I could figure out why the sample source
code and the text don't match up.  Anyway, despite his poor book
recommendation at the end, I really enjoyed this video series.  It's worth
a watch if your looking for something to view with your Safari Books Online
membership.
