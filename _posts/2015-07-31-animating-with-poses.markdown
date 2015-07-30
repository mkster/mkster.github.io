---
layout:     post
title:      "Animating with Poses"
subtitle:   "A Quick Introduction to Modding Planetoid Pioneers for Beginners"
date:       2015-07-30 12:00:00
author:     "Max"
header-img: "img/assembling/spider4.PNG"
redirect_from:
  - tutposes/
---

<img src="{{ site.baseurl }}/img/poses/Rover Coalition Spider Climber T.png" height="0" width="200" align = "right">
In the following tutorial animate the spider vehicle which we have assembled from a picture in the [previous tutorial](assembling-a-vehicle.html).
If you want to follow along you can drag this blueprint into your game.
<br>

<br>
<br>

##Creating the poses
First create some walking poses which the assembly will fade between one by one later to walk. Make sure you have assigned a master object in the mo properties of one object. Move objects by dragging them. To test your animation click play animation.
<img src="{{ site.baseurl }}/img/poses/1.PNG" align = "middle">
<br>
<br>

##Set up the Lua script
Now lets dive into the scripting. Press edit external script to open the Lua script of the Blueprint.
<img src="{{ site.baseurl }}/img/poses/edit.PNG" align = "middle">
<br>


Set up your Lua script with the Build and Update function like here:
{% highlight lua %}
function Blueprint:Build()
  -- do this once when the object is created
end


function Blueprint:Update()
  --do this every frame (many times a second)
end
{% endhighlight %}
<br>

##Register button inputs
Now setup the joints to make sure they are able to fade to poses later. In addition to that set up some function which get called by the vehicle pilot if he presses the right button.
{% highlight lua %}
function Blueprint:Build()
  --Do this once when the object is created

  --Setup joints
  self:JointSet(""):SetAngularSpringPower(2000)
  self:JointSet(""):SetAngularFriction(50)

  --Setup a variable to check the state of the right button
  self.right = false
  self.ControlRightPress = function(which)
    self.right = true
  end

  self.ControlRightRelease = function(which)
    self.right = false
  end
end
{% endhighlight %}
<br>

##Setup a pose state
Now we create a table which holds all the information about the pose we added: its name, affected joints, current pose, the count of poses in total and the time to fade from one pose to the next. Make sure the joints you want to change all start with the string you set for joints (here "Leg").
{% highlight lua %}
function Blueprint:Build()
  --Do this once when the object is created

  --Setup joints
  self:JointSet(""):SetAngularSpringPower(2000)
  self:JointSet(""):SetAngularFriction(50)

  --Setup a variable to check the state of the right button
  self.right = false
  self.ControlRightPress = function(which)
    self.right = true
  end

  self.ControlRightRelease = function(which)
    self.right = false
  end

  --Put all the information about the pose in a table
  self.poseanim = {}
  self.poseanim.walkRight = {
    name = "Walk Right",
    joints = "Leg",
    state = 1,
    count = 4,
    interval = 0.4
  }
end
{% endhighlight %}

In the update function we check if right button is pressed and then call a function which advances the pose. We define this function next. If no button is pressed all joints of the assembly will fade back to its idle pose.
{% highlight lua %}
function Blueprint:Update()
  --Do this every frame (many times a second)

  --Walk right if the right button is held down
  if self.right then
    self:advancePose(self.poseanim.walkRight)
  else
    self:FadeAngularSpringAnglesByPose("", "Idle 1", 0.04)
  end
end
{% endhighlight %}
<br>

##Advancing the pose
Finally, to put everything together, we define the advancePose() function which fades from one pose to the next if the assembly is not fading to a pose.
{% highlight lua %}
function Blueprint:Build()
  --Do this once when the object is created

  --Setup joints
  self:JointSet(""):SetAngularSpringPower(2000)
  self:JointSet(""):SetAngularFriction(50)

  --Setup a variable to check the state of the right button
  self.right = false
  self.ControlRightPress = function(which)
    self.right = true
  end

  self.ControlRightRelease = function(which)
    self.right = false
  end

  --Put all the information about the pose in a table
  self.poseanim = {}
  self.poseanim.walkRight = {
    name = "Walk Right",
    joints = "Leg",
    state = 1,
    count = 4,
    interval = 0.4
  }

  --Advance pose to the next pose
  function self:advancePose(anim)
    --Get any joint of this group and make sure it exists and finished its pose fade
    local joint = self:GetAnyJointByName(anim.joints)
    if joint and not joint:GetAngularSpringAngleFadingNow() then

      --Advance state counter
      anim.state = anim.state + 1
      if anim.state > anim.count then
        anim.state = 1
      end

      --Advance to next pose
       local pose = anim.name.." "..anim.state
      self:FadeAngularSpringAnglesByPose(anim.joints, pose, anim.interval)

    end
  end

end


function Blueprint:Update()
  --Do this every frame (many times a second)

  --Walk right if the right button is held down
  if self.right then
    self:advancePose(self.poseanim.walkRight)
  else
    self:FadeAngularSpringAnglesByPose("", "Idle 1", 0.04)
  end
end
{% endhighlight %}

And that's it. With this system established it should be fairly easy to add new additional animations to your blueprint. Don't forget to share your creation in #pp-blueprints.
To improve the gait of this robot further an additional joint connection between the feet and legs can be added. Give it a try!
<br>

<img src="{{ site.baseurl }}/img/poses/spiderwalk2.gif" align = "middle">
