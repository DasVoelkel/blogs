---
Author: Zweieuro
title: Sturdy start
---


It took me almost the whole day, but I finally managed to get a somewhat good ( I think ) structure down for the game to run on. 


In itself the first game was just running in a single thread, at least all the events were managed that way. This means that no matter what you will always be restrained. \
Since I want stuff to be structured and not all in one mix like, display output, audio output, keyboard input and frame drawing, I needed to offload this stuff. \
Easier said than done ... this meant I had to multithread everything, thankfully I quickly foudn out allegro has it's own implementation of pthread and thereof, so i could use that. \
Mind you their implementation doesn't do you any favors since it's almost identicaly to the real thing, but the crucial differences are documented a little sparsly, mainly \
 ***pthread_exit()*** straight up ***doesn't*** exist! This had me thinking around. \
 Now since everything was event driven the threads would stall at their respective event queue.\
 Drawing -> timer thread runnning 60 fps\
 input -> keyboard listener running on those events\
 display -> well I added this to the input from the keyboard since the only thing I want here was "exit" which happens when you click the red 'x' of the window.\

 Problem: How do I tell every thread that it should exit? \
 On the docs it doesn't say what happens if the threads are "joined" or "destroyed" when they are not finished, since both calls have implicit "wait until stops" stuff on it, super annoying.\
 I didn't want to test it out either, and quickly thought that my idea of solving this could be useful anyways: \
 Create a custom event and trigger it when the "GAME STATE" of the game itself changes, with this I could also globally control a context switch e.g. to a menu or something.\
 This wasn't too hard to implement, but after implementing it the programm went apeshit.\
 As soon as you exit it would spam a lot of clutter onto the console, which are my debug messages, triggering events like id: '-1' , which does not exist. \
 This took me more than 1.5-2 hours to debug, in the end when i de inited everything and deleted the queues and events (which I dilligently programmed thoroughly because I thought that was the reason,\
 I noticed that I called (copy paste error) a deinit for the display twice, which has an internal buffer init that also deallocs.\
 Why there is no warning dispensed even on debug compile mode is beyond me, but simply fixing that fixed everything else.\
 Again... super anticlimactic. But fun ^^ now it works!

 Next up are options and how to scan the jsoon file, I started on it a bit but it's nowhere near done yet. \
 My next big big goal is installing the assets, and parsing them through the json and viewing them in the program. Yes that will take a while, but I got time anyways since Uni is out of order :P 
 -Ze
