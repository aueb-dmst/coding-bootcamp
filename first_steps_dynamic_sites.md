---
layout: default
---

# First Steps in Dynamic Web Sites

You have two days to get through the following material and solve
[Exercise 5](#exercise-5) below.

### Purpose: First Steps in Spring

Up to now the things you have been developing on the web are *static*.
All web applications, however, are *dynamic*. That means that they take
input from the user who visits the site and they alter the pages according
to the user's input. 

To create a real web application you have to use a *web development framework*.
There are many web development frameworks, and new ones are created all the
time, although the ones that have a lot of adopters are few.

* For those that like programming in Ruby, the obvious choice is [Ruby
  on Rails](http://rubyonrails.org/); that is probably the most famous web
  development framework of all, thanks to its simplicity and elegant design,
  and it has influenced web development in all other languages.

* For Python, the most popular framework is
  [Django](https://www.djangoproject.com/). You can do pretty much
  everything in Django and as Python is used for more stuff than Ruby is,
  you can leverage Django to interface directly with all kind of Python
  libraries. If Django is overkill and you need something simpler,
  [Flask](http://flask.pocoo.org/) is an obvious choice.

* For Java the de facto standard is [Spring](https://spring.io/),
  which is pretty much synonymous with web development in that language.
  It is very popular for big enterprise applications; that means that it
  has enormous capabilities, but to really learn Spring in depth you need
  to devote a lot of time.

As this course is using Java, we will cover Spring. Knowing that it is
quite a beast, we will only cover the things that we absolutely need.
Fortunately tor us, the Spring developers have understood that you can
learn how to develop web sites with it without learning every little
detail, and they have developed a very good set of tutorials and
guides for that purpose.

* Without further ado, start with [Serving Web Content with Spring
  MVC](Serving Web Content with Spring MVC).

### Purpose: Dynamic HTML Forms

The most common way to accept input from a user in a dynamic web site
is through the use of *forms*. Forms are created using HTML that
accepts the user's input; this is then fed into our application that
runs on the web server; our code takes the input and then proceeds
with the interaction with the user, most probably displaying a new web
page.

* To learn how HTML forms are constructed, check the [w3schools HTML
  tutorial](http://www.w3schools.com/html/html_forms.asp).

* Then, proceed to [Validating Form
  Input](https://spring.io/guides/gs/validating-form-input/). You will
  learn how to write the *back-end code* that handles your form; you
  will also learn how to inject output from your code into your HTML
  page. This is done using a *templating* mechanism; the guide uses
  one called Thymeleaf.

### Exercise 5<a id="exercise-5"></a>

Just go over the material covered in this module and then:

* Create a form that accepts user data and validates them. The data
  should include a person's name, surname, age, address, and e-mail.
  You should combine your knowledge of Bootstrap with your newly
  acquired Spring skills so that your form looks much better than the
  one in the tutorial guide above.
