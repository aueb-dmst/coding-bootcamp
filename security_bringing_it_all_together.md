---
layout: default
---

# Security and Bringing it All Together

You have two weeks to get through the following material and solve
[Exercise 8](#exercise-8) below.

### Purpose: Understand Spring Security Basics

In most web applications security plays a crucial role. You are
certainly familiar with services that ask you to register, and then in
order to access them you have to provide a username and a password. It
is also common practice to ascribe roles to users: different roles
have access to different functionalities in our applications.
Moreover, users may have access-related attributes associated with
them: for example, whether their account is active, or expired.

Spring can allow access to specific pages of our application only on
users with particular roles. All the nitty-gritty of granting or
refusing access is taken care of by Spring. You should take that as a
general lesson: never develop a security framework yourself. Always
use a readily available, popular one.

The one we are going to use is
[Spring Security](http://projects.spring.io/spring-security/). That is
a very comprehensive framework with lots of functionality. You cannot
learn it all at once; it is much better to become acquainted with it
through a simple example and then explore more of it as you need it.
To start with Spring Security, head over to
[Security a Web Application](https://spring.io/guides/gs/securing-web/).

### Purpose: Storing Security Data in a Database

Assuming that you have gone through
[Security a Web Application](https://spring.io/guides/gs/securing-web/),
you may have noticed that the application has only one user and one
password; and these are hardcoded into the program. Of course this
will not fly in a real application. We want to have users that are
able to register in our services, and their services could not be
saved in the program code itself.

One way to secure access to a service is to save the set of approved
users in a database. The database contains user details and access
details. The access details usually comprise the username and the
password saved in a suitable form, as well as the roles ascribed to
the user.

It is important to ensure that user passwords remain secure. That
means that you should never, ever, store the user passwords in the
form that the user enters them. If the user enters the password
`3eaudxki7r`, you will *not* store `3eaudxki7r` in the database (or
anywhere else). You will feed `3eaudxki7r` to a special function that
produces an output, which you will then save to the database. The
function is special because no two passwords will have the same
output; it is also special because it is impossible to guess the
password from the output of the function. So, each time the user wants
to log in, they type their password, then your application takes the
password, passes it through the same function, and compares the output
with the output stored in the database. If your database is breached
or leaked, nobody will know anything but the transformed passwords,
and none will be the wiser.

All this is an application of
[password hashing functions](https://en.wikipedia.org/wiki/Cryptographic_hash_function#Password_verification),
this being in turn an application of
[cryptographic hash functions](https://en.wikipedia.org/wiki/Cryptographic_hash_function).

In technical terms, the password typed by the user is transformed by
the cryptographic hash function to a `digest`, saved into the
database. A good cryptographic function is
[bcrypt](https://en.wikipedia.org/wiki/Bcrypt). The bcrypt function
takes an input string and transforms it to another, unique string from
which we cannot guess the original input. You should not try to
implement it yourself. You should use a well-tested, publicly approved
library that implements it.

### Purpose: Starting with an Example Application

To see how everything fits together, you can refer to the example
application found
[here](https://github.com/louridas/spring-forms-security-jpa). The
application itself has very simple functionality. It allows users to
login, or to register. When they enter the application they can see
other users that have already registered, and they can logout. Even
though a minimal example, it will allow you to see:

* how you can apply Spring Security on top of a database

* how you can secure some pages but not all

* how to provide links so that the users navigate from one page to
  another

* how to apply different CSS styles to different pages of your
  application

* how to use hashed passwords and how on-line registration and
  password registration works.

To see all that in practice you can start by defining the appropriate
tables in a database:

{% highlight sql %}

CREATE TABLE users(
    id INT NOT NULL AUTO_INCREMENT,
    username VARCHAR(30),
    name VARCHAR(30),
    surname VARCHAR(30),
    password CHAR(60),
    email VARCHAR(30),
    address VARCHAR(200),
    age INT NOT NULL,
    PRIMARY KEY(id)
);

CREATE TABLE roles(
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(30),
    PRIMARY KEY (id),
    UNIQUE KEY role_name(name)
);

CREATE TABLE user_roles(
    id INT NOT NULL AUTO_INCREMENT,
    user_id INT NOT NULL,
    role_id INT NOT NULL,
    PRIMARY KEY(id),
    UNIQUE KEY user_id_role_id(role_id, user_id),
    CONSTRAINT fk_user_id FOREIGN KEY(user_id) REFERENCES users(id)
);

{% endhighlight %}

You may have noticed that the `password` field is 60 characters long,
to fit the output of bcrypt; the users will enter much smaller
passwords. Then you can seed the database with roles; to keep things
simple, we'll just use one:

{% highlight sql %}
INSERT INTO roles(name) VALUES("user");
{% endhighlight %}

After you have the database in place, study the code carefully. Use
Google when there is something in particular you do not understand. It
is perfectly normal to wonder what a piece of code is doing at first
sight, but you should be able to glean its meaning after some search
and some careful study.

### Purpose: One Step Beyond with TLS Support

The example application is not at all realistic in one aspect: the
user enters the password and submits it; then the password travels as
plaintext through the internet to the server that hosts our
application, where it enters our application. That means that
everybody that can eavesdrop on the internet in the path from the
browser to the server can get the password.

To solve that we must ensure that the communication itself between the
user browser and our application is encrypted. This is the purpose of
[Transport Layer Security (TLS)](https://en.wikipedia.org/wiki/Transport_Layer_Security).
Yes, for those of you who have been through algorithms, this is the
stuff that you have seen when you studied public key cryptography.

To make your application communication encrypted with TLS there are
some additional steps you need to take. First, you need to generate a
key for your application. You can do that with the following command:

{% highlight bash %}
keytool -genkey -alias CodingBootcampKey -keyalg RSA -keystore my_keystore.p12
{% endhighlight %}

You will be asked some questions; answer them, and the server key will
be generated. Then you place the file `my_keystore.p12` (you can
choose any name), which contains your server key, to the
`main/resources` directory of your application. Note that the server
key *must be kept secret*. Your application is as secure as the server
key. Then you must add the following lines to the
`application.properties` file:

```
server.port=8443
server.ssl.key-store=classpath:my_keystore.p12
server.ssl.key-store-password=whatever
server.ssl.key-password=whaveter
```

The passwords are the ones you entered when `keytool` asked you to do
it. When you restart your application, it will no longer be available
through `http://your.host:8080`! You will have to use
`https://your.host:8443` (spotted the difference?). When you do, you
will get a warning from your browser. That's OK, go ahead. The warning
is because you generated the server key and you signed it yourself,
stating that it is valid; but how does somebody know that you are who
you say you are? In a real production environment you get a server key
from a certified company, such as
[DigiCert](https://www.digicert.com/). But for development purposes a
self-signed key will do.

### Exercise 8<a id="exercise-8"></a>

* This is open-ended. Think of a small, real application that you
  would like to develop and build a couple of pages and forms for it.
  Then secure it using as example the code in this module
