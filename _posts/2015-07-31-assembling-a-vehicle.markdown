---
layout:     post
title:      "Assembling a Vehicle"
subtitle:   "A Quick Introduction to Modding Planetoid Pioneers for Beginners"
date:       2015-07-29 12:00:00
author:     "Max"
header-img: "img/assembling/spider4.PNG"
redirect_from:
  - tutvehicle/
---

In this tutorial we will assemble a working blueprint from this picture drawn by our artist [Arne](http://androidarts.com).
<img src="{{ site.baseurl }}/img/assembling/ClimberSpider.png" align = "middle">

This is the source image I assembled from this which has to have a transparent background and all flipped parts on it.
<img src="{{ site.baseurl }}/img/assembling/Rover_Spider2.png" align = "middle">

<br>
<br>

##Creating the Blueprnt
Start by opening the editor(F2) and create a new blueprint with the button at the bottom.
<img src="{{ site.baseurl }}/img/assembling/1.PNG" align = "middle">
<br>

Then enter a name and type and save it.
<img src="{{ site.baseurl }}/img/assembling/2.PNG" align = "middle">
<br>

##Assigning a texture
Make sure to save your image in the "Textures" folder in the game root.
Next add an object by clicking the plus button and assign your texture from the texture library(F3).
<img src="{{ site.baseurl }}/img/assembling/3.PNG" align = "middle">
<br>

##Setting up the objects
Copy your added object a few times. Then name the objects and assign textures by clicking them on the picture.
<img src="{{ site.baseurl }}/img/assembling/4.PNG" align = "middle">
<br>

##Position the objects
Now allign the parts in the Blueprint editor. Manage layers with the arrow up and down button. Tune the positions precisely by entering exact coordinates at bottom.
<img src="{{ site.baseurl }}/img/assembling/5.PNG" align = "middle">
<br>

##Add joints
Change into joint edit mode and select "Add". Click to add joints. Check your added joints in 3D mode and delete unnecessary joints. Make sure to add a joint called Mount Pilot with no B object for vehicles which will connect the pioneer with the vehicle.
<img src="{{ site.baseurl }}/img/assembling/6.PNG" align = "middle">
<br>

Click somewhere in the game to spawn your blueprint with the insert button. The blueprint is now assembled but lacks proper joint and material properties. Thats what we are going to do next.
<br>

##Set the joint properties
Double click joints to edit them. Tune angular friction to make joints move harder. Tune angular spring to hold the joint angle in place. Make the "Mount Pilot" joint a mount joint.
<img src="{{ site.baseurl }}/img/assembling/7.PNG" align = "middle">
<br>

##Set the object proprties
Set a material, the thickness(depth) and the hollowness of each objects to define its weight and behavior.  
<img src="{{ site.baseurl }}/img/assembling/8.PNG" align = "middle">
<br>

This is it. You should now have a mountable vehicle. Check out [the next tutorial](animating-with-poses.html).to find out how define poses to animate it and write a Lua script to make it drivable.

<br>
<img src="{{ site.baseurl }}/img/assembling/spider5.PNG" align = "middle">
