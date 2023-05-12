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

When our journey in programming begins we are taught to add descriptive text to any functions or variables.

In practice, however, when the program isn't functioning as-intended we have the impulse to add or remove or rearrange things until we can get it to work.

Having the discipline to stick to the *program* for the more tedious aspects can become an anathema.

---
### Standard Definition

It is only when we return to our work, or when we're finished, that we regret not originally utilizing the [**Coding-Standards**](https://en.wikipedia.org/wiki/Programming_style)--"... *a set of rules or guidelines used when writing the source code for a computer program* ..."--which promote clarity and readability.

Using a text-editing program that can automate or impose these rules allows everyone to quickly and efficiently write code that all look identical without the combined parallel effort it would require to do so, otherwise.

Having identical formats allow us to densely pack our work with certain concepts implicitly, *between-the-lines*.

#### Tall, small, and justRight

```js
var inonecase = 'harder-to-read';
const CapitalizingObjects = {
  distinguishes: 'what-they-are',
}

function badlySpaced(){isHarderTo(read,fix);}

function isEasierToRead (withSpacing) {
  if (linesAreIndented) {
    // You can see
    whatIs(inside);
  }
  // and, at a glance,
  whatIs(outside);
}// And symbol-placement can
// relate it to its "function"

// Spacing lines apart can
imply(relationships);
andLogical(groupings);
```

There are rules that concern themselves with **white-space**--spaces between symbols and between lines--to enable either easier reading or to illustrate relationships.

Others focus on **casing**--whether a letter should be upper-case or lower-case--for names of variables and objects to imply their uses or what they are.

Some can be particular to languages, but all simply are arbitrary patterns to follow to help us to quickly understand the intent of the author.

---
## Easy mode

[intellij IDEA](https://www.jetbrains.com/idea/) is an Integrated Development-Environment (IDE), which is simply a *compiler*--performs a process to turn *source* code into instructions the machine can understand--combined with a text-editor.

This editor, with the help of an automated *reader*, [**ESLint**](https://eslint.org/), can identify certain "problems" in a file with regard either to the rules of a coding-standard or other issues with efficiency and format.

The program can be personally configured to handle individual aspects of coding-standards or together as a pre-configured group.

Being able to ignore standards while still, mostly, adhering to one has given me the opportunity to be lazy and intellij together with ESLint combine to be *the* best IDE-experience I've ever had and I will continue to use them whenever possible.
