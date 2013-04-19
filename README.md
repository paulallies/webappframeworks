#Web Application Frameworks

Here we will be looking at a couple of <a href="http://en.wikipedia.org/wiki/Web_application_framework" target="_blank">web application frameworks</a> that support some modern <a href="http://en.wikipedia.org/wiki/Dynamic_programming_language" target="_blank">dynamic languages</a>.  Obviously the frameworks need to follow the MVC <a href="http://en.wikipedia.org/wiki/Architectural_pattern_(computer_science)" target="_blank">architectural pattern</a> to separate the <a href="http://en.wikipedia.org/wiki/Data_model" target="_blank">data model</a> with <a href="http://en.wikipedia.org/wiki/Business_rules" target="_blank">business rules</a> from the user interface.  We will be evaluating the following frameworks:

1. Python and Django
* Groovy and Grails
* Node and Express
* Ruby on Rails

For each of these frameworks we will discuss the following:

* Installation on all platforms (windows, linix, mac)
* Dependencies
* IDEs
* Command Line Interpreter
* Closures
* DataBase Access / ORM
* REST Client interfaces


##Python and Django
The Django framework is an MVC based one.  It has an ORM which mediates between data models(defined as Pythoon classes) and a relational database.  A templating engine and routing system is also included.

Included:
A lightweight, standalone web server for development and testing.

Django can be run in conjunction with Apache, NGINX using WSGI

##Ruby on Rails
Rails enables you to create database-driven web applications with remarkable speed and ease.


##Groovy and Grails
Groovy has closures which is a simple executable block of code



##Node Express
Node uses the event-driven programming model to create scalable servers without using threads.  Node
provides a purely event-driven, non-blocking infrastructure for building highly concurrent
software.

###A small aside on threading vs event-driven programming styles
A thread is a path of execution through a program. Single threaded programs have one path of execution, and multi-threaded programs have two or more paths of execution. Single threaded programs can perform only one task at a time, and have to finish each task in sequence before they can start another. For most programs, one thread of execution is all you need, but sometimes it makes sense to use multiple threads in a program to accomplish multiple simultaneous tasks.  A thread is the basic unit to which the operating system allocates processor time and memory.
Traditional programming does I/O(long running task) the same way as it does local function calls: Processing cannot continue until the IO operation finishes. This thread is now blocked and will not be used while it is waiting for a response from the I/O operation.  During this time, if another request comes in for the same I/O operation then another thread is spawned.

Mutli-threaded application is one alternative to this programming problem.  Multi-threading is a widespread programming and execution model that allows multiple threads to exist within the context of a single process.  These threads share the process' resources, but are able to execute independently. This means that programmers do not know what set of threads is executing at any given time and need to keep track of concurrent access to the shared memory state. If process and thread tracking is not done unforseen problems can occur.  If the application relies on shared state between threads, this type of programming can easily lead to strange bugs.

Event-driven programming is a programming style whereby the flow of execution is determined by events.  Events are handled by event handlers and event callbacks.  A callback is a piece of code(a function) that is executed when something significant in the program happens(an event).  So for example when we make a call to a database for a recordset in traditional I/O programming, it has to wait for the response from the database before it continues.

```js
	result = query('select * from users where id =1');
	do_something(result);
```

In event-driven programming, the query will be giving a piece of code to execute when the result returns from the database.  In the meantime the program execution will continue.

```js
	query('select * from users where id =1', function(result){
		do_somthing(result);
	});
	continue_to_do_something();

```
We can see here that the query is given a function to run as soon as it receives a result.  The program's use of resources is therefore more efficient.  This is one of the defining features of Node.  It means that concurrent programming will not block when doing I/O.  All of the event-driven execution is done by an event loop.  The event loop performs two functions - event detection, and event handler triggering.  The event loop uses one thread running inside one process.

##Learning Curve
The learning curve for nodejs and express is flat as all web developers are or should be equipped with JavaScript skills in both bare bones javascript and using JavaScript via a Javascript Framework.  Yes, nodejs works with your favourite framework like JQuery and YUI.

Node has an extensive amount of third party modules


Vibrant Community.
Event loop model.
Code sharing. 
JS Frameworks.
Express cli

####Companies using it:
https://github.com/joyent/node/wiki/Projects,-Applications,-and-Companies-Using-Node





