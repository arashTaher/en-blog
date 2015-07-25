---
author: arashthr
comments: true
date: 2013-08-10 09:59:10+00:00
layout: post
slug: practitioner
title: Practitioner
wordpress_id: 317
categories:
- Articles
- Computer Topics
tags:
- Bugs
- Open source
---

Yesterday, I was finally honored to contribute to an open source project, NRefactory: Front-end parser for C#.
Although, I have to admit I was only a helper through this journey; In fact at first I was totally reluctant to dive into thousands lines of code. After all, it’s still a bit scary ![:)](https://s0.wp.com/wp-includes/images/smilies/icon_smile.gif)
Anyway we did it, we found the problem and add our short piece of modification into the code.

But what was the dilemma ? The problem was an ambiguity in resolution when we had an object with same name as class name. In order to disambiguate it, parser looks to see whether method has a static modifier or not. Now, when we try to call an extension method from an object … Poof ! Parser thinks this object is the class and …

Well, all we had to do was to add another condition to check whether it’s an extension method or not. I was so thrilled and I impatiently wanted to recompile our program to see the results. But wait ! “Let’s not rush into it”, said the other guy. “First let’s to see what are it’s side effects.” We checked every occurrence of this method in the code to make sure this change doesn’t cause any malfunction. After that we ran the program and … it was working like a charm.

PS : Soon I’m gonna post a share about [NRefactory ](http://arashthr.wordpress.com/2013/08/10/332/)library and how I’m using it in developing an aggressive obuscator for C#. So be prepared !
