---
layout: default
---

# Deployment on MySQL and Tomcat

You have two days to get through the following material and solve
[Exercise 7](#exercise-7) below.

### Purpose: Installing Java on Ubuntu

To install the Oracle Java implementation on Ubuntu, enter the
following commands on the command line:

{% highlight bash %}
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
{% endhighlight %}

You should test that everything is OK with:
{% highlight bash %}
java -version
{% endhighlight bash %}
The response should indicate that you are using the latest version of Java.

### Purpose: Installing MySQL on Ubuntu

Installing server software on Linux is usually easier than installing
them on desktop machines; after all, that is why Linux servers are
intented to do. To install the MySQL server and client on your Linux
virtual machine, enter the following at the command line:

{% highlight bash %}
apt-get install mysql-server-5.7
apt-get install mysql-client-5.7
apt-get install libmysql-java
{% endhighlight %}
The first command installs MySQL server; the second command the client
tools; the third the Java connector. 

You will be asked to enter a password for the database's root user. Do
so and make sure you do not forget that password. After the
installation is complete, you can check that everything is fine with:
{% highlight bash %}
mysql -u root -p
{% endhighlight %}
After entering your password you will be taken to the MySQL prompt
where you can interact with the database.

MySQL will start automatically every time you start or reboot your
server. If you want to manipulate directly:

* `service mysql stop` stops MySQL
* `service mysql start` starts MySQL
* `service mysql restart` restarts MySQL

You will need to be root to execute these commands. So you must 
prepend them with `sudo` (e.g., `sudo service tomcat8 start`).

### Purpose: Configuring your Application for MySQL

Your application must know which database it will use; it will also
need to know the credentials (username and password) that it will use
to connect to the specified database. This information, as well as any
other configuration information that your application may need, is
entered into a file called `application.properties`, which is placed
in the `src/main/resources` directory in your project. As an example,
your `application.properties` files should contain:

{% highlight conf %}
spring.datasource.url=jdbc:mysql://localhost/coding_bootcamp?serverTimezone=Europe/Athens&useSSL=false
spring.datasource.username=themysqldatabaseuser
spring.datasource.password=thisisthepassword
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
{% endhighlight %}

Another change you have to do concerns the `id` attribute of the
entities you are going to save. They will need to be declared as
follows, in their class file:
{% highlight java %}
@Id
@GeneratedValue(strategy=GenerationType.IDENTITY)
private long id;
{% endhighlight %}

This declaration must be consistent with the way the `id` attribute is
declared in the SQL table:
{% highlight sql %}
CREATE TABLE my_table (
	id INTEGER PRIMARY KEY AUTO_INCREMENT,
    ...
{% endhighlight %}

Finally, you must build your application using the MySQL Java
connector libraries. That means that you have to add the appropriate
dependency in your `pom.xml` file:
{% highlight xml %}
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>6.0.3</version>
</dependency>
{% endhighlight %}

### Purpose: Introducing Tomcat

Your web applications are written in Java. However, the Apache web
server, which you have met to this point, can only serve HTML web
pages. It does not understand Java.

In order to run a Java web application, your code must run inside a
web server that can take your Java compiled code and execute it. The
most popular web server for handling Java web applications is
[Apache Tomcat](http://tomcat.apache.org/).

In fact, you have already used Tomcat. In the dynamic pages you have
built you have implicitly used an instance of Tomcat embedded in your
application. When you run your application what really happens is that
Tomcat starts locally on your machine, it loads the Java code of your
applications, runs it and serves the web pages.

Im most cases, though, you will have Tomcat up and running on your
production server machine (be it virtual or real). Therefore you will
want to upload your application to *that* Tomcat, so that it will be
accessible to the rest of the world.

You start by installing Tomcat on your server. That is an one-liner:
{% highlight bash %}
apt-get install tomcat8
{% endhighlight %}
Once the installation is complete you can verify that Tomcat is up and
running by entering the URL composed of the IP of your machine, followed by
`8080`, e.g., `http://my.vm.machine.address:8080`. You should see the
Tomcat welcome page.

Tomcat will start automatically every time you start or reboot your
server. If you want to manipulate directly:

* `service tomcat8 stop` stops Tomcat
* `service tomcat8 start` starts Tomcat
* `service tomcat8 restart` restarts Tomcat

You will need to be root to execute these commands. So you must 
prepend them with `sudo` (e.g., `sudo service tomcat8 start`).

### Purpose: Deploying Web Applications to Tomcat

To develop a Java web application to Tomcat you must package it in a
format called
[WAR (Web Application Archive)](https://en.wikipedia.org/wiki/WAR_(file_format)).
One way to create it is to run maven as follows:
{% highlight bash %}
mvn compile war:war
{% endhighlight %}
There are also other ways; for example, you can make a small change
to `pom.xml` so that `mvn package` will create the WAR file. For more
details see the
[documentation of the maven WAR plugin](http://maven.apache.org/plugins/maven-war-plugin/usage.html). 

Note that since your application has been using an embedded Tomcat
instance, you will need to make some changes to it as well. See
[Traditional deployment](http://docs.spring.io/spring-boot/docs/current/reference/html/howto-traditional-deployment.html)
in the Spring documention. In particular y ou must make the indicated
changes in the `Application` class and add the
`spring-boot-starter-tomcat` dependency in your `pom.xml`.

In the end, you should see a file ending in `.war` in your `target`
directory. This contains your web application. To deploy it on Tomcat,
you need to copy it in the appropriate directory of your Tomcat
installation. This directory is `/var/lib/tomcat8/webapps/`. When you
copy the WAR file in this directory, it will be unpacked. If the name
of the WAR file is `my-app.war` (you can copy it with any name you
want), the application will be available to its users with the URL
`http://my.vm.machine.address:8080/my-app`.

### Purpose: Copying Files to a Remote Server

To copy a file to a remote server, you must use a secure method. If
you are working on a Macintosh or a Linux computer, then you enter:

{% highlight bash %}
scp local_file_path username@remote_computer:remote_file_path
{% endhighlight %}

where `local_file_path` is the path to the file you want to copy from
your computer, `username` is your username on the remote serer,
`remote_computer` is the name or the IP address of the server to which
you want to copy the file, and `remove_file_path` is the path where
you want to copy the file on the remote server.

If you are using MS-Windows, you must use
[pscp](http://the.earth.li/~sgtatham/putty/0.67/htmldoc/Chapter5.html#pscp),
which is installed along with PuTTY.

### Exercise 7<a id="exercise-7"></a>

* Take the application that you developed in the
[First Steps in Dynamic Web Sites](first_steps_dynamic_sites.html) but
this time deploy it on a Tomcat instance running on your virtual
machine. It will run it on top of MySQL, so you should first install
MySQL and create a database containing the table, or tables, that you
will use. Then install Java and Tomcat, and copy the WAR file to
your Tomcat applications directory.
