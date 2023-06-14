---
title: "The Right Abstraction"
date: 2023-03-19T20:58:09+05:30
draft: false
---

It’s a very popular saying — abstract it out if you are duplicating it a third time. But when you make duplication the primary trigger for abstraction, it could lead to some problems. You should abstract something only if you have found the right way to abstract it.

Recently, I came across some poor abstractions and decided to investigate their causes. Most of the time, poor abstractions often result from a hasty attempt to eliminate duplication. This usually happens because of 2 reasons.

The first case is when you abstract something without having enough understanding of the problem/context. For example — There are 2 classes bird and plane, and both can fly. If you don’t have enough understanding of the context you may abstract both into flying things. This will do more harm than good.

The second case is when there is a good abstraction. But then the requirements change and there is friction to rewrite the abstraction. For example you have a an abstraction birds that abstract out the flying property. Later you want to add a non flying bird. The current abstraction doesn’t make sense anymore. Now if you don’t refractor your abstraction and add new properties or add more if-else conditions to the already created abstraction that would make the abstraction poor.

When the codebase lacks good abstraction, it gets cluttered with conditional statements on the abstracted code. This makes the abstraction worse as it becomes a place to dump duplicate code that has no proper place elsewhere.

The right abstraction is one that isolates a single responsibility that is agnostic of its users or contexts. It is preferable to keep the duplicates until such an abstraction can be identified.
