---
layout: post
title:  "Imperative to Declarative Javascript"
date:   2017-01-06 2:35:05 -0400
categories: Javascript, Functional Javascript
---

## Imperative To Declarative JavaScript

Trying to incorporate the recently rediscovered functional paradigm into your next JavaScript project? You are not alone. It is easy to get trapped structuring your code in an object-oriented way. It is always hard to move out of our comfort zone and take on something new. For us to remain effective developers, this is what we must do. Live on the edge of our seat and continue to struggle, continue to fail and continue to grow as a developers.

If you are like me, you learned to program in an imperative / procedural style. Constructing your application in a top to bottom flow makes sense. You are solving a problem, constructing your answer in a sequence of procedures. There is one important part of this paradigm that we need to focus on. We need to understand that as we move through steps in our sequence, we will be mutating the state of of our program. The more we add or change the state the less predictable and readable our program can become. If you are a developer by trade, you know that you can spend hours combing through complicated logic to find a bug. Much of this complication can be abstracted away, by using instructions that tell your program what you want, rather than telling your program how to do what you want. Later I’ll provide and example of how to approach this style.

> OO makes code understandable by encapsulating moving parts.
> FP makes code understandable by minimizing moving parts.
>  — Michael Feathers (Twitter)

### Here There Be Imperative Monsters

Let’s look at some of trouble our imperative style can get us into.
Side Effects — Changing values or state outside of the current expected return value. This can make functions harder to reason about. Also, it decreases the chances that the statement / function will be reusable.

<script src="https://gist.github.com/newmanbrad/7b8f0a44d3f45b93e3ec06c3689c9c38.js"></script>

The snippet is causing a side effect by modifying an external variable. This is bad because the value of decrement can be changed at any time by another part of our program. Thus, the output of the decrement function is unpredictable.
Below is a full example illustrating the same problem. Keeping track of what is happening in the example can become difficult for the next developer. Especially if you bury this in a ton of business logic.

Let’s take a look at an imperative code snippet that is not difficult to understand. The program below will print the average grade for courses that have more that 1 student enrolled.

<script src="https://gist.github.com/newmanbrad/64fd9f049b14c9d475fc15c61b8750dc.js"></script>

Looks like this will get the job done. Say that our business requirements have changed and now we need an average number of students. We have some serious refactoring to do. The more we touch code like this example above, the more chances we have for bugs. I will show an example below of the same program in a declarative style.

### No Ring To Rule Them All

I think that is important to understand that Javascript is a multi-paradigm language. That is what makes it so awesome. Combining the imperative and declarative paradigm can be powerful. This is JavaScript’s super power.

> Natural language has no dominant paradigm, and neither does
> JavaScript. Developers can select from a grab bag of approaches — 
> procedural, functional, and object-oriented — and blend them as
> appropriate.
>  — Angus Croll, If Hemingway Wrote JavaScript

### Functional Goodness

Composing declarative Javascript is a different way to solve the same problems we face daily. The benefits to solving problems in the way can be numerous.

<script src="https://gist.github.com/newmanbrad/1f380fe9015edebf1338adeeacbd41c2.js"></script>

We have taken the program from above and broken it down using some functional goodness. Above, I suggested that the business may want a different output from this program. You can see ( line 22 ) I have the ability now to specify which key I would like to pass for an average. Also, notice that the new functions that we have, average and pluck, are reusable and portable. They make no assumptions about what sort of data that is passed in.

Some benefits to the changes above include:

* Easier to test

* Easier to reason about

* Easier to reuse

* Easier to maintain

To make my program more declarative I have used 3 central higher order functions that are used in all functional languages; map, reduce and filter. These functions can be be used to abstract away problematic for loops. Just as we have done in the example above, using these cornerstone functions reduces the complexity of our application. It also makes our code easier for the next developer to figure out what is going on. Using this declarative style will provide your program consistency and predictability.

### Conclusion

Adding some declarative style to your project will allow you to unleash the real power of JavaScript.