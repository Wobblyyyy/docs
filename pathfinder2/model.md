---
layout: default
title: Pathfinder's Model
parent: Pathfinder2
---

# A Definitive Pathfinding Model
The following is an excerpt from Pathfinder2's official design
documentation. There's a little bit of reformatting, etc.

##### TABLE OF CONTENTS
1. 
{:toc}

## Introduction
There are only a couple of things I know.
- I could really go for a couple of Oreos right now. Especially if they’re the double-stuffed ones. I mean… come on. Can you really say no to some double-stuffed oreos?
- Pathfinder is going to be rebuilt from the ground up.
- Pathfinder is going to become a lot better.
- I’m going to plan out the entirety of Pathfinder before writing a single line of code.

Every time I work on a project, I’ll figure out a solution, I’ll spend 
hours implementing it, and then a week later I’ll realize the whole thing 
sucks and I need to re-do it. I want to avoid that. Part of the reason 
Java became a staple of the programming world is because it was built 
expertly by a team of qualified programmers. The entire language is 
strictly planned out and incredibly logical and organized. C and C++ 
never shared those same advantages - just look at how C++ implements 
classes. They feel very awkward and uncomfortable to use, unlike Java’s 
incredibly natural declarative syntax.

So if I plan everything out beforehand, I can avoid the “oh well, I did 
this all wrong, but I’m too lazy to fix it” that I run into all the time. 
Thus, this section is going to declare a definitive model for how Pathfinder 
will operate. This isn’t going to be a pseudocode section. This isn’t going 
to be a code section. This is going to explain the operation of Pathfinder 
in English, in a way that makes sense, and in a way that I can explain it 
to other people (and even myself) as I’m about to do now.

The plan is as follows. After defining Pathfinder in a definitive model, 
I will build exactly what I said I would. I won’t change it in the slightest. 
It will function exactly as I’d like it to and it will do exactly what I wanted 
it to do. Documentation can’t become deprecated if the project doesn’t change. 
Hopefully I don’t come up with something stupid. Hopefully.

## Redefinition of Movement
Pathfinder is described as an “autonomous motion planning” library or something of the sorts. This is true and will, unless something goes seriously wrong, remain true. However, I believe it would make sense to further abstract movement and give Pathfinder complete control over movement - both autonomously operated and manually operated. You may be wondering… why would anyone want to do this?

As of now, it can be challenging to differentiate between user-given instructions and non-user-given instructions during a manual operation period. A very temporary workaround that we’ve implemented for the 2020-2021 season is putting the robot in two different modes - user controlled, meaning only the user can control the robot, and non user controlled, meaning only Pathfinder can instruct the robot on how to move. Pressing a button (A, B, X, or Y in our case) will “tell” the robot to go to a certain position. Specifically for the 2020-2021 season, those aforementioned buttons could be used to automatically align the robot with a specific target. The robot will remain in this autonomous navigation mode until it either reaches its target position or receives a command instructing it to stop moving entirely. (For the purpose of detailing this fully, pressing the right bumper would cause the robot to stop)

If we abstract movement away from manual control (you no longer set power to each motor individually, rather, you tell the robot to move a certain way and it does it for you) we can avoid any and all issues induced by attempting to operate the robot bimodally. 

### Relative translation-based movement
Our model depends on relative translations. For the purpose of explanation, let’s define a relative translation (“transformation,” if you will) as the following.

> A relative transformation can be represented as an object with several attributes.
> 
> Transformation along the X axis. (“vX”)
> Transformation along the Y axis. (“xY”)
> Rotation from the center of the robot. (“vZ”)

Alright. So we’ve defined what a relative translation is. And we know how it works. There’s a couple more things I’d like to clarify just so this is very clear. Translations are always relative to whatever the robot’s current position is. When the robot moves, its position will change. However, the robot’s current position is always defined as the origin - (0, 0) with a heading of 0. So no matter what direction you want the robot to go in, instructing it to follow a relative transformation with the following values:
- vX: 0
- vY: 1
- vZ: 0
… will cause it to move forwards. Remember, this “forwards” is defined relative to the robot. If the robot is facing π/2 (90 degrees to the left) , instructing it to go forwards (vX = 0, vY > 0, vZ = 0) will cause it to move, relative to an absolute origin, to the left. This probably sounds a lot more complicated than it actually is.

### Absolute movement
Absolute movement is where things get a little bit more complicated. This is also where what makes Pathfinder so useful really shines. 

Given we know a relative transformation is composed of three translational components, (vX, vY, and vZ) we can convert these movements into an absolute transformation given we know the current angle of the robot. Remember how I said if the robot turns 90 degrees to the left, telling the robot to go forwards would actually make it go leftwards, relative to an absolute position? We don’t have to do that anymore. We can convert this relative movement to an absolute movement, so long as, and only so long as, we know the angle the robot is currently facing.

Let’s define a couple of terms.
The translation’s magnitude (total translation distance) is equal to (vX*vX)+(vY*vY). If you’ve taken geometry before, you may recognize this as “the distance formula.” The translation’s angle (which we’ll call θ) is equal to tan-1(y, x). Note that atan2 is a computational method and not a mathematical function. If we can define the transformation as a power value and an angle value (how far to move and in what direction) we can adjust these values to make them relative to wherever the robot actually is.

You can convert these values (“P” is the magnitude” and “θ” is the angle) back into component vX and vY values as so:
vX = Pcosθ
vY = Psinθ

Let’s call the robot’s current heading (what direction it’s facing relative to its center - 0 degrees would be straight forwards, 90 degrees would be straight leftwards, 180 degrees would be straight backwards, 270 would be straight rightwards) “Ω”. If we already know we can calculate the vX and vY values based on the magnitude (P) and the angle (θ) we can also add Ω to θ to get a new angle which we can use for absolute power purposes.

So, to summarize.
vX = Pcos(θ+Ω)
vY = Psin(θ+Ω)

So, in full, we have the following.
vX = sqrt(cos(θ+Ω)x^2+y^2)
vY = sqrt(sin(θ+Ω)x^2+y^2)

Because vZ is always relative to the center of the robot’s rotational axis, we don’t have to worry about converting it. Absolute movement for the win!

## Omnidirectional movement in application
Alright. So let’s say we have a robot capable of moving in any direction we’d like. Our robot can be defined as follows:

This robot can accept one single parameter - a translation.

A translation is defined as…
> vX (x translation component)
> vY (y translation component)
> vZ (rotation about the center of the robot)

Based on this translation, the robot will move accordingly.

### Arctangents and Magnitudes 
Java’s Java Platform SE 8 JavaDoc says the following about a method named “atan2(double, double)”:

> static double
> atan2(double y, double x)
> Returns the angle theta from the conversion of rectangular coordinates   (x, y) to polar coordinates (r, theta).

In essence, this method will return an angle based on a Y and X value. This angle will always be measured in radians and will always fit within the bounds 0 to 2π, inclusive. To go further, we need to define a couple of things.

#### Point
> A point is defined as a pair of double coordinates, each representing an X and Y value.
> 
> X - Offset from the origin ((0, 0)) along the X axis, from the Y axis.
> Y - Offset from the origin ((0, 0)) along the Y axis, from the X axis.
> 
> Points can be extended with a heading (which we’ll name “Z”), but that’s something we’ll have to figure out later. I can tell you’re excited, aren’t you?

#### Math with Points 
Here. I’ll give you a sneak-peak into some code that we’ll end up using.

```java
public static Angle angleTo(PointXY a,
                            PointXY b) {
    return Angle.fromRad(
        Math.atan2(
            distanceY(a, b),
            distanceX(a, b)
        )
    );
}
```

Fun, right? distanceY is a method that subtracts the Y value of A from the Y value of B. distanceX is a method that subtracts the X value of A from the X value of B. This might be a little bit confusing, and I do apologize, but just know that this method will return the angle from point A to point B.

Remember the section on “Absolute movement” and how you can translate an absolute translation to a relative translation if you know the robot’s current heading? That’s coming back here. Crazy, right?

Our absolute movement section requires a magnitude and an angle. With both of those, we can determine a relative translation for the robot to make in order for it to do anything. 

Remember how our robot accepts relative translations, and, from there, it can move in any which direction? Yeah. It does. And remember how we can generate relative translations based on absolute translations if we know the heading of the robot? I’m sure you do. Can you see where this is going yet? Hopefully.

And finally, let’s define a target point. For now, our target point will be (10, 10). The units here don’t matter - just the fact that the target point is, in fact, a point.

There’s a couple steps we can take here.
- Based on the robot’s current position (X and Y values) and the target position (once again, it’s (10, 10) in this case just for demonstration purposes) we can determine the angle between the two points using the “angleTo(PointXY, PointXY)” method we defined earlier on.
- With the robot’s heading and a desired angle, we can convert an absolute translation, given in the form of magnitude and angle, into a relative translation.
- Our robot accepts relative translations - so now that we’ve determined a relative translation, we can make our robot drive exactly as we want it to.

If the robot starts at (0, 0) and has a target of (10, 10), we would obviously have to move at a 45 degree angle. A triangle with equal legs and a hypotenuse equal to a * sqrt(2) is a 45-45-90 triangle, so the robot needs to move at a 45 degree angle.

If it does move at this angle, and it continues doing so infinitely, it will eventually reach the target point. So long as it continues moving at this 45 degree angle, it’s position will go like…
- (0, 0)
- (1, 1)
- (2, 2)
… and so on and so forth. 

This is all perfectly logical and makes sense. But if the robot’s position were to suddenly change - say it moved from (0, 0) to (0, 1), the robot would have to move at a different angle to reach the same point. Which is where Pathfinder comes in. It would be very easy to calculate all of this beforehand and run an autonomous program that will run at a specific angle for a specific amount of time. Pathfinder takes that a step further. By constantly determining where the robot is on an imaginary coordinate plane, the robot can constantly determine how it can go to a specific target point. So if you run these calculations repeatedly - say, hundreds of times per second - the robot will always be able to go to a target, even if it gets knocked off course.



##### Drive 
Accepts a relative translation and drives the robot appropriately according to the translation.

##### Odometry 
Provides a point (with an X and Y component). Provides a heading (the direction the robot is facing).

## Basic Movement
Let’s recap everything we’ve gone over so far, shall we?

If we can use odometry to determine the position of the robot, and if we can use a physical drive train to control where the robot is, we can therefore control where the robot is by feeding it whatever points we’d like it to. Ignoring all of the physical limitations driving a robot has - velocity, slip, etc - and focusing solely on the kinematics aspect of our problem, we can tell the robot to go wherever we’d like it to and it will do exactly that. 

That’s a pretty cool concept, right? In essence, we’ve created an imaginary coordinate plane that the robot can move along. We can tell it where we want it to go and it’ll go there. This on its own is transformative for most robotics groups. If you have no way of controlling your movement, and you can suddenly tell your robot to go wherever you want it to and it’ll do exactly that, your potential for autonomous capabilities is expanded infinitely. 
