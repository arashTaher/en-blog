---
author: arashthr
comments: true
date: 2012-08-12 20:30:06+00:00
layout: post
title: 'Prolog : How to implement if-then structure'
categories:
- Programming
tags:
- Concept
- Programming
- Prolog
---



How to implement if-then-else in prolog ?
This was a question posted on stack overflow and I though it might be good to say a few words about ot in here.

There is nothing as if or else in a logical programming languages, all you have is some stupid rules and facts :) and you job as a programmer in this environment is not to tell the language how to do the thing ( if foo then bar ), but to describe the problem. You state some facts, establish some rules and based on that ( unification ) the language interpreter will search and find the solutions for any given problem that fits into your description ( backtrack ).

Suppose we want to find the union of two sets . How do we make decisions ? let's see :

{% highlight prolog %}
union( [], X, X ).
union( [H|T], X, List ) :- member( H, X ), union( T, X, List ), !.
union( [H|T], X, [H|List] ) :- union( T, X, List ).
{% endhighlight %}


You can see we did not use conditions, we just setup different ruls for different conditions.

As another example take a look at this code . In here we want to exclude all the elements of the first list from the second one. We have no condition :

{% highlight prolog %}
diffLst( _, [], [] ).
diffLst( [], X, X ).
diffLst( [H|T], [H|Rest], Result ) :-
  diffLst(T, Rest, Result). % Ignore same items
diffLst( Exc, [I|Rest], [I|Result] ) :-
  [H|_] = Exc, H > I, diffLst( Exc, Rest, Result ).
diffLst( [H|T], Inc, Result ) :-
  [I|_] = Inc, H < I, diffLst( T, Inc, Result ).
{% endhighlight %}

That's the stuff, isn't it ?
