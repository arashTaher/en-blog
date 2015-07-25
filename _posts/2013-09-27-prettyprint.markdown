---
author: arashthr
comments: true
date: 2013-09-27 20:12:02+00:00
layout: post
slug: prettyprint
title: PrettyPrint C# codes via NRefactory
wordpress_id: 417
categories:
- Coding
- Programming
tags:
- C
- NRefactory
- Parsing
- PrettyPrint
- reformatting
---

Yet another code example via NRefactory. This time we intend to take advantage of reformatting capabilities in NRefactory library.

What does it mean ?  Well, when you become engage in Code generating activities, you usually don't want to be involved in details of code formatting, indentation and these kind of stuff. All you wanna do, is to concatenate some codes, one behind another and create you desired code. After you're done with your code, you may have a program in one line, with no indentation. This is where NRefactory steps in.
It can take your code, and by considering tons of available options, automatically reformat your code. easy peasy !

I have created a rudimentary example of this operation that you can download from [here](http://ge.tt/6JuQk2o/v/3). It's quite simple and straightforward.

PS : I've uploaded binary files in [here](http://ge.tt/6JuQk2o/v/2). In case you already download the previous sample, you don't need to download binary files again. Now all you have to do is to reference to these binary files to be able to build the project.

Oops ! I made an honest mistake and used Formatters. I've applied changes and updated the code.
Formatters are appropriate tools when you want to apply modifications in IDE ( like preserving correct indentation after copy-paste or when IDE fills some fields for you ).
In our case, proper tool would be OutputVisitors. We create parse tree of out code, then visit it by CSharpOutputVisitor and ... Boom !
