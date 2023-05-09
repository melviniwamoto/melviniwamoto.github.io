---
layout: essay
type: essay
title: "Writing for tomorrow, today."
# All dates must be YYYY-MM-DD format!
date: 2023-04-27
published: true
labels:
- javascript
- Facade
- Module
- Coupling
- Composition
- Inheritance
- Factory
- Design-Patterns
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

> **Note**: all code is in a *pseudo*-javascript

> *Typical case of repeating patterns:*
> ```js
> // Note: const, var, and let are "keywords"
> // const defines a "constant", unchanging, piece of data
> const hourlyWage = 15;
> // var defines a "variable", changing, piece of data
> var weeklyIncome = 20 * hourlyWage;
> // let is also a "variable"
> let yearlyIncome = 50 * weeklyIncome;
> // *...Do Other stuff...*
> weeklyIncome = 40 * hourlyWage;
> yearlyIncome = 50 * weeklyIncome;
> // *...Change data and do it yet again...*
> ```
When we see repeating sets of tasks performed on specific sets of data we like to group them up into nice little packages that we call **functions**.

> *Normal format of a function:*
> ```js
> // A good description of what it does
> function functionName (input) {
>   let output;
>   // ...operations...
>   return output;
> }
> ```

> *Arrow-Function format represents the same thing:*
> ```js
> // Full descrition, including: purpose, inputs, and outputs
> let semanticName = (whatItNeeds) => {
>   // Good description of variable
>   // *data-types MUST match if defined*
>   let whatYoudExpect;
>   // *...mysterious implementation...*
>   // *...esoteric operations...*
>   // *...and good explanations...*
>   return whatYoudExpect;
> }
> ```

Declaring these functions with *semantic* names, or names that describe what it does, is a type of *design pattern* called the ***Facade* pattern** because of how the complexity *behind* it is hidden by the name while still providing context as to it's purpose.

> ```js
> // Pick an outfit from a wardrobe
> function pickOutfit(wardrobe, stars, ...etc) {
>   // *If you name data semantically, comments are redundant*
>   let chanceOfRain = askAstrologer(stars);
>   let coat = chooseCoat(chanceOfRain, wardrobe);
>   // more sets of functions...etc
>   return outfit;
> }
> ```

*Sets* of functions can also repeat so we simply create higher-level functions, and so-on.

---
### Seeing the trees in the forest

Collecting repeating and related sets of *data* into a new entity is called **object creation**.

> ```js
> var treeHeightA = 19;
> var treeAgeA = 14;
> var treeHeightB = 34;
> var treeAgeB = 22;
> // *more data*...etc
> // *treeA is an OBJECT*
> const treeA = {
>   // *with height-DATA*
>   height: 19,
>   // *and age-DATA*
>   age: 14
>   // *other data*...etc
> }
> // *more objects*...etc
> ```

The result of applying facade to object creation produces *classes* that tidily encapsulate the central philosophy behind *Object-Oriented Programming*.

The **Class** hides the unwieldy creation of objects behind a special type of *function* called a **Constructor** method and uses the keyword **new** when creating *new* objects.

*Example Class:*

> ```js
> // Represents a tree
> // *class is a keyword for a generic "shape" of an object*
> class Tree {
>   // *Creation hidden inside the class*
>   constructor (height, age, ...etc) {
>     // *Shape of the OBJECT*
>     this.height = height;
>     this.age = age;
>     // *other tree data*...etc
>   }
>   // ...etc
> }
> // Cleaner object-creation afterward
> const treeA = new Tree(19, 14, ...etc);
> // *more trees*...etc
> ```

Objects can perform varying functions; a tree might have a vast amount of them, including a *grow* function that adds to it's height and age.

Functions devoted to changing the *content* of the data of **objects of a *class*** are called **methods**.

These include *helper*-methods that aren't defined *inside* the class itself but still help other parts of the program to somehow interact with them.

*Example Methods:*

> ```js
> class Tree {
>   constructor (...) {...}
>   // =Methods=
>   // Accepts a hug, takes name data
>   let getHug = (huggerName) => {
>     // *Note: "this" is a self-referential keyword*
>     // *that refers to the "Tree" from the constructor*
>     // Add name to list
>     this.friends.push(huggerName);
>     return this.deepConnection;
>   }
>   // *more methods*...etc
> }
> // =Helper-Methods=
> function plantGrove(numTrees) {
>   // *make list of new trees*...etc
>   return grove;
> }
> // *more helpers*...etc
> // *Finally using the class far below*
> // *Note: "this.friends" inside the class*
> // *is the same as "myTree.friends" outside*
> const myTree = new Tree(...);
> const neighborsTree = new Tree(...);
> const nearbyGrove = plantGrove(...);
> ```

#### **Note**: For the purpose of illustrative clarity:

- Functions and methods *outside* of a class will use Normal function formatting with the **function** keyword.
- Methods *inside* a class will use Arrow-Function formatting with the **let** keyword.
- *DATA* will be defined with **var**.
- *OBJECTS* and objects of *CLASSES* will be preceded by **const**.

> I'm doing this because **const** is largely preferred over the others
> but seeing const everywhere can obscure these concepts.
> This is all arbitrary, but it means that much of the code in this paper wont actually work if you copy it letter-for-letter: Be warned!

Special helper-methods that aid in the creation of objects are called **Factory** methods, including the Constructor method already mentioned, but can be beneficial when creating many of the same object. 

Increasing the complexity of these classes eventually crowds the file to the point where separating them from the files that use them becomes necessary to preserve readability.

The **module pattern** presumably arose from this need and allows these ***modules*** to be *exported* from their files and *imported* into multiple files, evoking DRY.

Exporting *Tree.js*:

> ```js
> export class Tree {...}
> export function plantGrove(...) {...}
> // helpers...etc
> ```

Exporting *VeryLongClassName.js*:

> ```js
> class VeryLongClassName {...}
> function veryLongHelperName(...) {...}
> // ...etc
> // *Bottom of the file*
> export {
>   VeryLongClassName as ShortClassName,
>   veryLongHelperName as shortHelperName,
>   // ...etc
> }
> ```

Importing into *MyProgram.js*:

> ```js
> // *The top of the file*
> import Tree from '/path-to-file/Tree.js';
> // *interact with user*...etc
> const myTree = new Tree(...);
> // ...etc
> ```

---
### *Not* more than meets the eye

An intended side-effect of segregating the module when it is complete is that it becomes protected from any temptation to *transform* it across it's uses; providing fixed expectations from them and forcing us to use them *as-is*.

```js
// A function that does "this"
export function doThis(...) {
  // *does "this" first*
  return addThatToThis(doThat(...));
}
// *without renaming function, or updating comments,*
// *usage may lead to perplexing results*
// *Note: NOT referring to the "this" keyword*
```

The power wielded when actively developing a program can tempt us to to expand method functionality, or to intertwine classes that commonly interact, in an attempt to streamline and automate processes.

**Coupling** objects, however, can lead to asymmetrical responsibilities and hidden interactions that are hard to grasp and harder to find.

*tightly*-coupled objects:

```js
class Tail {
  constructor(...) {...}
  // Changes the data of other objects
  let wag = (dogObject) => {
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
  let chase = (tailObject) => {...}
  // ...etc
}
```

In small classes strong-coupling makes finding bugs inside method calls nearly impossible, especially if changes are coming from *outside*, and causes readability to suffer because of the need to read two or three files at the same time. 

Ultimately, it is an imperative for our *own* benefit to head-off this frustration by preserving each class' generic state and functions as much as possible; this is called **loose-coupling**.

*tree.js* Class:

```diff
  // Aliens might hug trees, as well
- let getPersonHug = (personObject) => {...}
- let getAlienHug = (alienObject) => {...}
+ let getHug = (objectOfAffection) => {...}
```

When it is *indeed* natural to link several objects together, which often can be the case, it is better to either create a higher-level class that is *composed* of other classes or to *extend* classes.

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
  let drive = (...) => {
    // If speed is high enough, then do...
    if (this.speed >= 88) {...}
    if (this.fluxCapacitor >= 1.21) {...}
    // ...etc
  }
  // ...etc
}
function stowAlmanac(...) {...}
// ...etc
```

**Composition** is a straightforward type of umbrella-object that **owns** the smaller parts of itself; like how a car **has** wheels and an engine.

Conversely, **Aggregation** implies either *extension* or *specification* of an object and specifically does *not* imply ownership; a truck **is** a vehicle, a car **is** a vehicle, and neither **has** a vehicle.

```js
import Chair from '/path/Chair.js';
class Bench extends Chair {...}
class Throne extends Chair {...}
class Toilet extends Throne {...}
// ...etc
```

Aggregation and extension have an implicit functionality distinct from composition: the constructor of the extended **parent** class is used when making new **child** classes causing the child to **inherit** everything the parent *is* and *does* and *needs*.

```js
import Tooth from '/path/Tooth.js';
// ...etc
class Dinosaur extends Tetrapod {
  constructor(...) {
    // *this.body is defined in some distant PARENT*
    // *Use and change whats needed, make whats missing*
    this.jaw = fillTeeth(new Tooth('scary'));
    // ...etc
  }
  // *CHILD methods are defined here*
  let scareParkGoer = (...) => {...}
  // ...etc
}
function fossilize(...) {
  // use distantly-inherited parent data
  const fossil = tryMakeFossil(dinosaur.body);
  return new TestFromGod(fossil);
}
// ...etc
```

---
## Seeing the forest through the trees

When we can be *absolutely* sure of the existence of a rigid set of functionalities--a bare *minimum* of capabilities--they're called **interfaces**.

Similarly, absolute surety of rigid sets of attributes--symmetrical sets of data--are called **abstract classes** and can also have related interfaces;

Simply conforming with and reapplying these ideas, at every level and in every stage of development, should ideally *always* produce generically-composed *abstract* classes.

Concretely defining them to take a specific *shape*, consequently shedding it's generalities, can become a lot to manage when the many parts of it each themselves require their own specific shapes to be configured in uniquely different ways.

Modeling various *breeds* of dogs--with distinct *shapes* though they remain the same *species*--could produce *nearly*-identical helper-methods for each distinctive breed's **shape**, and might even be nearly-identical to other species of the same *genus*.

The **factory pattern** can be applied to consolidate the different factory *methods*, or class constructors, into a single function or object that handles the creation of *all* the concretely-defined "descendants" of an abstract class based on either object characteristics, external conditions, or both.

```js
// *Inheritance strongly-couples classes by-design*
class MeasuringStick extends Stick {...}
// *the above class is still abstract*

// An external condition
var frameOfReference = ...;

// Factory-pattern method
// *factory and abstract are strongly-coupled*
function rulerFactory (rulerType, data, ...) {
  // Concrete-Definitions: MeasuringStick-Types
  const yardStickData = {...}
  // ...etc
  // *Where the rubber meets the road*
  const measuringStick;
  if (rulerType === 'yard-stick') {
    // *build "descendent"*
    measuringStick = new MeasuringStick(yardStickData);
  }
  // ...etc
  if (nearSpeedOfLight(measuringStickData)) {
    // *mutate "descendent"*
    specialRelativity(frameOfReference, measuringStick);
  }
  return measuringStick;
}

// *Give it a way to identify _which_ type to make*
// *and give it any more information it needs*
const myYardStick = rulerFactory('yard-stick', '0.9c', ...);
```

Factory methods can be composed of other lower-level factory methods to further *delegate* the creation processes of each of the complex-objects' parts, once again applying *facade*.

The factory pattern conforms to most of--if not all--the other patterns I've outlined and exemplifies a treasured occurrence that I've been consistently referring to, but failing to define: a *design pattern*.

---
### Pattern-seeking

As stated, a **design pattern** combines every relevant *best-practice*, or ***standardized principles maximizing efficiency and clarity***, within itself and within it's parts.

It solidifies itself as a design *pattern* when many people, commonly through applying best-practices, come to the *same* shape or form--of an object or function--for the same *purpose*.

In any effort to expand our vocabularies we often only search for the definition of a word when confronted with one we don't understand, so not wanting to pour over dictionary-definitions of design patterns is understandable.

Whether or not you personally adhere to my specific set of *principles* and apply the same *patterns* you can see how utilizing them--after being made aware of them--can minimize the amount of frustration and time spent in-development and can maximize efficiency and clarity of purpose *as a matter of course*.

We all work in our own ways and modify our protocols to suit the context and our needs but some *wants* remain constant--the desire to understand, to be understood, and to understand *yourself*--and using these design patterns in programming is what helps *me*.
