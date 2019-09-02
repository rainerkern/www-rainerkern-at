# One-Day Workshop: Introduction to Kotlin

The One-Day Workshop: Introduction to Kotlin is aimed at developers who want to dip their toes into the waters of Kotlin programming. The course is suitable for almost all skill levels. It is helpful - tough not necessary - if you are able to answer the following questions:

What is Java?

- A Coffee Brand
- An Island
- A Programming Language

Have you ever used IntelliJ?

* Yes, a lot
* Yes a little
* No

What is the difference between Git Push and Commit?

What is the difference between Git Pull and Fetch?

What is the name of the main Maven Configuration file?

What is the name of the main Gradle configuration file?

Which statements are generally named “control-flow” statements?

* If, Else, Case
* Class, Void, String
* For, While, Until
* Print, Println, Log
* Return, Continue, Break
* Try, Catch, Throw
* Public, Protected, Private

What is the difference between a variable and a data type?

How do you repeat the execution of a statement or block of statements?

What is it called when a function “walks” through a collection?

What is overloading?

* Multiple classes inheriting from the same parent
* Multiple functions with the same name
* When a function returns more than one value

What is the difference between a parameter and an argument?

What is TDD?

What is BDD?

What does Inheritance mean?

What is Spring?

What is Hibernate?

What is JUnit?



## Workshop Agenda

1. Setup Development Environments

   [introduction document](1-introduction.md)

2. Create a Hello World application

3. [kotlin-ktor-client-server github repository](https://github.com/rainerkern/kotlin-ktor-client-server)
   [kotlin-ktor-client-server-log](kotlin-ktor-server.md)

   - Create a small web server
   - Deliver dynamic pages from our webserver
   - Introduce Kotlin Serialization

4. [Advanced World](https://docs.google.com/document/d/1LzRb3Ex7JdlYf_9tQF_Ovq4UYk9RKU31PLN0zqmvXkI/edit#heading=h.2dv6awdmc6n7) Exercises 1 - 3

5. [Ktor Get Client](https://docs.google.com/document/d/1E_MxduZGCfFTUXjwWktjgxY2WaiwDoUm2pdALzYJFSM/edit#) Authentication token



# Preparation and Introduction

What is Kotlin, Java, JVM?

Kotlin is a relatively young programming language. For execution, Kotlin needs a runtime library called the Java Virtual Machine (JVM). Kotlin is fully interoperable in both directions with the much older Java programming language (Java also needs the JVM to run). This means that Kotlin can make use of all the very mature and useful libraries and tools of the Java ecosystem. Also, Java applications can use classes and libraries developed in Kotlin.So to fully use Kotlin you must also learn at least a little bit about the Java ecosystem.



## Set up the development environment

The Java ecosystem can be a confusing place to new developers which is why in the beginning we focus only on the Java Development Kit (JDK) which you need to develop Kotlin. The JDK includes the JVM which you need to run Kotlin. The JVM does not include the JDK.

Historically, there are different editions of Java (JRE and JDK)
Standard Edition (Java SE) , Enterprise Edition (Java EE) , Micro Edition (Java ME) JavaFX...

Every edition provides special functionality for different use cases. For now, you only need the development Kit for the Java Standard Edition (Java SE JDK). You can download either the Oracle JDK: [java.com](https://www.java.com) or from the Open JDK: [openjdk.java.net](https://openjdk.java.net). Make sure that you really download the JDK, not the JRE.

Software development in Kotlin is preferably done in IntelliJ by JetBrains. As of the time of this writing, IntelliJ has the best support for the Kotlin language. There are pro and free versions available so there is no financial barrier to using this software.



## Running Your First Hello World Program

If your machine is already set up, you can watch video 1 and 4 below to create your Hello World program. However, if you have any questions in the previous topics or you would like to reinforce them, we recommend watching the videos from 1 to 4.



## Watch video series

1. [Welcome (video by HackerSploit)](https://www.youtube.com/watch?v=pDqlF9F58Cg&list=PLBf0hzazHTGPM-NepYUuidHmcxej2zR4l&index=1)

2. [Installing Java JDK (video by HackerSploit)](https://www.youtube.com/watch?v=e4jMSMW5LaA&index=2&list=PLBf0hzazHTGPM-NepYUuidHmcxej2zR4l)

3. [Installing IntelliJ (video by HackerSploit)](https://www.youtube.com/watch?v=f2hPuBg5Bn0&list=PLBf0hzazHTGPM-NepYUuidHmcxej2zR4l&index=3)

4. [Running Your First Program (video by HackerSploit)](https://www.youtube.com/watch?v=VG77blIBxe4&list=PLBf0hzazHTGPM-NepYUuidHmcxej2zR4l&index=4)



## Exercise Tasks

#### 1. Write a Kotlin program `TopMovies.kt` printing this output:

```
Top 3  Movies:
1. Avengers Infinity War
2. Venom 
3. Solo: A Star Wars Story
```



#### 2. Write a Kotlin program `JumpOneLine.kt` printing this output

```
++++++

@@@@@@

******

######
```



## Quiz

1. Who is the creator of Kotlin?
   
   * Google
   
   * Jet
   * Bains
* Oracle
   * Microsoft
   
2. Which kotlin function to send output to the standard output (screen)?
   * echo “Hello World”
   * alert(“Hello World”)
   * output(“Hello World”)
   * println(“Hello World”) or print(“Hello World”)

3. Fill in the blanks:

   ```kotlin
   fun _____(args:_____<String>__ __ 
   ```



## Additional Resources

Language Reference: [Getting Started with IntelliJ IDEA](https://kotlinlang.org/docs/tutorials/getting-started.html)