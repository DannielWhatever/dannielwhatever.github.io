---
layout: post
title:  "Strategy pattern"
date:   2019-03-23 13:10:05 -0400
categories: architecture designpatterns
---

*Wena Cabres!
 There was a lot of time that i didnt write about patterns, principles or stuff like that, the last time was about SOLID. You can figure out. But im recovering from a hangover and i read in my feed something about strategy pattern, so, that was like i know about this, but i dnt even remembered that i used to knew it. So... talk is cheap, start walking.*

#### TL;DR

"Essentially, the strategy pattern allows us to change the behavior of an algorithm at runtime." (taken from [Baeldung](https://www.baeldung.com/java-strategy-pattern)) .-


#### Use cases

For simple understandment, when you have a math problem, this have just one correct answer (or not jeje), but there is a lot of different ways to achieve this result. So, you could code different implementations to resolve the problem, and the strategy pattern allows you to easily change between the implementations.

You could use this pattern in different problems, for example:
- Implement different ways to call a backend
- Change between different algorhitms for compression


#### A picture is worth a thousand words (stoled obvs)

UML From wikimedia:
![alt text](https://upload.wikimedia.org/wikipedia/commons/4/45/W3sDesign_Strategy_Design_Pattern_UML.jpg "from wikimedia")

#### How it looks in code

[in github :p](https://github.com/DannielWhatever/dessign-patterns-js/blob/master/strategy-pattern/strategy.js)

An interface:
{% highlight javascript %}
class FindStrategy {
    find(collection, predicate) { throw new Error("this is so abstract!")}
}
{% endhighlight %}

And possible different implementations:

{% highlight javascript %}
class FindWithLodash extends FindStrategy{
    find (collection, predicate) {
        return _.find(collection, predicate);
    }
}
{% endhighlight %}

{% highlight javascript %}
class FindWithVanilla extends FindStrategy{
    find (collection, predicate) {
        return collection.find(predicate);
    }
}
{% endhighlight %}



Select the strategy:

{% highlight javascript %}
const selectedStrategy = process.env.FINDSTRATEGY || 'FindWithLodash';
const finder = new strategiesToFind[selectedStrategy]

const result = finder.find(users, predicate);
{% endhighlight %}

#### Keep reading!

- https://en.wikipedia.org/wiki/Strategy_pattern
- https://www.baeldung.com/java-strategy-pattern
- https://dzone.com/articles/design-patterns-strategy

