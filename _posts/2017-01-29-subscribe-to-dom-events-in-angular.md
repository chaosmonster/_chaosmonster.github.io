---
title:        "Subscribe to DOM Events in Angular"
description:  "Last week I tried figure out how to subscribe to a click Event in Angular v2.x"
author:       "Martin"
---
So my basic problem was, that I needed to somehow delay a **blur** event (or to be precise the callback function) after a **click** event.  
My first thought was to use a `debounceTime` operator from **rxjs**, but I found out that **blur** is a real EventListener and not the **rx** counter part `Observale.ofEvent`.  

While the ["This.JavaScript"](https://www.youtube.com/watch?v=InOWBvseRYU) panel at 29. January 2017 [Ben Lesh](https://twitter.com/benlesh) mentioned something about **rxjs** doing some stuff with **zone.js**.  
After the show I dug into the issues on github and found this [issue](https://github.com/angular/angular/issues/13248), where [Miško](https://twitter.com/mhevery) introduces what I was looking for. As this issue from December and seems to depend on changes in **rxjs** I'm hoping that it may be part of some minor version of **Angular** 4 if not of the verison 4 itself in March/ April this year.

Btw my first problem could be solved like explained [here](https://github.com/angular/angular/issues/5489#issuecomment-160036492) or like I did in the above case move from the **click** event to the **mousedown** event as it is executed before the **blur** event.