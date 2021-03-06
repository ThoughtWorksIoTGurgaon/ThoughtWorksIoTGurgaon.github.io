---
layout: post
title:  "Learnings and start of a journey"
date:   2016-01-16 19:54:33
comments: true
categories: Showcase Learnings MovingForward
---


*"When you don't create things, you become defined by your tastes rather than ability.Your tastes only narrow & exclude people. so create."*


The Idea
------------

The Internet of Things has always been every *lazy* programmers dream - we yearn to make things more comfortable for ourselves,as a programmer we hold our environment customizations/ide and choice of tools dearer than the code we write for we know that those are the things that make our life easier; the tools that we use are what make us feel at home with the code we write.The idea of automating  and customizing our physical environments similar to our virtual environments is thus something that every programmer has always dreamed of and constantly desires.Imagine being awoken to the sound of sprinklers watering your plants,coffee being brewed just the way you like it,your news feed and email ready and delivered to be read out while you get ready for work - all done automagically through some customized configuration/code you wrote to your liking,isnt that exciting!


It is with that thought and the motivation of being lazy that a couple of us programmers here at the office in gurgaon got together for building SmartX - a flexible framework that allows us to build *things* connected through *code glue*,or well that is how we started at least about 4 months ago and it has been a wild ride ever since!The current framework allows you to add *things* to your home automation setup without much drama,it allows you to build things seperately on the arduino and with minimal use of the SmartX library you can have your home auto discover and configure your devices for you.

The way it works is simple -:

1. A defined preset of communication standards and device characteristic definitions that stay common to the whole architecture.

2. A control system that discovers/manage and controls any new devices it sees.

3. A library for the Arduino called Scarab that makes life easy for you and exposes an API that lets your code talk to the controller

4. A fronted - Asgard that lets you view and control/configure all your devices in real time,if a device toggles state,the UI updates it in real time.

The code can be found and used [here][Github-repo] with a brief presentation from the session and more information on the tech stack [here][presentation].

![Smart-X][smartx-image]


Why is SmartX different from all the public n - home automation frameworks
----------------------------------------------------------------------------

Why did we go about building SmartX when we couldve just configured and used something like OpenHAB?!For one,we did it for fun and now that thats out in the open,allow me to help you make sense of the advantages that such a framework may have-:


1. Instead of having the bus standard which is most commonly used,we felt that going for a reactive framework made more sense.A bus although may seem more simple brings in more complexity when you want to do things such as device redundancy/fault tolerance/device operation locality - something that IoT needs very much.For example what if we wanted to have multiple controllers controlling devices in different localities within the house (Indoors vs Lawn/Garage),the use of Actors allows us to easily build and manage clusters with locality of concerns and is much better in my opinion than using a queue based system. 

2. All current frameworks give you the ease of configuring devices but you still have to buy most of them and they are expensive as hell!A single LED wifi bulb will cost you close to 9000INR,this is because the devices are packaged as such;having to replace your existing set of appliances with expensive ones with shorter life spans and support makes very little sense.We aim to do away with this by offering cheap connectors that just attach to your existing set of appliances and also giving the user the ability to build his thing for himself through the use of Scarab.

3. Shared consumer data analytics - One of the key things that we found lacking in the current set of IoT software is analytics and intelligence which although often neglected should be one of the main focus areas - I should be able to share my data with other people and get analytics on things such as device energy consumptions,average life span in real life to make more informed decisions.This will not only benefit device manufacturers but also help people choose the best device according to their needs.


Where are we now?
-------------------

We conducted our first [showcase][Showcase] last month to the office where we were able to succesfully demonstrate controlling a lamp connected to an arduino connected to a wifi network with our controller code and front end receiving and reacting to the events. The steal of the show was the discovery of the lamp thing (we had our fingers crossed) which worked flawleslly! It was agnostic to our code and controller. Our code had never before seen the device. Upon turning on the lamp thing (lamp -> relay -> arduino with our code -> esp 8266), SmartX was able to discover the device and it showed up on our Asgard UI where we were able to configure it for future use.

This is all of course still very early prototype,very hackish. A lot of things didnt work as we expected them to and we had to leave them out.The Scarab library is still not finished yet and needs some major toolchaining and polishing before we can put it out in the open but all in all,it was a great experience for we now have a clear idea of what to do next and how we wish to achieve it. 


Warp speed ahead!
---------------------------------------

Now that we have a fair understanding of how most things work,our next immediate steps will be to

1.Introduce a reactive-ish framework

2.Focus on security

3.Introduce more means of communication besides WiFI

Watch this space for more.


[presentation]: https://docs.google.com/a/thoughtworks.com/presentation/d/1ysq87JS3PwYfoksgjF3MAndatUmeUQLwNZXfH23RTGs/edit?usp=sharing 
[Github-repo]: https://github.com/ThoughtWorksIoTGurgaon
[Showcase]: https://www.fuzemeeting.com/replay_meeting/0890ae9a/7751766
[smartx-image]: http://i.imgur.com/YrU0d8O.png?2


