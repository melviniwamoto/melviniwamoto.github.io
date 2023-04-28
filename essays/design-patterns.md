---
layout: essay
type: essay
title: "Writing for tomorrow, today."
# All dates must be YYYY-MM-DD format!
date: 2023-04-27
published: true
labels:
- javascript
---
## Writing for tomorrow, today.
### Speaking in tongues

Understanding others can be troublesome when there are language barriers, but it is even more pronounced when someone uses idioms you're unfamiliar with; "What do you mean the early bird catches the worm?  Which bird?"  Now imagine that the speaker you're listening to isn't even necessarily being intelligible in that language.  That is what it is like, sometimes, while reading my own work.  This is why I try to provide enough context to myself, or anyone else for that matter, about what I was trying to accomplish and there are certain things that we do in programming which can alleviate that very human struggle of trying to understand yourself.

### Paradigm-a-dozen

Recognizing patterns comes naturally to us as "great" apes, and if we see something repeating we may find it aesthetic pleasing, or not, depending on the context.  In the context of _work_ the prospect of repeating the same laborious tasks over and over is what leads to innovation, like in the case of power tools.  In programming, we have a unique opportunity to create these innovations ourselves and it is greatly encouraged because of how _frequently_ we encounter these repeating patterns.  The first time many of us are made to be aware of this, in our specific context, is in the phrase "Don't Repeat Yourself."

When we see a repeating set of tasks we like to group them up into nice little packages called "functions" with overly-descriptive names.  In this way we can cut down on the sheer amount of letters we are looking at while still giving context as to what it is, just as it is when you abbreviate University of Hawaii (UH) in a document and can therefor refer to UH again very simply.  Furthermore, By grouping it up into a function we can change one part _inside_ of it and affect it every time it is used, as would be the case had I misspelled the "definition" of the abbreviation.

Of course, there can be larger patterns to see when certain sets of _functions_ are repeated, so we in-turn create higher-order functions, and so-on, but the key point is to have the overly descriptive names at every level that explains what it actually does.  We can even separate these functions from the file that uses it and "import" these functions to further improve readability and to prevent it from being changed where it is being used, and this concept is _encapsulated_ as the "module" and is perhaps one of the most useful imperatives in software design patterns that I've come across so far.

In this same fashion, we can collect either repeating or related sets of data, _especially_ when they relate to or refer to the same thing, into "objects" just as we do in the case of the "covers" and "pages" of a "book" or the "name" and "age" of a "person."  These objects that we create often have specific functions that they perform, or that are performed on them, and we call them "methods" to differentiate it from "functions" because of it's context of being related to an object, and can also be encapsulated into a separated "module."

### _Not_ more than meets the eye!

We humans have a desire and a drive to make things better and/or faster and/or automated.  The benefits of these things are obvious and we live in a world where a phone might not be used to perform it's _primary_ task of making a call, but rather to primarily perform _other_ tasks, yet in programming we like to limit our functions and objects to only do what it _says_ it is going to do and when there is a further need we just make new functions or objects.  We want our objects to be completely self-sustaining so that there isn't some _other_ object performing critical functions on it, nor does it itself perform the critical functions on another.  Furthermore, we don't want our objects to possess or rely on another's data, and we preferably don't want them to have intersecting or overlapping functionality either.

This concept is known as "loose coupling" and is another useful paradigm that is build around the expectation that changes to an object should have no affect on another.  A previously popular design pattern was in direct contradiction to this idea, which posited that objects should "extend" other simpler or smaller objects.  For example, a "shape" object with a "position" data would extend itself to a "square" with an additional "width" data or a "circle" with a "radius."  This, of course, could cause problems if the "parent" object did something that the "child" object didn't know would happen, or if the "parent" object was changed to exclude data that the "child" object relied upon, and could even lead to a seemingly unnavigable hierarchy structure of "inheritance."

### Freedom isn't free

These types of rigid imperatives are completely voluntary and can at times become tedious, but, in my experience, has greatly improved legibility and the form of the work can even approach the intelligibility of natural language.  Coming back and being easily able to resume an unfinished and perhaps forgotten task is priceless after an extended period away and conforming is such a small price to pay for the immense benefit of being able to speaking to myself in a way that I can understand.
