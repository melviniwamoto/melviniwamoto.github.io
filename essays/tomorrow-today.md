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
### Speaking in tongues

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
> class tree {
>   // Hidden behind the class
>   constructor (height, age, ...etc) {
>       this.height = height;
>       this.age = age;
>       // tree data...etc
>   }
>   // ...etc
> }
> // Cleaner object-creation afterward
> const treeA = new tree(19, 14, ...etc);
> // more trees...etc
> ```

Objects can perform a variable amount of functions; a tree might have a vast amount of them, including a *grow* function that adds to it's height and age.

Functions devoted to changing the *content* of the data of **objects of a *class*** are called **methods**.

These include *helper*-methods that aren't defined *inside* the class itself but still help other parts of the program to somehow interact with them.

*Example Methods:*

> ```js
> class tree {
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
> // Finally using them far below
> const myTree = new tree(...);
> const neighborsTree = new tree(...);
> const nearbyGrove = plantGrove(...);
> ```

Increasing the complexity of these classes eventually crowds the file to the point where separating them from the files that use them becomes necessary to preserve readability.

The **module pattern** presumably arose from this need and allows these ***modules*** to be *exported* from their files and *imported* into multiple files.

Exporting *tree.js*:

> ```js
> export class tree {...}
> export const plantGrove(...) {...}
> // helpers...etc
> ```

Exporting *veryLongClassName.js*:

> ```js
> class veryLongClassName {...}
> const veryLongHelperName(...) {...}
> // ...etc
> export {
>   veryLongClassName as shortClassName,
>   veryLongHelperName as shortHelperName,
>   // ...etc
> }
> ```

Importing into *myProgram.js*:

> ```js
> // The top of the file
> import tree from '/path-to-file/tree.js';
> // interact with user...etc
> // Usage
> const myTree = new tree(...);
> const nearbyGrove = plantGrove(...);
> // ...etc
> ```

---
### *Not* more than meets the eye

An intended side-effect of segregating the module is that it becomes protected from any temptation to *transform* it across it's uses; providing fixed and understandable expectations from them and forcing us to use them *as-is*.

```diff
// A function that does "this"
export const doThis(...) {
- // does "this"
+ // does "this" and "that"
}
// without renaming or updating comments
// usage may lead to confusing results
```

The power wielded when actively developing a program can tempt us to intertwine classes that commonly interact, especially when they both tend to act together, in an attempt to streamline and automate the process.

*Coupling* classes, however, can lead to a situation where simple mistakes can cause unwanted and hard-to-find--and sometimes dangerous--consequences.

```js
class foot {
  constructor(...) {
    // creates a new object
    this.leg = new leg(...);
    // foot data
  }
  // many methods that rely on,
  // and change, leg data
}
```

```js
class leg {
  constructor(...) {
    // creates a new object
    this.foot = new foot(...);
    // leg data
  }
  // many methods that rely on,
  // and change, foot data
}
```

*Simple mistakes that built-up over-time:*

```js
import leg from '/path/leg.js';
// NO "errors" in compilation
const leftLeg = new leg(...);
// ---Endless loop, or recursion, of NEW objects
// using up system resources and causing crashes
const hokeyPokey = (...) {
  leftLeg.putOut();
  // ...etc
}
// ---In big enough classes, finding bugs inside
// complex method calls can seem almost impossible,
// especially if changes come from the "outside"
```

Ultimately it is an imperative for our own benefit to head-off frustration because changes to any strongly-coupled object requires that it's reflected on the other.

Preserving the class' generic state also maximizes it's usage while preventing the need to create *mostly*-identical classes or methods to interact with different objects.

```diff
export class tree {
  constructor(...) {...}
  // keep methods generalized
- getPersonHug(personObject) {...}
- getAlienHug(alienObject) {...}
+ getHug(objectOfAffection) {...}
}
```

---

The legs of *tables* are not attached to a table's *hip-socket* and, to spare us the horror, should not be *implicitly* tied to one.

These concepts together are called **loose-coupling** and allows the programmer to focus on integrating these modules *where* they interact rather than *inside* of the objects themselves.

Tying *certain* classes of objects together is indeed intuitive but considering the broader need to relate *types* of object classes together for different *purposes*.


But then again, you might rather use a different *type* of leg by creating a new class when the usage, context, or underlying-data are significantly different.

 implicitly when they're *very* similar by including an identifying piece of data during it's creation.

This keeps the flexibility of each individual object in-tact while still being able to represent ever-more complex objects.

---
## Seeing the forest through the trees

Whether or not you're adhering to my set of coding practices you can see how I've outlined that spotting a pattern can save you a lot of time by *reusing* them and can even help to *understand* the work you've done.

There still requires the work of both *optimizing* how it works and *designing* the ways that they're utilized or interacted with.

What if it were the case, though, that someone else has already went through all the effort to optimize your idea, and perhaps already figured out the proper ways to interact with it?

The natural temptation would be to use what was already created, thereby extending the scope of the philosophy of DRY to encompass *everyone's* work.

### Pattern-seeking

The obvious challenge is gaining access to it if these works were not *common* problems, for an obscure functionality would be inherently much harder to find.

In the case when many people create the same shapes of *objects*--or classes--with the same *functionalities*--and methods--for the same *purposes*, we refer to that repeating *form* as a *design pattern*.

A **design pattern** is a special type of concept that combines the best-practices, or the common standards, at every level of the program, object, or functions, and have already been optimized to a *currently* un-improvable level.

Two examples of design patterns that I now have personal experience with is the Publish/Subscribe pattern and the join pattern implemented in [**Meteor-React**](https://guide.meteor.com/react.html), "a full-stack JavaScript platform for developing modern web and mobile applications."

---
#### The great wall

The Publish/Subscribe pattern addresses the problem of segregating user activity from the database.  The brilliance of the pattern allows for full flexibility of the definitions of the data objects to be held inside the database--each different type of object being a part of a "collection" or list for that specific object-type, called a "document" in this context--which means I can have many collections for any conceivable object.  Using this pattern allows me to dictate which of those objects are available to the user, and when and how they can access it, all while keeping the user from _directly_ interacting with it by allowing them to "clone" certain sections of the collection to a new one that that specific user can see.  This allows for many people to access the database without having any one person tying it up, and allows everyone to see their specific requested set of data.   I can only imagine implementing this type of thing with the greatest of dread and foreboding and I don't even know how it's implemented but is still usable by me.

#### The middle-man

The join pattern, however, is somewhat more abstract and is at first unintuitive.  When thinking of how to relate two different objects in different collections the intuitive solution might be to store a piece of _referential_ data in each object that points to the other one or by adding a _shared_ data to both of them, promoting coupling.  For example, you may have a "dog" object and a "person" object and you may have a piece of data in "dog" called "owner" that points to the "person" who has a "pet" data that points back to the "dog" or you might have both "dog" and "person" have some shared "pet-owner-ID" data and if they both have the same value then you know that the dog and the owner are related.

The problem with the additional data approach arises, as with inheritance, when you make changes to an object, or when you try to verify data.  In the case of the referential data, changes to one of the objects must be reflected by the other--if dog.owner changes then person.pet must change as well--and the problem only becomes larger when you want another relationship because each of the objects _themselves_ must grow in size _by design_, so that if the person got another dog then the "pet" data would contain more and more pets for that person.  In the case of the shared data, you might get a case where a "dog" might be evaluated as the owner of another "dog" when really that "person" has two dogs, and again, any change to the relationship must be performed on _two_ objects.

The elegant solution to the problem exists in creating a third object-type, for example a "dogPerson" that relates or "joins" the two different objects.  Each dog and person could have a "name" data--called a _key_ when that data uniquely identifies each in its own collection--and storing them both in that join object as references to both.  In this way, searching in the join collection can point to both and removing the relation is done on a single object.  Furthermore, the join can contain additional data about that relationship, so a dog with a name "Spot", and two persons, one with the name "John" and the other with the name "Mail-man", resulting in two join documents both sharing dogPerson.dog value while having different dogPerson.person values and different dogPerson.relationship values.  You can then search _two_ collections, by relationship, person, or dog, all from looking at _one_ collection.

### Standing on the shoulders of giants

These types of amazing solutions for common problems are not only incredibly valuable for the amount of time saved but have also been enlightening and inspiring in my brief time working with it and I doubt I could have come up with things that work as well as them.  For me, most of the design patterns I've read about don't come close to being as easily understandable as the ones I've identified, and they aren't named as intuitively as I like them to be, but then again I haven't yet been forced to work with them or to need their functionality.  These, however, support and parallel the other paradigms that I use to enable my coming back and being easily able to resume an unfinished and perhaps forgotten programming task after an extended period away.  I will try to incorporate and emulate these patterns, especially basic ones like module encapsulation, for the immense benefit of being able to speak to myself in a way that I can understand.
