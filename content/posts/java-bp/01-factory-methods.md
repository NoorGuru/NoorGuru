---
title: "Java Best Practices 01 | Static Factory Methods Over Constructors"
date: 2021-05-27T00:27:28+03:00
slug: static-factory-methods-over-constructors
aliases: ["/java-bp/1"]
tags: ["Best Practice", "Effective Java"]
categories: ["Java"]
series: ["Java Best Practices"]
hideSummary: false
---

## Static Factory Methods

> Consider using Static Factory Methods Instead of Constructors

The static factory method is a method that returns an instance of the class.

---

## Example

In this example, we will build some HTML elements using Java. Here is the base class.
```java
class HtmlElement {
    private final String tag;
    private final String content;

    public HtmlElement(String tag, String content) {
        this.tag = tag;
        this.content = content;
    }

    @Override
    public String toString() {
        return "<" + tag + "> " + content + " </" + tag + ">";
    }
}
```

Instead of providing a normal constructor, we can provide the `of` static factory method:

```java
class Div extends HtmlElement {
    private Div(String tag, String content) {
        super(tag, content);
    }

    public static Div of(String content) {
        return new Div("div", content);
    }
}
```

So that, we can create new `div`s using this method:
```java
class Demo {
    public static void main(String[] args) {
        final Div div1 = Div.of("Hello, World!");
        final Div div2 = Div.of("Hi, People!");

        System.out.println(div1);
        System.out.println(div2);
    }
}
```

Here is the output of the demo above:
```html
<div> Hello, World! </div>
<div> Hi, People! </div>
```

---

## Why?
- Static Factory Methods have names - easier to know and use especially if we have multiple static factory methods VS multiple overridden constructors!
- Static Factory Methods do not require creating a new object each time - you may use some cache or a singleton behavior.
- Static Factory Methods can return an object with a type of sub-class if needed! The constructors cannot.



---

## Why Not?
- Classes with only Static Factory Methods can not be subclassed - unless you added at least one protected or public constructor, you may need to add multiple constructors as well.
- Constructors are easier to be found and highlighted by the IDEs for developers.

---

## Common Names
There are multiple common names for Static Factory Methods, some of them are: `of`, `from`, `create`, `getInstance`, and `valueOf`.

*Read more about this topic from our resource below.*

---

## Resources
- Effective Java, 3rd Edition, by Joshua Bloch - [Buy from Amazon](https://www.amazon.com/Effective-Java-Joshua-Bloch/dp/0134685997).