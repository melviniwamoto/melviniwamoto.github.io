---
layout: project
type: project
image: img/snake/snake-header.jpg
title: "Snake: Nokia nostalgia"
date: 2015
published: true
labels:
  - C-Language
  - UNIX
  - VIM

summary: "A final project for EE160, written in C in 2015."
---

<head>
  <h1>My first Project: Snake - Nokia Nostalgia</h1>
</head>

<body>
  <img class="img-fluid" src="../img/snake/snake-header.jpg">
  <h2>About the Game</h2>
  <p>As mass production flooded the market with newly affordable mobile phones, not only with regard to the hardware but with the contracts for service as well, aquiring these phones became much more practical and prevalent for "middle-class" families.  In some cases, as time progressed in these market conditions, even children and young adults were gaining personal access and ownership of these devices.  The game "Snake" came pre-installed onto Nokia phones and it is by this way that I was introduced to the game and it was one of the only other functions of the phone, aside from talk and text, before the appearance of smart phones and the app stores they brought with them.</p>
  
  <p>The game is a simple untimed game that is played on a grid.  On that grid is a snake represented by a head with a direction on one space and the rest of the body and tail on trailing spaces which grows in length as the snake collects tokens, presumably representing mice.  The snake moves on its own and the player must direct the snake in such a way that it never crosses its own body, which causes the game to end, providing an increasing difficulty level as the game progresses.  The snake is also programmed to begin to move faster as it grows, thereby compounding the increasing difficulty.  The game is technically winnable with a maximum possible score if you can fill the entire grid play-area with your body.  Eventually the game was made to support a high-score list and was ultimately given a sequel-game with improved graphical representation of the grid, the tokens, and the snake.</p>

  <hr>
  <h2>About the Project</h2>
  <p>In 2015, I was pursuing a degree in Civil Engineering and I ended up enrolling in the course Electrical Engineering 160 to fulfil a requirement for the Associates degree in Science offered from the University of Hawaii (UH): Kapi'olani Community College's (KCC's) STEM program.  This was the first time I had ever interacted with computer science or programming and it sparked great interest in me despite having to learn the command-line UNIX system that UH uses and the infuriatingly hard-to-use text editting program Visual Editor Improved (VIM).</p>

  <p>As part of the final grade for that course we were required to write a Game Design Document (GDD) and implement the game from C Language.  After reviewing example programs that utilized a periodically refreshing grid layout, simulating animation, to display gameplay areas on a text-console I was reminded of the game snake and decided to pursue that for my submission.  The greatest appeal, of course, was that I'd be able to create the program simply from modifying the existing example programs in such a way that the game would play out as I remembered it.</p>
  <img class="img-fluid" src="../img/snake/screenshot-snake-game.jpg">
  <p>The above is the console output of the actual code used in the submission of the project that was preserved on the UNIX system and that I retrieved a year ago, in the spring of 2022, when I had to once again use that system for the course ICS212.  Unfortunately, the app I used to try to run the program does not support the file-linking procedure in <em>makefiles</em>, and the code itself is also quite primitive, and so is now throwing errors that the old system wasn't perhaps able to catch; so my attempt to splice together the code from several files resulted in a broken game that can only display the grid area and the title of the game.  It does, however, show the starting point for the head of the snake with the letter S for snake, and the initial position of the token to collect with the letter F for food.  It should also be showing the time elapsed and the score, but the game doesn't even refresh and play through anymore.</p>
  <p>Although the picture may not show much, and the effort put forth may have been sorely lacking, this image portrays more for me than simply the final project at the end of an engineering course.  Indeed, it also represents the beginning of my current path in computer science and the memory also helped me in choosing my direction after I abandoned my pursuit of an engineering degree.  This project is the most appropriate work to showcase as it was the first program I wrote that I had any say in and invokes a sense of pride.</p>
  <hr>
</body>
