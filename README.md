Clustered Camel File Consumer
=============================

This example shows how to consume files from a shared directory across multiple JVM instances. It does so by using a shared `inProgressRepository`. In this example, I used Inifinispan, but it could just as easily be a database or any other `org.apache.camel.spi.IdempotentRepository`.

Requirements
------------

- [Apache Maven 3.x](http://maven.apache.org)

Building Example
----------------

Run the Maven build

```
~$ cd $PROJECT_ROOT
~$ mvn clean install
```

Running Camel
-------------

Open up two terminal windows.

Terminal 1:

```
~$ cd $PROJECT_ROOT
~$ mvn -Djava.net.preferIPv4Stack=true -Dorg.apache.camel.examples.clusterInstanceId=instance01 camel:run
```

Terminal 2:

```
~$ cd $PROJECT_ROOT
~$ mvn -Djava.net.preferIPv4Stack=true -Dorg.apache.camel.examples.clusterInstanceId=instance02 camel:run
```

Testing
-------

Copy some files into `$PROJECT_ROOT/target/input`. You should see each of the files picked up by 1 and only 1 of the consumers.
