---
layout: default
title: Quickstart
parent: Pathfinder
nav_order: 3
---

# Quickstart
First, you should go check out the installation guide. Unless you are entirely
confident you already know what you're doing, it's a great idea to go ahead and
read through the installation before you continue. The installation guide can be
accessed using the sidebar on the left.

##### TABLE OF CONTENTS
1. 
{:toc}

## Getting familiar with Pathfinder
Pathfinder is an expansible and extensible library for dynamic path generation
and playback. Unlike similar libraries, such as ACME Robotics RoadRunner,
Pathfinder is designed to be as close to a drag-and-drop solution as possible.

## Generating your First Path
You, unfortunately, won't have some magic method that you can just run, and your
robot will immediately do whatever you ask it to. However, it's almost as easy.
Almost. There are two ways you can handle some pre-requisites to path generation,
which are as follows.
- Controllable drivetrain
- Accurate odometry
- Robot dimensions:
  - Wheelbase (horizontal)
  - Wheelbase (vertical) (also known as trackwidth)
- Robot motion profile:
  - Acceleration and deceleration distances (feet) and times (seconds)
  - Maximum jerk
  - Maximum speed (feet per second)

All the stuff you need (or might want) is detailed (very thoroughly) in
the PathfinderConfig class (`me.wobblyyyy.pathfinder.config.PathfinderConfig`).

### Pre-Made / Custom Drivetrains
You can either use a pre-made drivetrain that's been configured and tested to
work for robots of a defined drive type, or create your own drivetrain that
handles driving on its own.

#### Pre-Made
Several drivetrain types are available, such as...
- Tank Drive [(here)](https://wobblyyyy.github.io/JavaDocs/Pathfinder/me/wobblyyyy/pathfinder/drive/tank/Tank.html)
- Swerve Drive [(here)](https://wobblyyyy.github.io/JavaDocs/Pathfinder/me/wobblyyyy/pathfinder/drive/swerve/Swerve.html)
- Meccanum Drive [(here)](https://wobblyyyy.github.io/JavaDocs/Pathfinder/me/wobblyyyy/pathfinder/drive/meccanum/Meccanum.html)

Information on how to create and use these pre-made drive classes is available in the JavaDocs
of the class, as well as in the examples section of code.

#### Custom 
Creating a custom drivetrain, although more challenging, gives you a better degree of
control over your robot's operation. There's an interface for drivetrains that allows you
to use whatever drivetrain you'd like named "Drive", which is available right
[here](https://wobblyyyy.github.io/JavaDocs/Pathfinder/me/wobblyyyy/pathfinder/drive/Drive.html).

### Pre-Made / Custom Odometry
Odometry is (rather obviously) needed to track the position of your robot.

#### Pre-Made
A couple of different pre-made odometry classes are available for your use. Due to the nature
of some drivetrains, notably meccanum, accurate positional tracking based on drive motors is
not always an option. Positional tracking for a swerve drive is significantly easier. Tank drive
is the easiest (and most reliable). Another option is two or three wheel unactuated odometry,
which allows for you to track the robot's position pretty accurately. 
- Swerve [(here)](https://github.com/Wobblyyyy/Pathfinder/blob/master/src/me/wobblyyyy/pathfinder/tracking/swerve/SwerveChassisTracker.java)
- Three-Wheel [(here)](https://github.com/Wobblyyyy/Pathfinder/blob/master/src/me/wobblyyyy/pathfinder/tracking/threeWheel/ThreeWheelChassisTracker.java)

#### Custom 
You can create your own odometry system by implementing
[this](https://github.com/Wobblyyyy/Pathfinder/blob/master/src/me/wobblyyyy/pathfinder/robot/Odometry.java)
interface. Update should update the system's position, and will be called as frequently as
possible (several hundred times per second), and getPos should get the robot's position.

## Generating your First Path, Actually
Now that you have everything set up, let's walk through an example implementation of the
pathfinder. Note that this is simply a test class designed to generate a path and follow it.
There's no other implementation, meaning this wouldn't run on an FRC or FTC robot without
further configuration. More examples are avilable in the examples section.
```java
public class SimplePathfinderExample {
  private static final PathfinderConfig pathfinderConfig =
    new PathfinderConfig(
      // pathfinder options go here 
    );

  private static final ArrayList<HeadingPoint> points = new ArrayList<>() {{
    add(new HeadingPoint(
      0, 0, 0
    ));
    add(new HeadingPoint(
      10, 0, 0
    ));
    add(new HeadingPoint(
      10, 10, 0
    ));
    add(new HeadingPoint(
      20, 20, 0
    ));
    add(new HeadingPoint(
      30, 40, 0
    ));
  }};

  private final Pathfinder pathfinder;

  public SimplePathfinderExample() {
    pathfinder = new Pathfinder(pathfinderConfig);
  }

  @Test
  public void generatePath() {
    // Generate a path and drive the robot to the target
    pathfinder.goToPosition(points.get(3));

    // Lock the current thread until the pathfinder has finished
    pathfinder.lock();
  }

  @Test 
  public void generateWaypointedPath() {
    // Generate several paths and link them together and follow it 
    pathfinder.followPath(points);

    // Lock the current thread until the pathfinder has finished
    pathfinder.lock();
  }
}
```