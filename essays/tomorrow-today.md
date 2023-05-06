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

### Paradigm-a-dozen

In the context of *work* the prospect of repeating the same laborious tasks over and over is what leads to innovation, like in the case of power tools.

When programming in javascript, we have a unique opportunity to create these innovations ourselves and it is greatly encouraged because of how *frequently* we encounter these repeating patterns.

The first time many of us are made to be aware of this, in our specific context, is in the phrase "Don't Repeat Yourself" (DRY).

When we see a repeating set of tasks we like to group them up into nice little packages that we "define" called "functions".

Defining these functions with overly-descriptive names is a type of *design pattern* called the ***Facade* pattern** because of how the name of it hides the complexity *behind* it.

#### Spotting the trees in the forest

Of course, there can be larger patterns to see when certain sets of *functions* are repeated, so we in-turn create higher-order functions, and so-on, but the key point is to have the overly descriptive names.

We can even separate these functions from the file that uses it and "import" them into multiple files, improving the benefit of facade and preventing it from being changed where it is used so it doesn't affect other files.

this concept is _encapsulated_ as the "module" and is perhaps one of the most useful imperatives in software design patterns that I've come across so far.

In this same fashion, we can collect either repeating or related sets of data--_especially_ when they relate to or refer to the same thing--into "objects" just as we do when we refer to the "covers" and "pages" as simply a "book" or the "name" and "age" that is represented or identified when referring to a specific "person."  These objects that we create often have specific functions that they perform, or that are performed on them, and we call them "methods" to differentiate it from "functions" and to infer it's context of being related to an object.  These objects and it's methods can also be encapsulated into a separated "module" as well and helps to keep the main file size--where the rubber meets the road, if you will--at a minimum while things become increasingly complex.

#### _Not_ more than meets the eye!

We humans have a desire and a drive to make things better and/or faster and/or automated.  The benefits of these things are obvious and we live in a world where a phone might not be used to perform it's _primary_ task of making a call, but rather to primarily perform _other_ tasks, yet in programming we like to limit our functions and objects to only do what it _says_ it is going to do and when there is a further need we just make new functions or objects.  We want our objects to be completely self-sustaining so that there isn't some _other_ object performing critical functions on it, nor does it itself perform the critical functions of another.  Furthermore, we don't want our objects to possess or rely on another's data, and we preferably don't want them to have intersecting or overlapping functionality either.

This concept is known as "loose coupling" and is another useful paradigm that is built around the expectation that any changes to any object should have no affect on any other.  A previously popular design pattern was in direct contradiction to this idea, which posited that objects should "extend" other simpler or smaller objects.  For example, a "shape" object with a "position" data would extend itself to a "square" with an additional "width" data or a "circle" with a "radius".  This, of course, could cause problems if the "parent" object did something that the "child" object didn't know would happen, or if the "parent" object was changed to exclude data that the "child" object relied upon, or could even lead to a seemingly unnavigable hierarchy structure of what is referred to as "inheritance".

### Seeing the forest through the trees

Whether or not you're adhering to my specific set of coding practices, you can see how I've outlined that spotting a pattern can save you a lot of work by _using_ these objects and functions to re-use the work you've done, and naming conventions can help _understanding_ the work you've done, and yet there is still all that time spent _designing_ and _developing_ these things.  What if it were the case, though, that someone else has already went through all the effort to create that _something_ that has all the functionality that you want to implement?  The obvious temptation would be to use what was already created--extending the scope of the philosophy of DRY to include others' work--but the challenge would be gaining access to it if it weren't a common problem, for an obscure functionality would be inherently much harder to find.

In the case when many people come to the same or similar solution for the same problem, we call the _form_ of that solution a "design pattern" and are generally regarded as the most efficient, and thereby elegant, implementations of that particular functionality.  Two examples of _this_ that I now have personal experience in working with is the Publish/Subscribe pattern and the join pattern in Meteor, "a full-stack JavaScript platform for developing modern web and mobile applications."

#### The great wall

The Publish/Subscribe pattern addresses the problem of segregating user activity from the database.  The brilliance of the pattern allows for full flexibility of the definitions of the data objects to be held inside the database--each different type of object being a part of a "collection" or list for that specific object-type, called a "document" in this context--which means I can have many collections for any conceivable object.  Using this pattern allows me to dictate which of those objects are available to the user, and when and how they can access it, all while keeping the user from _directly_ interacting with it by allowing them to "clone" certain sections of the collection to a new one that that specific user can see.  This allows for many people to access the database without having any one person tying it up, and allows everyone to see their specific requested set of data.   I can only imagine implementing this type of thing with the greatest of dread and foreboding and I don't even know how it's implemented but is still usable by me.

#### The middle-man

The join pattern, however, is somewhat more abstract and is at first unintuitive.  When thinking of how to relate two different objects in different collections the intuitive solution might be to store a piece of _referential_ data in each object that points to the other one or by adding a _shared_ data to both of them, promoting coupling.  For example, you may have a "dog" object and a "person" object and you may have a piece of data in "dog" called "owner" that points to the "person" who has a "pet" data that points back to the "dog" or you might have both "dog" and "person" have some shared "pet-owner-ID" data and if they both have the same value then you know that the dog and the owner are related.

The problem with the additional data approach arises, as with inheritance, when you make changes to an object, or when you try to verify data.  In the case of the referential data, changes to one of the objects must be reflected by the other--if dog.owner changes then person.pet must change as well--and the problem only becomes larger when you want another relationship because each of the objects _themselves_ must grow in size _by design_, so that if the person got another dog then the "pet" data would contain more and more pets for that person.  In the case of the shared data, you might get a case where a "dog" might be evaluated as the owner of another "dog" when really that "person" has two dogs, and again, any change to the relationship must be performed on _two_ objects.

The elegant solution to the problem exists in creating a third object-type, for example a "dogPerson" that relates or "joins" the two different objects.  Each dog and person could have a "name" data--called a _key_ when that data uniquely identifies each in its own collection--and storing them both in that join object as references to both.  In this way, searching in the join collection can point to both and removing the relation is done on a single object.  Furthermore, the join can contain additional data about that relationship, so a dog with a name "Spot", and two persons, one with the name "John" and the other with the name "Mail-man", resulting in two join documents both sharing dogPerson.dog value while having different dogPerson.person values and different dogPerson.relationship values.  You can then search _two_ collections, by relationship, person, or dog, all from looking at _one_ collection.

### Standing on the shoulders of giants

These types of amazing solutions for common problems are not only incredibly valuable for the amount of time saved but have also been enlightening and inspiring in my brief time working with it and I doubt I could have come up with things that work as well as them.  For me, most of the design patterns I've read about don't come close to being as easily understandable as the ones I've identified, and they aren't named as intuitively as I like them to be, but then again I haven't yet been forced to work with them or to need their functionality.  These, however, support and parallel the other paradigms that I use to enable my coming back and being easily able to resume an unfinished and perhaps forgotten programming task after an extended period away.  I will try to incorporate and emulate these patterns, especially basic ones like module encapsulation, for the immense benefit of being able to speak to myself in a way that I can understand.
