---
author: arashthr
comments: true
date: 2014-03-14 11:04:43+00:00
layout: post
slug: editing-code-whilst-preserving-its-formatting
title: Editing C# AST, Yet preserving its formatting
wordpress_id: 443
categories:
- Coding
tags:
- AST
- C
- formatting
- NRefactory
---

Earlier in one of my [posts](http://arashtaher.wordpress.com/2013/09/27/prettyprint/), I explained how can you reformat your code using NRefactory library. But, as matter of fact what you really want in your day to day task is not reformatting code, au-contraire, you want its formatting to be preserved. You don't want to commit dozens of files to your repository merely because their formatting's changed !

Now this question arises that whether is this quest possible in NRefactory or not ? Well of course it is, and it's really easy. ( Once you know what you have to do, who you have to call and ... ) BTW, NRefactory is an essential part of SharpDevelop IDE and we don't want our idea to reformat our code every time we use intellisens.

NRefactory has a class that's dedicated to do such and it's called DocumentScript.

Document scripts works by manipulating IDocument objects, which are specialization of string builder class. This class gives you this opportunity to change your document based on text location that were already stored in syntax tree. It also keeps track of latest modification and map them to current document, so you don't have to worry about whether multiple changes on the same document will be applied correctly or not.

{% highlight csharp %}
IDocument document = new StringBuilderDocument("Your code source");
CSharpFormattingOptions policy = FormattingOptionsFactory.CreateAllman();
var options = new TextEditorOptions();

var script = new DocumentScript(document, policy, options);
{% endhighlight %}

Now you can use methods like Replace, Remove, InsertAfter and etc. on you AST. It works with both AST nodes as well as offsets.
[![script](http://arashtaher.files.wordpress.com/2014/03/script.png?w=300)](http://arashtaher.files.wordpress.com/2014/03/script.png)

Beside that, there are some predefined methods on scripts:

{% highlight csharp %}
script.ChangeModifier(declaration, Modifiers.Public);
{% endhighlight %}
