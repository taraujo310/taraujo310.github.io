---
layout: post
title: Why I Don’t Like TypeScript
author: Thiago Ururay
image: js-vs-ts.png
comments: false
lang: en
tags:
  [
    'TypeScript',
    'JavaScript',
    'Type Checking',
    'Programming Languages',
    'Opinion',
  ]
---

## The Problem

Recently, I saw a tweet on X explaining why the `Object.keys()` method has a return type of `string[]` in its TypeScript signature.

In other words, an object in TypeScript should have all of its properties with known types. But there are situations where it is possible to add unknown properties to an object. Since it cannot be certain about the presence of unknown properties, TypeScript adopts a defensive position to handle these cases.

I don’t judge this defensive stance, since it is well known that in any software we need to evaluate trade-offs and make decisions that best align with its goals.

Another user questions why TypeScript does not follow the default behavior already defined by JavaScript, allowing strings as keys by default. After all, with TypeScript, a developer could enforce stricter typing if they wanted to. That is the central question of the debate.

<div class='twitter-element'>
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">The annoying part that isn&#39;t explained is why disallow using string as index signature for objects? <br><br>If you can&#39;t tell if object has hidden keys, then allow string indices by default.<br><br>If users want more rigid types they can cast to them.</p>&mdash; 𝕃𝕏𝔼 • e/acc (@lxe) <a href="https://twitter.com/lxe/status/1819062897936683272?ref_src=twsrc%5Etfw">August 1, 2024</a></blockquote>
<p class='twitter-caption'>
  Element implicitly has an `any` type because expression of type `string` can’t be used to index type `{ a: number; b: number; }`.<br />
  No index signature with a parameter of type `string` was found on type `{ a: number; b: number; }`.
</p>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

## Why Is JavaScript Dynamically Typed?

Here on this blog there is another article defining what type checking is, dynamic typing, static typing, and the pros and cons of each. If you are not familiar with these concepts or their trade-offs, I recommend taking a look before continuing.

Taste is subjective — everyone has their own opinion. It’s a matter of personal preference. But it’s important to recognize that dynamic typing offers greater flexibility, which can be advantageous in certain contexts.

When JavaScript was designed, internet connections were slow and unreliable, and any interaction with a page required a full page reload. Imagine filling out a form, submitting it, waiting minutes for a response (and even risking losing the connection — and consequently your data) just to discover that something was invalid.

To solve this, Netscape decided to create a scripting language that would allow interaction with web pages directly in the browser. Thus Mocha was born, later renamed to LiveScript, and eventually JavaScript.

JavaScript was designed to be a language that:

- could interact with the DOM tree, which is highly dynamic;
- was easy to read and write, even for inexperienced programmers;
- was simple, enabling quickly written code;
- could be interpreted by the browser (i.e., without compilation);
- was very tolerant of programmer mistakes.

These goals align with dynamic typing, since it results in simpler, more concise, easy-to-read and easy-to-understand code that handles changing structures (like the DOM tree) very well — in addition to not requiring a compilation process.

## Why Use TypeScript (or Another Type Checker)?

Over time, websites became larger and more complex. Developers began looking for alternatives that would:

- reduce the possibility of runtime errors (by catching them beforehand);
- provide features like autocomplete and code navigation, which are facilitated by type bindings;
- make explicit how different parts of the code integrate with each other;
- enforce the architecture of complex systems, preventing human errors (especially from junior developers).

## Understanding the Current Software Market

TypeScript’s popularity has grown significantly in recent years — and that makes perfect sense. Over the last decade, we have experienced economic crises and the rise of remote work. There has been a significant increase in courses selling the illusion of short-term financial gains and, as a result, many people saw software development as a way to improve their personal finances and migrated into the field. This resulted in the entry of many inexperienced programmers and the need to protect software from human error.

At the same time, software systems have become increasingly complex, requiring greater robustness and performance — something that static typing tends to provide a stronger sense of safety for.

Although these are valid reasons for adopting a statically typed language, I often see less compelling arguments focused purely on personal preference or solely on error prevention.

## TypeScript vs JavaScript

To discuss this with proper grounding, I will briefly compare TypeScript and JavaScript and then explain why I tend to avoid choosing TypeScript, if possible.

TypeScript:

- Transpiles code to JavaScript, where there is no type definition. Therefore, the entire type system disappears at runtime, losing guarantees of error prevention;
- Is a superset of JavaScript and therefore its performance can only be as good as JavaScript itself;
- Remains a dependency to be managed, which can generate version conflicts, maintenance overhead (breaking change hell), increase project size, etc. Managing dependencies requires time and resources;
- Often leads to more bureaucratic code due to static typing, increasing verbosity, especially in smaller projects or those with less complex requirements;
- Although it prevents syntax and semantic errors, it does not prevent logical errors. For that, other techniques are required such as unit and integration tests, following style conventions using linters, actively maintaining documentation, having CI/CD configured, among other practices that are already standard in dynamic language communities.

## Conclusion

In other words, the advantages of TypeScript are primarily about developer experience. That is, it enhances language tooling (classes, types, interfaces, etc.), improves editor capabilities (automatic refactoring, autocomplete, etc.), and embeds documentation directly in the code (variable declarations explicitly state their type and function signatures clearly define parameter and return types). These advantages are excellent for large teams, highly complex projects, and teams with inexperienced developers. But TypeScript does not truly have the advantages of a statically typed language at runtime.

On the other hand, it restricts JavaScript’s flexibility (one of the language’s main characteristics), while still requiring the same best practices used in dynamic languages. And it introduces the need to allocate time and resources to manage it as a dependency.

Unless it is a large, complex project with many developers — or geographically distributed teams — or inexperienced developers, I don’t see a real need to use TypeScript.

## References

- [TypeScript vs. JavaScript: Your Go-to Guide](https://www.toptal.com/TypeScript/TypeScript-vs-JavaScript-guide)
- [Brendan Eich - JavaScript at 20 - BrazilJS 2015](https://www.youtube.com/watch?v=bM79WQ9iMZQ)
- [A Trip Back in Time: the History of JavaScript](https://softteco.com/blog/history-of-JavaScript)
