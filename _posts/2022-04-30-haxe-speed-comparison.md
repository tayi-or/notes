---
layout: post
category: haxe
title: how fast is Haxe?
---
Haxe for those who don't know is a programming language that doesn't commonly run as itself. It usually gets transpiled to other languages such as C++, JavaScript or C#.

Of course, different targets will have different speeds. Here's the results from my MacBook Pro M1.

| Target | Runs |
|-|-|
C++|588
Javascript|548
JavaBytecode|387
Java|373
C#|340
PHP|34
Cppia|23
HaxeEval|15
Python|9
Neko|5


Compare these results to other programming languages on a 5950x (HxCPP got a score of 723) here: https://plummerssoftwarellc.github.io/PrimeView/report?id=davepl-1650451626.json
