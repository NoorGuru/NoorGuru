---
title: "Solid Design Principles with Java – #01 Single Responsibility Principle (SRP)"
date: 2019-03-30
draft: false
slug: single-responsibility-principle-java
tags: ["Design Principles", "Lecture"]
categories: ["Java"]
series: ["solid-design-principles"]
aliases:
    - /java/1
showToc: true
weight: 2
---

## Solid Design Principles with Java Series
Welcome to this new series of solid design principles with Java programming language.

In this series we will focus on the most important design principles, introduce them with minimal efforts on both us
and the reader, this series should be followed by a more advanced one on design patterns with Java later on – stay
tuned!

## Single Responsibility Principle (SRP)

On this first lesson, we will discuss the **Separation of Concerns (SoC)** aka **Single Responsibility Principle (SRP)**.

This is actually a very simple principle, as its name suggests, it means to extract every piece of code logic to its
own class.

For example, you have a class called Journal, you clearly should add it’s content to the class itself, but later on, 
you observed that you need to add a functionality to persist the content of a Journal object to a database, what should
you do? simply you go to your Journal class and add 2 new methods to save and load the contents and here we go – but
hold on!

What if you have another type of classes, say a Book, that obviously need same logic of persistence? what to do?
should you copy and paste your methods from the Journal class? – isn’t this
a [code smell](https://en.wikipedia.org/wiki/Code_smell)?

Let’s think again – why did you add the persistence logic to the Journal class itself? to make things simpler?
– wrong, it starts to complicate things.

You should observe now that the persistence logic has nothing to do with the Journal, so go on and build him a new home,
maybe a util class.

And that’s it, you just separated the logic of persistence code to its own class. And now, anytime you want to update
this code – you will not care about updating it in many places. Congratulations!


### Talk is cheap, show me the code [^1]

```java
package _00_solid_design_principles.single_responsibility;

import java.util.ArrayList;
import java.util.List;

public class Journal {

    private final List<String> entries = new ArrayList<>();
    private static int count = 0;

    public void addEntry(String text) {
        entries.add(++count + ": " + text);
    }

    public void removeEntry(int index) {
        entries.remove(index);
    }

    // DO NOT add persistence logic inside Journal class! 

    @Override
    public String toString() {
        return String.join(System.lineSeparator(), entries);
    }
}
```


```java
package _00_solid_design_principles.single_responsibility;
import _util.exception.NotImplementedException;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintStream;
import java.net.URL;
public class Persistence {
    public void save(Journal journal, String fileName, boolean overwrite) throws FileNotFoundException {
        if (overwrite || new File(fileName).exists()) {
            try (PrintStream out = new PrintStream(fileName)) {
                out.println(journal.toString());
            }
        }
    }
    public Journal load(String fileName) {
        throw new NotImplementedException(); // implement it your way
    }
    public Journal load(URL url) {
        throw new NotImplementedException(); // implement it your way
    }
}
```


```java
package _00_solid_design_principles.single_responsibility;
import java.io.FileNotFoundException;
public class Demo {
    public static void main(String[] args) throws FileNotFoundException {
        Journal journal = new Journal();
        journal.addEntry("I cried today");
        journal.addEntry("I ate a bug");
        System.out.println(journal);
        Persistence persistence = new Persistence();
        persistence.save(journal, "journal.txt", true);
        persistence.load("journal.txt");
    }
}
```

or check the code in [my GitHub repository](https://github.com/mohnoor94/LearningDesignPatterns/tree/master/src/main/java/_00_solid_design_principles/single_responsibility)!






[^1]: [Linus Torvalds](https://www.goodreads.com/quotes/437173-talk-is-cheap-show-me-the-code)