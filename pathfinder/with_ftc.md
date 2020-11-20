---
layout: default
title: Pathfinder for FTC
parent: Pathfinder
nav_order: 5
---

##### TABLE OF CONTENTS
1. 
{:toc}

# Pathfinder for FTC
**If you're not already using ftc2 and are planning on writing code specifically for any
given FTC season, you absolutely should be.** If you want to learn a bit more about ftc2
and how to use it, click [here](https://github.com/Wobblyyyy/ftc2).

## Using Pathfinder-ftc
There's another library, titled Pathfinder-ftc, which you can use specifically for the
First Tech Challenge. Obviously, you can feel free to write your own code to implement
Pathfinder and figure out how to use it on your own. However, if you're anything like me,
or most reasonable people, really, there is absolutely no point in spending way too much
time doing something somebody else already did for you. Anyways.

# With ftc2
*As I mentioned earlier, if you're not yet using ftc2, you should really go download it and
start using it. I'm going to be able to provide very much support if you're not using ftc2;
partially because I want to promote my own library, and partially because it's cumbersome to
be asked to debug code I didn't write for a goal I don't need to accomplish.*

You (firstly) need to have any available release or pre-release versions of Pathfinder, ftc2,
and Pathfinder-ftc, as they all work together. If you're using Gradle, you can implement these
libraries as so. The name of the file you'd like to edit is `TeamCode/build.release.gradle`.
```gradle
// Version required for "Pathfinder-ftc":
// Anything over release v1.0.0.
// Go to the official GitHub repository for "Pathfinder-ftc" to figure
// out what the latest available and suggested releases are.
implementation files('libs/Pathfinder-ftc-v0.1.0')

// Version required for "ftc2":
// Anything over release v1.0.0.
// Go to the official GitHub repository for "ftc2" to figure
// out what the latest available and suggested releases are.
implementation files('libs/ftc2-v0.1.0')
```

## Setting up your odometry system
Odometry shouldn't be very difficult to set up. Here's a (very simple) example implementation. 
Note that I'm currently writing this in Notepad in the back of my Spanish class, so I don't
have anything like syntax highligthing. This code might be a bit funky, but I'll correct that
(if it is) as soon as I possibly can.
```java
public class OdoSys implements HlOdo {
  public final double cpr; // Counts per rotation
  public final double dia; // Wheel diameter 
  public final double los; // Left wheel offset 
  public final double ros; // Right wheel offset 
  public final double bos; // Front/back wheel offsett
  
  public final int delay; // How long before async starts working.
  public final int duration; // How long in between async updates.

  // Now for some lovely encoder names. There's a couple things to note here.
  // Encoders can't really be plugged into their own port - they have to share
  // a port with a motor. rightName should be the name of the motor where it's
  // plugged in. This will usually share a slot with something on your drivetrain.
  public final String rightName; 
  public final String leftName;
  public final String frontBackName;

  // The actual localizer, used to track the position of the robot.
  public final TwLocalizer localizer;

  // Motors, used most frequently for encoder purposes.
  // These are important because... well, encoders in FTC are derivitives of
  // motors, which are... exceptionally cool. It's not really as cool as I'm
  // making it out to be, but oh well.
  public final Motor right;
  public final Motor left;
  public final Motor frontBack;

  public OdoSys(double cpr,
                double dia,
                double los,
                double ros,
                double bos,
                double delay,
                double duration,
                String rightName,
                String leftName,
                String frontBackName) {
    // Set all of our private variables - y'know, it's very fun.
    this.cpr = cpr;
    this.dia = dia;
    this.los = los;
    this.ros = ros;
    this.bos = ros;
    this.delay = delay;
    this.duration = duration;
    this.rightName = rightName;
    this.leftName = leftName;
    this.frontBackName = frontBackName;
    localizer = new TwLocalizer(
      cpr,
      dia,
      los,
      ros,
      bos
    );
    // Set up all three of the motors by acquiring the motors from the absolute
    // hardware map. For obvious reasons, this needs to be done post-init.
    right     = (Motor) Global.getAbsMap().getByName(   rightName   );
    left      = (Motor) Global.getAbsMap().getByName(    leftName   );
    frontBack = (Motor) Global.getAbsMap().getByName( frontBackName );
  }

  // Required method to get the position of the robot. 
  @Override
  public HeadingCoordinate<Double> getPosition() {
    return localizer.position;
  }

  @Override
  public void enableAsync() {
    localizer.enableAsync(
      right,     // The right motor/encoder.
      left,      // The left motor/encoder.
      frontBack, // The front/back motor/encoder.
      delay,     // Delay before updates start.
      duration   // The delay between two updates.
    );
  }

  @Override
  public void disableAsync() {
    localizer.disableAsync();
  }
}
```
Everything there should be fairly self-explanatory. Create a new HlOdometry (which means
High-Level) and get everything set up. I'm tired and incredibly hungry and don't feel like
explaning any of this any more than I already did. If you don't understand, that sucks fory
you - good luck.