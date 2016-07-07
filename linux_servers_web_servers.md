---
layout: default
---

# Linux Servers, Web Servers

You have two days to get through the following material and solve
[Exercise 3](#exercise-3) below.

### Purpose: Getting your Hands on Linux

Although you may be writing your programs in your local computer,
internet applications must be deployed on a web server. In most
situations the web server will be running on a server computer running
Linux (the GNU/Linux operating system, to be exact).

You can get your own Linux server on the
[~okeanos](https://okeanos.grnet.gr) service. Sign up to ~okeanos
using academic login with your AUEB credentials. Once you have signed
up, go to the ~okeanos dashboard and apply to join the
dmst-coding-bootcamp.dmst.aueb.gr project. When you are notified that
you have been accepted to the project, go to the Cyclades tab and
create a new virtual machine with the following characteristics:

* Operating System: Ubuntu Server LTS
* 2 CPUs
* 4 GB RAM
* 40 GB Disk storage
* 1 Public IPv4 address

At the end be very careful to write down the connection details. You
will not be able to connect to your virtual machine without the
displayed username and password.

Assuming that you have the username and the password, you can connect
to your virtual machine using an appropriate terminal program. If you
are using a Macintosh, then you just use `ssh` with the connection
details on a terminal window. If you are using MS-Windows, then you
must use
[PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html),
so
[download PuTTY](https://the.earth.li/~sgtatham/putty/latest/x86/putty-0.67-installer.msi)
and install it. For details on how to use PuTTY, read
[the PuTTY user manual](http://the.earth.li/~sgtatham/putty/0.67/htmldoc/).

### Purpose: Learning Linux

You need a lot of time to learn Linux in depth, but fortunately you do
not need to know everything about Linux to start using it
productively. There is a lot of open material on the web. You can
start with:

* [Ryan Chadwick's Linux Tutorial](http://ryanstutorials.net/linuxtutorial/)
* [William Shotts's Command Line Tutorial](http://linuxcommand.org/)
* [Ryan Chadwick's Bash Scripting Tutorial](http://ryanstutorials.net/bash-scripting-tutorial/) 

Be careful: your system is out there on the web. That means that
everybody can try to access it. You must take care of your system. A
vital part of that is making sure that you update it frequently. To
update it, use the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

### Purpose: Getting to Know the Apache Web Server

The web is based on web pages; but how are web pages served to the
people browsing the web? That is the job of *web servers*, special
programs that respond to user requests with the appropriate web pages.

The most popular web server on the internet is
[Apache](https://httpd.apache.org/). So an essential part of learning
to develop web applications is learning the fundamentals of the Apache
server. You can start with the following:

* [Ubuntu Apache Installation](https://help.ubuntu.com/lts/serverguide/httpd.html)
* [Digital Ocean Apache Configuration Guide](https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps)

### Exercise 3<a id="exercise-3"></a>

Just go over the material covered in this module:

* Create a virtual machine with the specifications given above.

* Connect to your virtual machine.

* Install Apache on your virtual machine.

* Visit the default Apache web page on your virtual machine.

When you are done, send the instructor the URL pointing to your Apache
instance. So, no programming this time! But getting a working server
up and running for the first time is no minor task...

