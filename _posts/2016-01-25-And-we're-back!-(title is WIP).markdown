---
layout: post
title:  "Modeling Functions with Movement"
description: "A website that models a position over time function with a neat little white circle."
date:   2016-01-25 4:20:41pm
categories: HTML projects
img: mmm
---
<h3><b>What it is:</b></h3>
Awesome website that takes any equation you give it and makes a white circle model a movement based on said function.

<b>Site:</b> [snickerton.github.io/Math420ModelMovement/][site]

<b>Duration Coding:</b> An entire night so.... 6 hours..ish?

<h3><b>Process:</b></h3>
So yeah wow hey we're back once again, coding through the night like the good ol' times. I'm sure all of my 2 followers are glad to hear that I'm not dead and that they can't wait to tell me how much they've missed me during my extended hiatus. However, before we do all of that I just wanted to note how great it is to be back on campus and how wonderful and supportive everyone's been since I've gotten here. Mushy gushy feelings aside though, let's dive right into it.

It started out has a discussion in class one Thursday morning. We were talking about how nice it would be to visually see and understand a certain math problem our class was having trouble with. This quickly evolved into a "yeah sure I totally have lots of time I can whip that up tonight and have it by tomorrow for the class" towards my teacher who, needless to say, was ecstatic about it. Except it became very apparent to me very quickly that this was not going to happen given my homework ridden schedule and inherit laziness. Either way I put it off until Saturday evening where, out of a sudden desire to create, I decided to sit down and code.

So what did I want to program to do? Well it needs to parse an equation typed into the input box. That equation will then define the x or y position of a dot that I will draw on an HTML canvas and update periodically given the frame game loop it's at (it'll all make more sense later bear with me).

First I needed a library for math text (aka LaTeX) so I can get a Desmos-esque input box. A quick google search results in the one and only Mathquill, a library that Desmos itself uses. A quick 2 hours of seeing its documentation (or lack thereof rather) and I decided "let's try Mathquill later when I'm feeling more insane." Next I needed a way to take the user-given equation and evaluate it in my code with a variety of x values. This seemed incredibly daunting at first as it seemed to require some way to rewrite the base code in the game loop. However, some angel on the internet had already solved this problem and saved me the headache (link [here][site2]). Finally, I structured a game loop (setInterval) and made an FPS variable that could be user defined to adjust the speed. Here's were things get a bit wonky. The y position of a "thing" is set to, say, x^2 whereas x is the amount of time passed. So in theory I can just keep a frame counter and mod that by something to get a looping incrementing value based on time right? But I soon realized that this x value I plug in has to start somewhere on the x^2 graph. I can't just set {% highlight javascript %} x = 0 + frameCount {% endhighlight %} and let it run because then we're getting an extremely biased portion of the quadratic graph. So instead I allowed for a user inputted domain which I then used to structure most of the modding and limitation of x through that. So after a lot of mathy mathy math (subtracting lower domain from upper domain, making that your... well... domain, x mod that plus 1 for various reasons add pixie dust) I finally got a working model of the equation.

<h3><b><s>Lesson Learned:</s> <br>
Additions to the Toolbox: </b></h3>
"Lesson Learned" sounds weird now that I think of it (it's like TIFU post from reddit). From now on, I hereby declare this section to be named "Additions to the Toolbox" because it works with the whole tinkerer theme (and it's my website so I can do that yo).



<h3><b>Future:</b></h3>
Hopefully I'll be able to come back to this and give some better documentation on the process, but for now this will have to do. I also plan to add support for multiple "nodes" (white dots in different places) and also support for a velocity over time graph. Perhaps I'll add in an autoscaling algorithm so that the user doesn't have to adjust the domain and scale based off of the shown canvas.


[site]:    http://snickerton.github.io/Math420ModelMovement
[site2]:   https://silentmatt.com/javascript-expression-evaluator/
