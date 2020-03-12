---
layout: post
author: ZweiEuro
title: Structutal improvements
---

    Hello, most likly me, being curious in the future what the hell I thought and why I started this, \
    How are you doing? I am doing great currently! I think I made a big improvement.



    I finished implementing my 2 thread system for my game and it's event queue, I've decided that I will make the main thread into\
    the control thread and create draw/input worker threads.\
    Now it really payed of to build an event system for the game state changes, this made it incredibly easy to implement a "restart" thing.\
    Actually ... I don't know if allegro lets me easily resisze a display, but I wanted to make sure and I thought it would be an interesting challenge, also I eventually would have to do it anyways.\
    Essentially I made a proper way to tear down and rebuild the whole system, in this case just draw and input threads.\
    This is incredibly useful! now if a big display change happens which includes I have to drop the current display and buffer allocations, I can!\
    Especially with some barriers build in so everything stays nice and synchronized it is a treat to watch!\

    Also I managed to clean up the code A LOT, now there is no central system with all the data anymore, display and input data are properly stored in their respective local stacks for the threads (in this case just in the cpp programm files).\

    Next up is settings, and I am certain I can make this properly, first I really want to implement the scale factor so I can try restarting the display with the events I've just implemented. :) \
