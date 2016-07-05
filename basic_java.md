---
layout: default
---

# Basic Java

### Purpose: The Fundamentals of Programming in Java

You have two days to get through the following material and solve
[Exercise 1](#exercise-1) below.

* As we will be using git extensively, go read the
  [git documentation](https://git-scm.com/documentation) (not
  necessarily all of it, start and the beginning, then start using
  git, and return to the documentation if needed), the
  [GitHub documentation](https://guides.github.com/activities/hello-world/)
  and if you want to use it, the
  [GitHub Desktop documentation](https://desktop.github.com/).
* [Think Java](http://greenteapress.com/wp/think-java/). That is a
  very good, free introductory book on Java. Read Chapters
  1 &ndash; 9. 

To solve the exercise you may use Google and StackOverflow at will
when you are stuck; however if you do find large parts of the solution
and you copy them verbatim, you defeat the purpose of the bootcamp and
you will not be able to progress much further.

### Working Environment

You may use any editor or Integrated Development Environment (IDE) of
your choice.

If you like to work with editors:

* [Atom](https://atom.io/)
* [Vim](http://www.vim.org/)
* [Emacs](https://www.gnu.org/software/emacs/)

If you prefer IDEs:

* [IntelliJ IDEA](https://www.jetbrains.com/idea/)
* [Eclipse](https://eclipse.org/)
* [NetBeans](https://netbeans.org/)

### Exercise 1<a id="exercise-1"></a>

You will write a Java program that handles numbers in three different
numbering systems:

* [Hindu-Arabic Numerals](https://en.wikipedia.org/wiki/Hindu%E2%80%93Arabic_numeral_system)
(which we actually use most of the time) 
* [Roman Numerals](https://en.wikipedia.org/wiki/Roman_numerals)
* [Greek Numerals](https://en.wikipedia.org/wiki/Greek_numerals)

Your program must be able to handle numbers up to 1000. When the
program starts, it will ask the user for an arithmetic expression that
may combine two numbers, in any combination of the above systems, with
one of the basic arithmetic operators (+, -, *, /). It will calculate
and output the result in all three different representations. Then the
program will ask for a new expression, and so on. It will terminate
when the user just presses enter, without giving a numerical
expression. Use only internet arithmetic.

When you start working into the exercise you may wonder how to handle
greek characters that are no longer in use. For digamma (number 6),
use the modern sigma teliko; for koppa (number 90), use the modern
latin Q (whose precursor it was, anyway); for sampi (number 900), use
the modern latin W (no relation, but they kind of look alike).

If you are using MS-Windows, you may want to use an alternative
terminal than the default. You can check out
[ConEmu](https://conemu.github.io/).

To solve the exercise use the material in Chapters 1 &ndash; 10 of
Think Java, that is, don't go into classes. Your program must be in a
GitHub repository. For consistence, create a GitHub repository called
called `dmst-coding-bootcamp` where you will put all the code you will
be writing in the bootcamp. You can put the code for this exercise in
a directory called `exercise-1`.
