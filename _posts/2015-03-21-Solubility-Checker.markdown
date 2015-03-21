---
layout: post
title:  "Solubility Checker"
description: "Website that determines if a compound is soluble or not"
date:   2015-03-21 9:16:41pm
categories: HTML projects
---


<i>Article is still under construction. <br> <br> Note: This project was created before the birth of Tinker but I still wanted to keep a record of it. Therefore, many of the descriptions will be vague, and will accurately exhibit how bad my memory is.</i>

<h3><b>What it is:</b></h3> Chemistry solubility rules are tedious and annoying to go through every single time. The rules/conditions are perfect for computers however, so I created a website that evaluates an ionic compound given these rules.

<b>Site:</b> [snickerton.github.io/SolubilityChecker][site] 

<b>Duration Coding:</b> idk don't remember....an evening...? maybe like 2 hrs actually

<h3><b>Process:</b></h3> 
Okay before we get stuck in you might need a quick crash course on chemistry or just a refresher:
an ionic compound has two components: a positively charged component (aka "a cation") and a negatively charged component (aka "an anion"). When working with double replacement reactions, usually a precipitate will form with one compound and not the other. The precipate, as you can guess, is the insoluble compound; the one that does not dissolve into the solution and falls to the bottom (hence "precipitate").

The rules for identifying it's solubility, as shown on the website, are quite straightfoward but just require a lot of work. Luckily the conditions aren't extremely complicated so we should be able to easily convert them into `if` statements. I want this to be a website so it can be widely used by any of my classmates so we'll use Javascript and simple HTML. First we need some word banks of all the cations and anions that are relevant to each rule. We can then use the banks of strings to compare it with the user inputed compound, also a string. So we'll be able to see if, say, "cation1" in the user-given compound is found in the list of accepted cations in rule 4. Seven arrays later, and bam, all we need are a list of "if" statements. 
(I guess you could say that the precipates were <i>deposited</i> in our <i>banks</i>.)<sup> sorry not sorry </sup>

For the UI, I decided that rather than asking for the entire written compound in one input box, I would ask for the cation and anion seperately. This saves me from needing to `split()` a string with a delimiter that the user may not even use correctly. In addition I can directly compare the input from the cation"or anion input box to it's respective cation/anion in the banks I have set up. 

Finally all we need are the `if` statements. What I ended up doing was working through each rule and translating it into a logic statement in javascript. For example, rule 4 states that any compound with sulfate being the anion is soluble...unless the cation happens to be barium, strontium, lead etc. So logically we need to check <b><i>if</i></b> the input anion string is <b><i>equal</i></b> to "SO<sub>4</sub>" (sulfate) <b><i>and</i></b> the input cation <b><i>does not equal</i></b> to any of the exceptions listed in our word bank of "rule 4 exceptions". 

Unfortunately, chemistry also dictates that we can have more than one SO<sub>4</sub>'s or bariums in a compound so excess numbers may be included to indicate the amount of an element (e.g. "(SO<sub>4</sub>)<sub>2</sub>"). Because of this, I decided that I would just check if the cation or anion string `.contains` any of the ions in our word banks. So even if the user gave "(SO<sub>4</sub>)<sub>2</sub>" we would just be searching for "SO<sub>4</sub>" and ignore any excess numbers. I wrote a quick `coincides(arr, str)` method to iterate throught the given word bank/array and check if any string was contained...

{% highlight javascript %}
function coincides(arr, s){
	for(var i = 0; i<arr.length; i++){
	  if(s.indexOf(arr[i]) > -1){
	  	return true;
	  }
	}
}	
{% endhighlight%}

...and voila! All done.

<h3><b>Lesson Learned:</b></h3>
Computers are the best. If there's some repetitive checking or evaluating to be done, then be lazy (or a programming) and make a website do it for you. HTML buttons and forms were very easy and straightforward as I remember because I don't recall spending much time figuring out how to get things working (unlike the HTML canvas <sup>*cough cough*</sup>).

<h3><b>Future:</b></h3> As rare as it is, this project actually met all the goals of the original dream. It definitely came in handy and I'll probably continue to use it to save those 5 minutes on my chem homework.



[site]:    http://snickerton.github.io/SolubilityChecker/

