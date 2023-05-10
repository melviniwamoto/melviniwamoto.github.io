---
layout: essay
type: essay
title: "Pulling myself up by the Bootstrap"
# All dates must be YYYY-MM-DD format!
date: 2023-05-09
published: true
labels:
- HTML
- CSS
- javascript
- UI-Frameworks
- Bootstrap-5.0
- React
- React-Bootstrap
---

<img class="img-fluid" src="../img/uiframeworks-e37/text-to-tablet.jpg" alt="Picture of a text-message translated to cuneiform and written onto a clay tablet">

## Lost in translation

Language is a powerful tool for accurately and concisely *symbolising* and *sharing* ideas.

*Written* language extends the possible scope of a language's utility *immeasurably*--temporally and spatially--and is perhaps the most important invention in all of human history.

Every language and alphabet can have wildly different *grammars*--patterns and structures of letters, words, and sentences--that must be followed, *to the letter*, to glean or convey anything meaningful.

*"Car driving person"* or *"mouse chased cat"*, depending on the motifs of the grammar, can have implications *differing* from a self-driving car or a monstrous rodent.

### *So* sorry.

Often *tone* or *contextual purpose* is the primary factor in trying to understand what *actually* was meant from any given message, but it can be challenging to communicate without some *conventions*, or agreed patterns, to represent them.

Formatting can serve to impart the intended subtext on, or include additional context to, the overlying message through *emphasis* or **highlighting** on ***words and Letters***.

Hyper-Text Markup Language [HTML][^html], Cascading Style Sheets ~~Language~~ [CSS][^css], and JavaScript [JS][^javascript] are the languages for the **content** and **formatting** and **functions**, respectively, of the documents that *browsers* use to communicate with *pages*.

<img width="40%" class="float-end" src="https://cdn.decorpad.com/photos/2020/11/23/restoration-hardware-wall-scrabble.jpg" alt="Image of a board-game that uses letters as pieces">

#### Elemenopee

HTML ***elements***--which are the *types* of sections of a page, called tags--and CSS ***classes***--group-settings like sizes with colors--make up the *alphabet and punctuation* of the *language of the internet*.

```html
<div class="properties" id="division-element">
  <img src="www.image-element.com/picture.jpg" />
  <p id="paragraph-element">Text about above.</p>
</div>
```

---
### Sound it out
Learning how to spell words can be painful ~~and seem spiteful~~ but, in programming, as long as reading it produces the correct-enough sounds it doesn't matter *how* you ***spehl*** it.

When introduced to new words through speech you *could* deduce the correct *spelling* if you were already familiar with the culture, and *grammar*, that the word was from.

This is because there exists a common *vocabulary* of words that already symbolize many common *sounds* of the language into it's *typically* written forms.

A grammar normally has different rules for speaking and writing *types* of words depending on how those words are *used* or to modify what it *means*.

Typical **Verb** Forms:
- Base: **Spell**
- Spell***ing***
- Spell***ed***
- ~~Spell***unking***~~

For some reason, there are people who catalog the "correct" spellings--ie. colo~~u~~r--of words and their derivative forms into horrible--logically-ordered--lists that are *hundreds* of pages long called dictionaries.

Luckily, there are technologies that allow programs with electronic dictionaries to predict what you're spelling and suggest words that match your input.

---
## *These boots are made for talkin'!*

[**Bootstrap-5.0**](https://getbootstrap.com/docs/5.0/getting-started/introduction/) is a [user-interface](https://en.wikipedia.org/wiki/User_interface) [framework](https://en.wikipedia.org/wiki/Software_framework) (UI-Framework), that is a set of CSS tools that help to design and build user interfaces, and is for website designers what auto-complete and spell-check is for writers.

```html
==HTML and CSS without Bootstrap==
==For a Column==
<div class="width-1 height-2 color-1 text-1">
  ==For a Row==
  <div class="width-3 height-4 color-1 text-2">
     <...>
  </div>
  <...>
</div>
==For a generic Container==
<div class="width-5 width-6 color-1 text-2">
  <...>
</div>
```

Bootstrap streamlines the process of dividing pages up into commonly formatted sections, like columns and rows, for various purposes, like buttons, links, or plain text, or for *theming* sections differently.

It also supports automatically sizing elements based on the screen's or window's dimensions, allowing phones and computers to both view the same page from the same document, albeit differently.

```html
==With Bootstrap==
<div class="col theme-1">
  <div class="row theme-2">
     <...>
  </div>
  <...>
</div>
<div class="container theme-2">
  <...>
</div>
```

Combining Bootstrap with [**React**](https://react.dev/), another UI-Framework, produces an advancement in the development-speed of web pages--and this is ***not*** an exaggeration--*on the level of **dictation-software*** and is called [**React-Bootstrap**](https://react-bootstrap.github.io/).

```html
==With React-Bootstrap==
<Col>
  <Row>
    <...>
  </Row>
  <...>
</Col>
<Container>
  <...>
</Container>
```

You can see how powerful it is to semantically name the elements to replace the repetitious class-combinations.

This reduces the difficulty in *writing* and *reading* HTML and CSS to a trivially-low level and allows the programmer to focus on the *big-picture* rather than getting bogged down in all the details.

An immense vocabulary combined with the appropriate artistic tones and formats, along with templates and other tools, gives us the opportunity to be as eloquent as we can be.

---
**References:**

[^html]: **Hyper-Text Markup Language** (**HTML**): *"... the standard markup language for **documents designed to be displayed in a web browser** ..."*: <https://en.wikipedia.org/wiki/HTML>

[^css]: **Cascading Style Sheets** (**CSS**): *"... a style sheet language used for describing the **presentation of a document written in a markup language** such as HTML ..."*: <https://en.wikipedia.org/wiki/CSS>

[^javascript]: **JavaScript** (**JS**): *"... a programming language that is one of the **core technologies of the World Wide Web, alongside HTML and CSS**. ..."*: <https://en.wikipedia.org/wiki/JavaScript>

---
