---
layout: default
---

# OO Java, Maven, Unit Testing

You have two days to get through the following material and solve
[Exercise 2](#exercise-2) below.

### Purpose: Object-Oriented Java

To this point you have seen Java as a procedural programming language;
i.e., the basic unit of abstraction has been functions and procedures.
Now you will make the transition to viewing Java as an Object-Oriented
language.

* Read Chapters [Think Java](http://greenteapress.com/wp/think-java/).
  That is a very good, free introductory book on Java. Read Chapters
  10 &ndash; 14.

### Purpose: Maven

You can compile and build your Java programs by invoking directly
`javac` and other `jar`, but when your programs contain but a small
number of files this can be very frustrating.

Most Java programs are built using special build tools. These tools
take care of creating the proper directory structure for our program,
downloading any third-party libraries we need, and packaging the final
product in the appropriate way so that it can be deployed easily.

* A very popular Java build tool is [Maven](https://maven.apache.org).
  You must learn how to use it, as you will use it for most of your
  Java development.

* Start with
  [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html).

* Then proceed to the
  [Maven Getting Started Guide](https://maven.apache.org/guides/getting-started/index.html).

* The Maven web site contains a wealth of documentation; return to it
  whenever you want to do something that you do not know.

### Purpose: Unit Testing

Professional, production-ready programs are accompanied by extensive
test suites. Testing starts with writing *unit tests*. You need to
understand what unit testing is and how it works in Java.

* Unit tests are frequently written with [JUnit](http://junit.org/). 

* You can use JUnit by just downloading and putting in the class path.
  Go ahead,
  [download and install it](https://github.com/junit-team/junit4/wiki/Download-and-Install)
  and then see the
  [Getting started](https://github.com/junit-team/junit4/wiki/Getting-started)
  instructions. You will notice that the basic installation involves
  just downloading the appropriate jar file.

* JUnit was introduced to the world with a wonderful article,
  [JUnit Test Infected: Programmers Love Writing Tests](http://junit.sourceforge.net/doc/testinfected/testing.htm).
  Note that the article applies to an earlier version of JUnit.
  However, you are well advised to read it, because you will get a
  glimpse in the rationale of unit testing. In the same vein, read
  also the
  [JUnit Cookbook](http://junit.sourceforge.net/doc/cookbook/cookbook.htm),
  written by two world-class developers.

* Most often you will be using JUnit from inside Maven. To
  see how, check
  [Running JUnit Tests](https://books.sonatype.com/mcookbook/reference/unit-sect-junit-run.html)
  from the Maven Cookbook. That means that you do not really need to
  download and install JUnit; Maven will do all this boring stuff for
  you. This will hold for all the third-party libraries that we'll
  use. Maven will do the installations for us. And we will not need to
  mess with the Java classpath at all.

### Exercise 2<a id="exercise-2"></a>

This time you will rewrite the program of [Exercise 1]({{ site.baseurl }}/basic_java.html#exercise-1), but in an OO
manner.

* Think how you should structure your classes so that you minimize the
  code that you have to write.

* You will build your program using Maven.

* You must also write a comprehensive suite of unit tests, which will
  be called also from inside Maven. By "comprehensive" we mean that
  the unit tests should cover the operations you have implemented and
  representative numeral combinations.

At the end you will have written a program that follows the dicta of
professional software development in Java. 
