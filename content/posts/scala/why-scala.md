---
title: "Scala and Functional Programming, Why?"
date: 2018-04-21
weight: 1
slug: "why-scala-and-functional-programming"
aliases: ["/scala/1"]
tags: ["Scala Language", "Functional Programming", "FP", "OOP"]
categories: ["Scala"]
author: "Noor"
draft: false
---

## What is Scala?
> “Scala combines object-oriented and functional programming in one concise, high-level language. Scala’s static types help avoid bugs in complex applications, and its JVM and JavaScript runtimes let you build high-performance systems with easy access to huge ecosystems of libraries”.

This is how  [Scala official website](https://www.scala-lang.org/)  introduces the language to the world. In this blog, I will try to make this introduction some way simpler with a taste of real Scala examples, note that I’m assuming a general knowledge of other object-oriented languages like Java or C# but no functional programming knowledge is ok.

## Scala is object-oriented
Scala is a pure object-oriented language in the sense that every value is an object. It’s even more object-oriented than Java, by that I mean that any value, even integers and doubles are objects! this opens a new world of no-special treatment for primitive values.

## Scala is functional
Scala is also a functional language in the sense that every function is a value. That maybe sounds weird or even crazy, but it opens a whole new world and programming style/paradigm that Scala supports, which is the functional programming world. This is not a place to introduce functional programming style and benefits, but I will mention what help us here. Let’s come back to the fact that every function is a value in Scala, that’s simply mean you can use a function anywhere you can use a value. Ummmm, a function?

### A Method or a Function?
To be closer to understand what the functions are, we want to quickly compare them with methods.

- A method, in general, is a piece of code that does something and attached to a context, i.e, belongs to a class.
- While a function is simply a verb that does something or performs an action.

In Scala, we can generalize (or converts) methods to functions, so we can use them outside the class they belong to!

## Which is better?
The one should not treat OOP and FP as 2 worlds who should use one of them, even that’s possible in some cases, but to combine them both and use each of them when
he/she/they needs to, and that’s exactly why **Scala** is found.

In general, most of the programmers use OOP as the main paradigm and FP when they need to, which in most cases make the code simpler, shorter, and easier to understand and maintain.


Now, let’s start to discuss Scala.

## Why Scala?
### 1. JVM
I will start with you, Java developers, because we share a lot together, we use the same base, yes, the **JVM**.
That’s an incontestable point since JVM is mature enough, optimized enough, and have been in use for over 15 years. You have a guaranteed very easy process to deploy and maintain applications, with a great performance!

### 2. OOP and FP Fusion
The second point, which is that you have the best of both worlds! why should you use Java and stuck to OOP* or use Haskell and stuck to FP while you can get them together? Ok, I know that Java 8 introduced a lot of features to support FP, but that nothing compared to what Scala offers. May this seems to be a normal point for you but believe me, once you start to taste the FP, you cannot go back.


Let’s have a quick example, given a list of numbers, write a function/method that segregates even and odd numbers into 2 new lists.

#### **Java** Solution (Using Imperative Way):

```java
import java.util.ArrayList;
import java.util.List;
public class MainJava {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
        List<List<Integer>> numberGroups = segregateNumbers(numbers);
        List<Integer> evenNumbers = numberGroups.get(0);
        List<Integer> oddNumbers = numberGroups.get(1);
        System.out.println(evenNumbers);
        System.out.println(oddNumbers);
    }
    private static List<List<Integer>> segregateNumbers(List<Integer> numbers) {
        List<Integer> evenNumbers = new ArrayList<>();
        List<Integer> oddNumbers = new ArrayList<>();
        for (Integer number : numbers) {
            if (number % 2 == 0)
                evenNumbers.add(number);
            else
                oddNumbers.add(number);
        }
        ArrayList<List<Integer>> result = new ArrayList<>();
        result.add(evenNumbers);
        result.add(oddNumbers);
        return result;
    }
}
``` 


#### **Scala** Solution (Using Functional Programming Paradigm):
```scala
object MainScala extends App {
  val numberGroups = 0 to 10 partition (_ % 2 == 0)
  println(numberGroups._1)
  println(numberGroups._2)
}
``` 

### 3. Concise Code
That’s actually another point to mention for Java developers, Scala will give you a more concise and short version of your code (some people will refer to Scala as a better Java!), let’s take another example of defining a simple class with basic methods in both languages:

#### **Java** Class:
```java
import java.util.Objects;
public class JavaPerson {
    private final String name;
    private final String id;
    private int age;
    public JavaPerson(String name, String id, int age) {
        this.name = name;
        this.id = id;
        this.age = age;
    }
    public String getName() {
        return name;
    }
    public String getId() {
        return id;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof JavaPerson)) return false;
        JavaPerson javaPerson = (JavaPerson) o;
        return age == javaPerson.age &&
                Objects.equals(name, javaPerson.name) &&
                Objects.equals(id, javaPerson.id);
    }
    @Override
    public int hashCode() {
        return Objects.hash(name, id, age);
    }
    @Override
    public String toString() {
        return "JavaPerson{" +
                "name='" + name + '\'' +
                ", id='" + id + '\'' +
                ", age=" + age +
                '}';
    }
}
```
#### **Scala** Class:
```scala
case class ScalaPerson(name: String, id: String, var age: Int)
```
Yes, that’s it! and actually, the Scala class above explicitly contains even more methods than what I wrote on the equivalent Java one, how great is that?

### 4. A lot of Features!
Scala is a step ahead of Java, just think of lambda expressions on Java 8, (limited) var and type inference on Java 10, and many other (new) Java features. They are in Scala since day 1, with much more use cases for them.

### 5. Statically Typed Language
**Scala** is statically typed. It’s enough for Java, now let’s hit other languages.
Python or Javascript? why those? because they are the most widely used dynamically typed languages.
Wait, what is that mean?
> “Dynamically-typed languages perform type checking at runtime, while statically typed languages perform type checking at compile time. This means that scripts written in dynamically-typed languages (like Groovy) can compile even if they contain errors that will prevent the script from running properly (if at all). If a script is written in a statically-typed language (such as Java) contains errors, it will fail to compile until the errors have been fixed”
-  Oracle

BTW, Groovy is another **JVM** language.

Let’s take this simple example in the three languages, **Python**, **JavaScript**, and **Scala**:

#### Multiply 2 Numbers in **Python**:
```python
def Multiply(num1, num2):
    answer = num1 * num2
    return answer
```

### Multiply 2 Numbers in **JavaScript** (ES5):
```javascript
var multiply = function(num1, num2){
    return num1 * num2;
}
```

#### Multiply 2 Numbers in **Scala**:
```scala
val multiply = (num1: Double, num2: Double) => num1 * num2
```
You see it, the ‘**Double**’ type, that’s mean that Scala will not compile at all if you call this function with non-numbers values! while this is OK for both Python and JavaScript. It's maybe faster not to add that ‘Double’ type (is it?) but you will lose a lot! You may compile this, release your product and there is 1 forbidden use in your codebase that leads to huge bugs! so, keep your self safe and use statically typed language.

### 6. Type Inference!
**Scala** has type inference, that’s mean you still may not include the type of the value and let the Scala compiler infer it for you! just print ```val x = 5``` and you are ready to go!
To be complete, there are some very rare cases where you have to declare the type yourself.

So Scala is statically typed, and you can not write the type yourself, **how amazing is Scala!**

### 7. A Scripting Language!
For Python users, a lot of you like the language to write quick scripts.
And again, Scala can be used as a scripting language! did you read about  [REPL](https://docs.scala-lang.org/overviews/repl/overview.html)?

### 8. Data Science and Big Data Processing
**Scala** is one of the main languages used in the Data Science and Big Data Processing fields. Actually, [Spark](https://spark.apache.org/), one of the most popular engines for big data analytics and processing in Java, Python, R, SQL, and Scala is actually written in Scala, so it's best to use it in Scala!

### 9. Parallel Programming
Scala comes with multiple built-in features to support [parallel programming](https://www.bestcomputersciencedegrees.com/faq/what-is-parallel-programming/) in which you can use multiple resources (cores) of your computer to run multiple things/processes together or to run one programme in multiple instances so that you can process it faster. There is one course in the resources below that talks about this.

In fact, [Akka](https://akka.io/), another widely used framework in Java, which helps in building powerful reactive, concurrent, and distributed applications more easily in also written in Scala! Doesn't that tell you something about the language?


***… Scala has a lot more to encourage you to choose it as your next journey. I can't mention all the reasons in one article, but I guess I mentioned just enough points to let you consider Scala for your next project! ***

**Are you aware of some other reasons to learn and use Scala? Please share them in the comments below!**

## Learn Scala with Me
I have a [GitHub repository](https://github.com/mohnoor94/LearningScala)  I use to keep my journey on learning Scala, you may want to check it [here](https://github.com/mohnoor94/LearningScala) :”)

### More Reasons
#### Check these resources for more reasons to choose Scala:

-  [Tour of Scala](https://docs.scala-lang.org/tour/tour-of-scala.html)
-  [Scala vs. Java: Why Should I Learn Scala?](https://www.toptal.com/scala/why-should-i-learn-scala)
-  [Why Scala? (by Martin Odersky, the creator of Scala)](https://www.lightbend.com/blog/why-scala)
-  [Why Scala? (for Spark)](https://medium.com/@natekupp/why-scala-23e62c2b9c8)
-  [Why should I learn Scala?](https://www.quora.com/Why-should-I-learn-Scala-How-is-it-different-unique-better-than-other-languages-Are-there-operations-which-can-only-be-performed-in-Scala-How-fast-is-it-compared-to-Java-Haskell-Clojure-Lisp-etc)
-  [This is why you should learn Scala](https://www.pluralsight.com/blog/software-development/how-to-use-scala)
-  [Why should I learn Scala?](https://www.reddit.com/r/scala/comments/3gd1d3/why_should_i_learn_scala/)
-  [Make 2017 The Year You Learn Scala](https://medium.com/@markcanlasnyc/scala-saturday-make-2017-the-year-you-learn-scala-6ec330847be5)
-  [A Newbie’s Guide to Scala and Why It’s Used for Distributed Computing](https://blog.insightdatascience.com/a-newbies-guide-to-scala-and-why-it-s-used-for-distributed-computing-979070a9f8)

#### More resources to learn Scala:
- My [GitHub repository](https://github.com/mohnoor94/LearningScala). **Free**.
- [Rock the JVM](https://rockthejvm.com/)
- [Functional Programming Principles in Scala](https://www.coursera.org/learn/progfun1) by Martin Odersky, the creator of Scala. **Free Course**.
- [Functional Program Design in Scala](https://www.coursera.org/learn/progfun2) by Martin Odersky, the creator of Scala. **Free Course**.
- [Parallel programming in Scala](https://www.coursera.org/learn/parprog1) **Free Course**.
- [Programming in Scala](https://www.amazon.com/Programming-Scala-Updated-2-12/dp/0981531687) **Book**.
- [Scala Programming for Data Science](https://cognitiveclass.ai/learn/scala/#course2000) **Free Course**.
- [Scala for Java Developers](https://www.apress.com/us/book/9781484231074) **Book**.
- [More resources](https://github.com/mohnoor94/LearningScala/blob/master/README.md).


See you in the next one!
