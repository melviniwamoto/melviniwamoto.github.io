---
layout: essay
type: essay
title: "Intellij-ent design"
# All dates must be YYYY-MM-DD format!
date: 2023-02-09
published: true
labels:
- Coding-Standards
- Intellij IDEA
- ESLint
---
### The creation of a problem

When our journey in programming begins we are taught to add descriptive text to any commands or variables with their purposes.

```diff
- // *Inaccurate Description*
- var wizardOfOz;
+ // *Accurate Description*
+ var manBehindTheCurtain;
```

In practice, however, when the program isn't functioning as-intended we have the impulse to add or remove or rearrange things until we can get it to work but potentially confusing comments can still litter the file.

```js
  // test stuff
  var test = {x:0,y:0,z:0};
  // *Why is test needed as an object?*
```

Having the discipline to stick to the *program* when it comes to much more tedious ideas about spacing or arbitrary symbol placement can downright become an anathema when the file is still in a dynamic state.

---
### Standard Definition

It is only when we return to our work, or when we're finished, that we regret not originally utilizing the [**Coding-Standards**](https://en.wikipedia.org/wiki/Programming_style)--"... *a set of rules or guidelines used when writing the source code for a computer program* ..."--which promote clarity.

Using a text-editing program that can automate or impose these rules on us allows us to quickly and efficiently write code that looks identical to any other produced by the same program and with the same standards.
