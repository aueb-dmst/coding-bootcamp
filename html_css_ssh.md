---
layout: default
---

# HTML, CSS, and a bit of SSH/SCP

You have two days to get through the following material and finish
[Exercise 4](#exercise-4) below.

### HTML

Web pages are written in the HyperText Markup Language (HTML).
Contrary to popular belief, HTML is *not* a programming language: it
does not have constructs to execute steps, take decisions, or repeat
things. It can only describe the structure and, to a certain degree,
the look and feel of a web page.

There is plenty of free material that you can use to learn HTML. Here
are a few pointers:

* [HTML Tutorials by HTML Dog](http://htmldog.com/guides/html/)

* [HTML Tutorials by w3schools](http://www.w3schools.com/html/)

* The HTML material from
  [MDN's Learning web development](https://developer.mozilla.org/en-US/Learn/HTML)

### CSS

HTML is intended to describe the structure of the document. Although
you can, with considerable effort, use it for visual design, that is a
bad idea. You should separate what a document item is (for example, a
heading), from how it is actually displayed.

We can achieve that by using Cascading StyleSheets (CSSs). A CSS
provides rules that are attached to document elements: for example,
that a paragraph should be displayed with a specified margin and font.

Again, there is free material galore on CSS; a few pointers:

* [CSS Tutorials by HTML Dog](http://www.htmldog.com/guides/css/)

* [CSS Tutorials by w3schools](http://www.w3schools.com/css/)

* The CSS material from [MDN's Learning web development](https://developer.mozilla.org/en-US/Learn)

### Bootstrap

[Bootstrap](http://getbootstrap.com/) is an HTML, CSS, and JavaScript
framework for web development. It is very popular, as it provides the
means to create responsive web pages that look nice on different
browsers as well as mobile devices. After spending some time with HTML
and CSS you will discover that each browser has its own foibles, and
writing a web page that looks great on all of them is quite a task.

Bootstrap, developed by Twitter, simplifies things. It defines a set
of CSS classes that you can use so that you have a cross-platform,
consistent, aesthetically pleasing look and feel. To learn Bootstrap
check out:

* [Bootstrap 3 Tutorial by w3schools](http://www.w3schools.com/bootstrap/default.asp)

* [Bootstrap's own documentation](http://getbootstrap.com/getting-started/)

### A Bit of SSH/SCP

As you proceed, you may find yourself writing files on your local
computer and then having to transfer them to your web server. How do
you do that? You use SSH (Secure Shell) and SCP (Secure Copy). These
are protocols that work with strong, public key cryptography, to
ensure that you can communicate securely with other computers.

* If you use an MS-Windows machine, PuTTY, which you have already
  encountered in [Module 3](linux_servers_web_servers.html),
  implements SSH, and you can use it to connect to a remote computer.
  You can use the `pscp` program, included with the PuTTY
  distribution, to copy files between computers.

* If you use a Macintosh or a Linux machine, then to learn basic SSH
  and SCP you can look at:
  * [SSH and SCP: Howto, tips & tricks](https://linuxacademy.com/blog/linux/ssh-and-scp-howto-tips-tricks/)

* To really understand how SSH and SCP work, you must know a little
  bit of cryptography. For a gentle introduction, you can check out
  [DigitalOcean's SSH Encryption and Connection Process](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).

### Exercise 4<a id="exercise-4"></a>

After covering the material in this module:

* In the Apache server you have set up in [Exercise 3](linux_servers_web_servers.html#exercise-3):

* Delete the default `index.html` page.

* Create a web page, presenting yourself, using the Boostrap
  framework. You are free to include anything you want; it can be a
  typical CV (but make an effort to have a nice layout), or something
  more creative. 
