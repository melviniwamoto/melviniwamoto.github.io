---
layout: project
type: project
image: img/manoa-recipes/manoa-recipes-logo.png
title: "Good food, good people, good times"
date: 2016
published: true
labels:
  - Meteor-React
  - javascript
  - github
summary: "An ICS314 project"
---
## Farm to table
There have been multitudes of dietary fads popping up and fading away for years but there is one thing that could never go out of style; meals made *yourself* from ingredients *you* chose.

The vast abundance of choices available and the relatively cheap prices of ready-to-eat meals, or *fast*-food, permeates every corner of our society.

<img width="30%" class="rounded float-start pe-4" src="../img/manoa-recipes/wendys-meme.png" alt="Screenshot of the Wendy's company criticizing the McDonald's company">

This breeds and sustains a culture of consumerism that only serves to produce viciously competitive and unkind interactions between inanimate probably-evil corporate entities.

I was part of a group that developed an application in a project, called Manoa Recipes, whose noble purpose was to provide college students with a website where they could find and exchange cooking recipes.

---
## Manoa Recipes
<img width="100%" class="rounded float-start pe-4" src="../img/manoa-recipes/manoa-recipes-home.png" alt="Screenshot of the Manoa Recipes website home page">

The website is centered around the recipes, naturally, along where to find the ingredients for them and what the prices would be at locations near to the campus.

A lot of work went into the project and can be found in the [project page](https://manoa-recipes.github.io/) for the website, however, I will be focusing what I talk about around implementing the evolving administrator page and the initial data structures I designed the website to have.

### Growing pains

Establishing a simple page for the admin gave way to the realization that I wasn't able to make a list of data whose shapes don't yet exist; so I shifted to designing a tentative data structure to display.

I began by doing some research on recipes to distill all the information into separate pieces of data; each recipe has a name and a list of ingredients, and the template was easy to spot.

Each ingredient in a recipe has--at a minimum--an additional size and amount with the name of it, and, by design, were intended to include associated prices and locations of markets.

It became obvious that ingredients were the central data point that linked every intended function of the website.

