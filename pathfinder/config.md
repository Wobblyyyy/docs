---
layout: default
title: Configuration
parent: Pathfinder
nav_order: 5
---

# Configuring Pathfinder
Pathfinder has as many configuration options as I could fit while developing it.
I've always been a fan of allowing users to have complete (or near complete)
control over code they're using, so providing many configuration options allows
me to do just that.

##### TABLE OF CONTENTS
1. 
{:toc}

## Pathfinder Configurations
In order to create a new Pathfinder instance, you need a PathfinderConfig.
There's a couple of different configuration classes you can use, but they're
all extensions of the same class:
`me.wobblyyyy.pathfinder.config.PathfinderConfig`

All the options are detailed under that class - however, in an effort to provide
more precise documentation, they're also available here.

### Odometry
Obviously, a robot needs to know where it is in order to anything useful.
The Odometry interface provides a set of standardized methods that allow
Pathfinder to track position. You can create your own odometry subsystem,
or you can use one of the pre-built ones, which I'd definitely suggest. The
"tracking" package contains all the tracking and odometry related code you'd
ever need.

### Field Width and Height
Field width and height are actually fairly deprecated, but I can't remove them
without causing major problems in Pathfinder's operation. The field's width
and height should actually be defined under the field's map, which allows for
a much higher degree of accuracy in seeing the field's size.

### Robot X/Y, Gap X/Y
Robot X and Y are fairly self-explanatory - the width and the height of the 
robot. Height, of course, meaning one of the 2d measurements of the robot. If
you're looking at the robot from a top-down view, X and Y are the robot's
measurements. X and Y are reversible, actually - the robot's X and Y values
are combined into a single hypotenuse-like measurement which is used for
collision detection and prevention, as well as map-scaling.

The robot's gap, X and Y, are a little more confusing. This applies mostly
to swerve drivetrains.
- Gap X: The gap, in inches, between the center points of the left and right
  pairs of drive wheels.
- Gap Y: The gap, in inches, between the center points of the front and back
  pairs of drive wheels.
  
Gap X and Y are, unfortunately, not as reversible as robot X and robot Y.
Tank drivetrains need only the X gap. Swerve drivetrains need both the X and
Y gap. Meccanum drivetrains, obviously, don't need any of those values fed
to them.

### Robot Profile
The robot's profile is essentially a quick reference to what the robot is
physically capable of. All the parameters for robot profiling are detailed
in the JavaDoc and regular documentation for the RobotProfile class.
Click [here](https://github.com/Wobblyyyy/Pathfinder/blob/master/src/main/java/me/wobblyyyy/pathfinder/util/RobotProfile.java)
to learn and see a bit more.

### Drivetrain
The robot's drivetrain is, obviously, very important to the operation of the
robot.
Now, obviously, we both know that a wheeled robot needs to have wheels
to move, right? In order to make the pathfinder able to control the
robot and its movement, we have to give the pathfinder some interface
to control the motors. This is that interface.
Don't create a new drive interface, that would be... really stupid.
Rather, you can (and should) use any of these drivetrains:
 - me.wobblyyyy.pathfinder.drive.meccanum.Meccanum
 - me.wobblyyyy.pathfinder.drive.swerve.Swerve
 - me.wobblyyyy.pathfinder.drive.tank.Tank

### Field Map
Field-mapping is integral to the entire function that Pathfinder desires
to accomplish - avoid solid targets on a map. The field mapping interface
provided in Pathfinder allows you to set up rectangular and circular zones 
that the robot will automatically avoid for you. Map creation and zone
management are both fairly simple topics - if you want to learn more about how
maps work, check out the Map file. If you want to learn more about how to toy
around with maps, check out the documentation guide on that, available via
the side bar on the website you're currently on.

### Follower Type
What type of follower the pathfinder should use. The different types of
followers that available for your use are detailed here:
[(click me!)](https://github.com/Wobblyyyy/Pathfinder/blob/master/src/main/java/me/wobblyyyy/pathfinder/core/Followers.java)

### Pathfinder Types (Lightning, Speed, Theta)
Pathfinder allows you to choose which types of path generation systems are
used. There's currently four.
- Lightning is the fastest finder and should be used whenever possible. This
  finder runs by checking to see if the area the pathfinder needs to traverse
  is empty. If it is empty, no path needs to be generated - we can just use
  the inputted line path.
- Speed is the second-fastest - it runs if lightning fails. It checks to see
  if the robot would collide with any zones if it were to follow the path as
  inputted. If it fails, it moves on to the next pathfinder.
- Theta* and A* are the two big-boy pathfinders. These run if everything else
  fails. The Theta* pathfinder is optimal, as it generates fewer points. The
  A* generates many more points, but is simple and works as intended.

Unless you know what you're doing/what you want, you should leave all three
of these to true. Setting all three of these to true allows for the most
optimal path generation and the least math, which is obviously good for saving
as much CPU time as possible.

> Please note:
> Setting the pathfinder to NOT use the Theta* algorithm forces it to use the
> A* algorithm - although it works, it's very slow and PID followers, etc,
> will follow the generated path incredibly slowly.