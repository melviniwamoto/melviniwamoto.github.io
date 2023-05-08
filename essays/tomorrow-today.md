---
layout: essay
type: essay
title: "Writing for tomorrow, today."
# All dates must be YYYY-MM-DD format!
date: 2023-04-27
published: true
labels:
- javascript
- Meteor
---
#### Speaking in tongues

Understanding others can be troublesome when there are language barriers, but it can be even more pronounced if someone uses idioms you're unfamiliar with; "What do you mean the early bird catches the worm?  Which bird?"

Now imagine that the speaker you're listening to isn't even necessarily being intelligible in that language.

That is what it is like, sometimes, while reading my own work.

This is why I try to provide enough context to myself, or anyone else for that matter, about what I was trying to accomplish and there are certain things that we do in programming which can alleviate that very human struggle of trying to understand yourself.

---
## Paradigm-a-dozen

In the context of *work* the prospect of repeating the same laborious tasks over and over is what leads to innovation, like in the case of power tools.

In programming, we have a unique opportunity to create these innovations ourselves and it is greatly encouraged because of how *frequently* we encounter these repeating *patterns*.

The first time many of us are made to be aware of this, in our specific context, is in the phrase "Don't Repeat Yourself" (DRY).

> *Typical case of repeating patterns:*
> ```js
> const hourlyWage = 15;
> // 20 hours a week
> let weeklyIncome = 20 * hourlyWage;
> // 50 weeks in a year
> let yearlyIncome = 50 * weeklyIncome;
> // ...Do Other stuff...
> weeklyIncome = 40 * hourlyWage;
> yearlyIncome = 50 * weeklyIncome;
> // ...Change things and do it yet again...
> ```
When we see a repeating set of tasks being performed on specific types of data we like to group them up into nice little packages that we call **functions**.

> *Format of a function:*
> ```js
> const functionName = (whatItNeeds) => {
>   // ...esoteric operations...
>   return whatYoudExpect;
> }
> ```

Defining these functions with *semantic* names, or names that describe what it does, is a type of *design pattern* called the ***Facade* pattern** because of how the complexity *behind* it is hidden by the name while still providing context as to it's purpose.

> ```js
> const pickOutfit = (wardrobe, stars, ...etc) => {
>   let chanceOfRain = askAstrologer(stars);
>   chooseCoat(chanceOfRain, wardrobe);
>   // more functions...etc
>   return outfit;
> }
> ```

*Sets* of functions can also repeat so we simply create higher-level functions, and so-on.

---
### Seeing the trees in the forest

Collecting repeating and related sets of *data* into a new entity is called **object creation**.

> ```js
> const treeHeightA = 19;
> const treeAgeA = 14;
> const treeHeightB = 34;
> const treeAgeB = 22;
> // more data...etc
> // The data grouped up as an object
> const treeA = {
>   height: 19,
>   age: 14
> }
> // more objects...etc
> ```

The result of applying facade to object creation is called *classes* and tidily encapsulates the central philosophy behind *Object-Oriented Programming*.

The **Class** hides the unwieldy creation of objects behind a special type of *function* called a **Constructor**.

*Example Class:*

> ```js
> class Tree {
>   // Hidden behind the class
>   constructor (height, age, ...etc) {
>       this.height = height;
>       this.age = age;
>       // tree data...etc
>   }
>   // ...etc
> }
> // Cleaner object-creation afterward
> const treeA = new Tree(19, 14, ...etc);
> // more trees...etc
> ```

Objects can perform varying functions; a tree might have a vast amount of them, including a *grow* function that adds to it's height and age.

Functions devoted to changing the *content* of the data of **objects of a *class*** are called **methods**.

These include *helper*-methods that aren't defined *inside* the class itself but still help other parts of the program to somehow interact with them.

*Example Methods:*

> ```js
> class Tree {
>   constructor (...) {...}
>   // Methods
>   // Accept a hug
>   getHug(huggerName) {
>       // Add to list
>       this.friends.push(huggerName);
>       // operations...etc
>       return this.deepConnection;
>   }
>   // more member-methods...etc
> }
> // Helper-Methods
> const plantGrove(groveData) {
>   // make like of new trees...etc
>   return grove;
> }
> // helpers...etc
> // *Finally using them far below*
> const myTree = new Tree(...);
> const neighborsTree = new Tree(...);
> const nearbyGrove = plantGrove(...);
> ```

Increasing the complexity of these classes eventually crowds the file to the point where separating them from the files that use them becomes necessary to preserve readability.

The **module pattern** presumably arose from this need and allows these ***modules*** to be *exported* from their files and *imported* into multiple files.

Exporting *tree.js*:

> ```js
> export class Tree {...}
> export const plantGrove(...) {...}
> // helpers...etc
> ```

Exporting *veryLongClassName.js*:

> ```js
> class VeryLongClassName {...}
> const veryLongHelperName(...) {...}
> // ...etc
> // *Bottom of the file*
> export {
>   VeryLongClassName as ShortClassName,
>   veryLongHelperName as shortHelperName,
>   // ...etc
> }
> ```

Importing into *myProgram.js*:

> ```js
> // The top of the file
> import Tree from '/path-to-file/Tree.js';
> // interact with user...etc
> const myTree = new Tree(...);
> // ...etc
> ```

---
### *Not* more than meets the eye

An intended side-effect of segregating the module when it is complete is that it becomes protected from any temptation to *transform* it across it's uses; providing fixed and understandable expectations from them and forcing us to use them *as-is*.

```js
// A function that does "this"
export const doThis(...) {
  // does "this"
  // also does "that"
}
// without renaming and updating comments
// usage may lead to confusing results
```

The power wielded when actively developing a program can tempt us to to expand method functionality or to intertwine classes that commonly interact in an attempt to streamline and automate processes.

*Coupling objects*, however, can lead to asymmetrical responsibilities and hidden interactions that are hard to trace.

*Strongly-coupled* objects:

```js
class Tail {
  constructor(...) {...}
  // Changes the data of other objects
  wag(dogObject) {
    // error trying to access method of a null object
    dogObject.mind.boggle();
  }
  // ...etc
}
```

```js
class Dog {
  // Class data was changed over time
  constructor(...) {...}
  // Relies on data from a single input
  chase(tailObject) {...}
  // ...etc
}
```

In big enough classes, finding bugs inside complex high-level method calls can be nearly impossible, especially if changes are coming from *outside*.

Ultimately, it is an imperative for our *own* benefit to head-off this frustration by preserving each class' generic state and to limit the level of their coupling.

*tree.js* Class:

```diff
  // keep methods generalized
- getPersonHug(personObject) {...}
- getAlienHug(alienObject) {...}
+ getHug(objectOfAffection) {...}
```

When it is *indeed* natural to link several objects together, which often is the case, it is better to either create a higher-level class that is *composed* of other classes or to *extend* classes.

```js
import Engine from '/path/Engine.js';
// ...etc
class Vehicle {
  constructor(...) {
    // =Sub-classes=
    this.engine = new Engine(...);
    this.frontLeftWheel = new Wheel(...);
    // ...etc
    // =Class data=
    // ...etc
  }
  // Methods
  drive(...) {
    if (this.speed >= 88) {...}
    if (this.fluxCapacitor >= 1.21) {...}
    // ...etc
  }
  // ...etc
}
```

**Composition** is a straightforward type of umbrella-object that **owns** the smaller parts of itself; like how a car **has** wheels and an engine.

Conversely, **Aggregation** implies either *extension* or *specification* of an object and specifically does *not* imply ownership; a truck **is** a vehicle, and a car **is** a vehicle, and neither **has** a vehicle.

```js
import Chair from '/path/Chair.js';
Bench extends Chair {...}
Throne extends Chair {...}
Toilet extends Throne {...}
// ...etc
```

Aggregation and extension have an implicit functionality distinct from composition: the constructor of the extended **parent** class is called when the new **child** class' constructor is used, causing the child to **inherit** everything the parent *is* and *does*.

```js
import Tooth from '/path/Tooth.js';
// ...etc
Dinosaur extends Tetrapod {
  constructor(...) {
    // Parent gives it's data (from elsewhere)
    // Use whats needed, make whats missing
    this.jaw = fillTeeth(new Tooth('scary'));
    // ...etc
  }
  // Parent gives it's methods
  // Child methods are defined here
  scareParkGoer(...) {...}
  // ...etc
}
fossilize(...) {
  // use deeply inherited data
  const fossil = tryMakeFossil(dinosaur.body);
  return new TestFromGod(fossil);
}
// ...etc
```

---
## Seeing the forest through the trees

When we can be *absolutely* sure of the existence of a rigid set of functionalities--a bare *minimum* of capabilities--they are called **interfaces**.

A rigid set of attributes--symmetrical sets of data--are called **abstract classes** and can also have an interface;

Technically, javascript doesn't even explicitly support them and they aren't included as important keywords like **class** or **export** because objects in javascript can actually be transformed to satisfy interface and abstract requirements.

Simply conforming with "best-practices", however, at every level of development should always ideally result in the production of generically-composed, *abstract*, classes.

Development should cease when the classes either have sufficient data to represent the concept, or have sufficient methods to effectively simulate an act, to minimize the complexity in actually finally creating concrete objects of the class.

```js
const name = 'batman';
// Done! Only needed a name
```

But implementing specific types of complex classes can become a lot to manage, and repetitive, when many parts of it need to be configured in specifically different ways; like how various *breeds* of dogs have distinct *forms* though they've remained the same *species*.

You could end up with *nearly*-identical helper-methods that all use the same sets of data in different ways or combinations 

```js
class Tree {...}
// helper-methods
const treePlanter ()
```
### EXPLAIN FACTORY