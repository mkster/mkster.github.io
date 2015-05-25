---
layout:     post
title:      "How to Make Your First Gun in less than 10 Minutes"
subtitle:   "A Quick Introduction to Modding Planetoid Pioneers for Beginners"
date:       2015-05-20 12:00:00
author:     "Max"
header-img: "img/inMinutes/header.png"
redirect_from:
  - creating-a-gun-in-less-then-10-minutes/
  - creating-a-gun-in-less-then-10-minutes.html/
  - 2015/05/20/creating-a-gun-in-less-then-10-minutes/
---


#Welcome
In this tutorial I will show you how to create a gun in Planetoid Pioneers.

I will walk you through the steps needed to create and test a new gun blueprint and then highlight some of the most important particle parameters to tweak the shots of your gun. No scripting will be required.
<br>
<br>

<!--
#Creating the gun
First we will create the blueprint for your new gun. That means we will choose a picture and a name and then see how to test the gun.
<br>
<br>

###1. Load a rifle from the game
<img src="{{ site.baseurl }}/img/inMinutes/1.png" align = "middle">
<br>
Enter edit mode with F2.
<br>
<br>

###2. Change the look of your gun
<img src="{{ site.baseurl }}/img/inMinutes/changeTex.png" align = "middle">
<br>
The image has to be in a horizontal position like the original image of the gun.
<br>
<br>

###3. Save your rifle under a different name
<img src="{{ site.baseurl }}/img/inMinutes/2.png" align = "middle">
<br>
Make sure the new name starts with "Tool".
<br>

###4. Test your gun
<img src="{{ site.baseurl }}/img/inMinutes/drag2.png" align = "middle">
<br>
Just drag and drop. Repeat this step whenever you change something.
<br>

###5. Choose your bullets to edit
<img src="{{ site.baseurl }}/img/inMinutes/3.png" align = "middle">
<br>

###6. Live preview your changes
<img src="{{ site.baseurl }}/img/inMinutes/4.png" align = "middle">
<br>


<br>
-->

##Create a gun
<img src="{{ site.baseurl }}/img/inMinutes/newBP.PNG" height="0" width="160"  align="right">

First follow these steps to create a new gun.
<br>

<ol>
   <li>Open edit mode (F2) and load one of the rifles from the blueprint library (F6, then double click)</li>
   <li>Save your rifle under a different name</li>
   <li>Double click one of the particles to start editing them</li>
</ol>

<br>
<br>

##Change the properties of the particles to your liking
I will now show you a selection of parameters to play with to create a fun gun. Tweak all these as you like and feel free to dig around yourself. Hover over parameters to see what they do in detail.

Drag your gun from the blueprint library into the game after changes to test it.
<br>
<br>

###1. Change the type of damage
<img src="{{ site.baseurl }}/img/inMinutes/5c.png" align = "middle">
<br>

<!--
###2. Change look of the shots
<img src="{{ site.baseurl }}/img/inMinutes/7.png" align = "middle">
<br>
-->

###2. Change the behaviour of your gun
<img src="{{ site.baseurl }}/img/inMinutes/6c.png" align = "middle">
<br>

###3. Make your gun special
<img src="{{ site.baseurl }}/img/inMinutes/8c.png" align = "middle">
<br>
For some final tweaking you can add a nice image for your gun.
Finally save your gun and you are done.


<br>

##Congratulations!
You learned how to create you own blueprint and how to edit particles to create your own gun.

The next logical step in gun creation is tweaking the script of the gun. By doing so you can change the buttons, make your gun auto aim or change particle parameters on the fly to make a gun shoot faster the longer you shoot it for example.

Most if not all particle parameters have functions which you can call in the script of the gun to tweak them. To do so check out the script of the gun for reference and have a look at the particles section in the documentation at PPTest\Docs\LuaManDocs.html.

Good luck and have fun, if you get stuck please ask.
