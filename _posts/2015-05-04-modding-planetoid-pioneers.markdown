---
layout:     post
title:      "A Quick Introduction to Lua Modding Planetoid Pioneers for Beginners"
subtitle:   ""
date:       2015-05-04 12:00:00
author:     "Max"
header-img: "img/post-bg-06.jpg"
---

Welcome to the first of hopefully many tutorials that will teach you how to make amazing things inside the Planetoid Pioneers editor! I will start off with a very basic object, a grenade, which we will create using both the in-game editor and some introductory Lua scripting.

In addition to reading this tutorial, I highly recommend checking out the C2D documentation for a list of all engine functions. You will find them in PPTest\Docs\LuaManDocs.html. Ctrl + F will be your friend.



##What can you build with Planetoid Pioneers?
A lot. Every blueprint in Planetoid Pioneers (these objects you can build or spawn from the editor) has a Lua script attached to it which controls what it does. Lua is a fast, easy and very accessible scripting language.

<a href="#">
    <img src="{{ site.baseurl }}/img/moddingPP/1.png" alt="Post Sample Image">
</a>


![alt text]("{{ site.baseurl }}/img/moddingPP/1.png")
![alt text]("img/moddingPP/2.png")
![alt text]("img/moddingPP/3.png")


That means you can change a blueprint and make them obey to your code! Of course you can also create entirely new weapons, Pioneers, vehicles, scenarios, enemies with AI and whatever else you can think of with the power of Data Realms’ Crush2D at your fingertips.


##What we are going to do?
Let’s start by turning a regular bomb into a throwable grenade. To do this we will go through every step necessary to create a new blueprint in Crush2D. We will create the blueprint, make it usable by the Pioneer, add Lua script to it and finally have a look at how to find and solve errors.

When we are done you will be able to realize your coolest ideas in Planetoid Pioneers!

Remember, you will need no additional tools for writing code, because Planetoid Pioneers conveniently has a modded version of [ZeroBraneStudio](http://studio.zerobrane.com/) packaged with it which has some extra features for Crush2D development that will be very helpful for you.

Have fun!


##Editor Overview
I am going to give you a quick overview of all the functions the editor has. If you want a more detailed look you can watch [Datas video](http://www.twitch.tv/data01/c/6471768). If you are already familiar with the editor just skip this part.

Objects in Crush2D are grouped into different categories like movable objects, terrain objects, lights, particles, etc. The edit modes are grouped in the same way.

You have one edit mode for each kind of object, where you get extra information about these in the scene and can move them around.


If you want to change something about an object you can open it in the editor (F2). The editor is grouped in the same categories.

In addition to that you have different widows like the help window (F1), the sound window (F4) where you can select sounds and set the volume of the game or the blueprint library (F6) where you select blueprints and spawn or edit them.


##Creating the Blueprint
We will start by creating the Blueprint for our grenade. If you want to skip this part or run into any trouble just jump to “Lua Scripting for Crush2D” and download the complete blueprint there.

Start up Planetoid Pioneers and enter the edit mode(F2). Open the blueprint library(F6) in it look for the bomb click on it and press load to editor. The blueprint (bp), all its particles, joints etc. are now loaded to the blueprint editor where you can change various properties of the object.


Click on the blueprint tab and change the blueprint name to “Tool Grenade” its important that you keep “Tool “ as first letters for all tools because thats how the Pioneer detects what he can pick up at the moment. Set the blueprint type to “Tool”. Feel free to change the texture in objects. Finally click on “save bp” in the top.

Next we have to add joints which will be mounted to the hands of the Pioneer when he picks up the grenade. Or puts it on his back. You can place the joints in the blueprint editor (Ctrl + F2). To do so press the plus button, copy the names from the screenshot, press the # symbol to mount them to the bomb and then place the FG joint on the left and the BG on the right. Make sure 0 as second value like I do so the grenade is held the right way.



Now save your blueprint and scroll down and click on “Script Edit” and then on “edit external script”.



Now ZeroBraneStudio should open with a tab called Tool Grenade.lua. and we can finally start writing our own code!
If you game is stuck now go into ZeroBrane and press Shift + F5 to stop the debugger. I will explain later what that is.

One more tip before the coding starts! Everytime you change the code of your blueprint the scene has to reload (all done automatically on saving the script). That means you will have to watch the emergency dropship crash at the start of the game every time you change code and that will cost time.

To save that time, change your scene for faster testing. To do so save the scene under a different name in the scene editor, open the activity editor and remove all the code there (which places you in the ship at the start every time). Now zoom out and place your Pioneer (he is somewhere in the sky) at the ground and put the grenade next to him so you can pick it up instantly. Remember to save the scene again.












<pre>
  <code class="ruby">
    function Blueprint:Build()
      -- do this once when the object is created
      -- declare some variables
      -- declare some functions
    end


    function Blueprint:Update()
      --do this every frame (~60+ times a second)
    end
  </code>
</pre>


aaaa

{% highlight lua %}
  function Blueprint:Build()
    -- do this once when the object is created
    -- declare some variables
    -- declare some functions
  end


  function Blueprint:Update()
  	--do this every frame (~60+ times a second)
  end
{% endhighlight %}
