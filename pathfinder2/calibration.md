---
layout: default
title: Calibration
parent: Pathfinder2
---

Calibration is among the most important steps you'll need to take in order
to utilize Pathfinder as intended. It's also one of the most boring.

##### TABLE OF CONTENTS
* TOC
{:toc}

# What is calibration?
Calibration, in the context of Pathfinder, is the process of making sure your
robot's hardware and software are synced up (I know that's a terribly
non-technical way of explaining it, I'm sorry but I can't think of anything
better at the moment). You have to ensure that when you tell your robot to
drive forwards, it will drive forwards. You must also ensure that your robot
is correctly tracking its own position.

# Calibration guide
Unfortunately, this isn't a clearly-defined process: you're just going to sort
of have to figure it out, you know?

## Steps to calibration
1. Calibrating odometry
2. Calibrating drive train
3. Syncing both up

### Calibrating odometry
You need to make sure your robot correctly reports its position. Because
odometry can vary so much, the way you'll have to calibrate your odometry
system differs based on what robot you're working with.

Pathfinder makes calibrating your odometry system (relatively) easy.

#### Implementing `AbstractOdometry`
You absolutely could implement the `Odometry` interface yourself, but it's
not a very fun experience: there's a lot of methods. Instead, you should
extend `AbstractOdometry`, just like this:
```java
public class ExampleOdometry extends AbstractOdometry {
    @Override
    public PointXYZ getRawPosition() {
        // your odometry code goes here. this method should return the robot's
        // position, without modifying it in any way

        return new PointXYZ(0, 0, 0);
    }
}
```

#### Testing your odometry implementation
Now that you've implemented odometry, it's time to test it.
```java
public class ExampleOdometryTester {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();

        while (true) {
            System.out.println(odometry.getPosition());
        }
    }
}
```

Instead of using standard output, you should definitely check out a better
tool.

##### FTC
Use `Telemetry`.
```java
public class ExampleOdometryTester extends OpMode {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();

        while (true) {
            telemetry.addData("position", odometry.getPosition());
            telemetry.update();
        }
    }
}
```

##### FRC
Use `SmartDashboard`.
```java
public class ExampleOdometryTester {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();

        while (true) {
            SmartDashboard.putString("position", odometry.getPosition());
        }
    }
}
```

#### Fixing broken odometry
Unless there's a hardware issue or you're using some bad math, odometry will
always be fixable. Pathfinder provides a very easy way to do exactly that:
check out "modifiers."

##### What's a modifier?
A modifier is a function that modifies a value. Odometry uses this to allow
you to virtually offset your position - you can make your robot "think" it's
at (0, 0) when it's really at (10, 10).

A modifier is defined technically as a `Function<T, T>`. `T` can be any type.
The function should take one instance of `T` as a parameter and return a
modified version of that parameter.

Java's lambda syntax makes modifiers very easy to make. Here's an example of
a modifier that does nothing at all:
```java
public class ExampleModifier {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();
        odometry.setModifier((position) -> {
            return position;
        });
    }
}
```

... and here's an example of a modifier that swaps the X and the Y values
of the robot's position. This is done quite commonly to make odometry
systems more workable for a given environment.
```java
public class ExampleModifier {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();
        odometry.setModifier((position) -> {
            return new PointXYZ(
                position.y(),
                position.x(),
                position.z()
            );
        });
    }
}
```

#### Creating a good modifier
When making a modifier, you need to know what you want it to do: you need to
have a problem that requires a solution, and then a solution to that problem.

Here are some of the most common issues you may encounter, and a modifier
to fix it.

##### X, Y, or both is/are inverted
How do you know if one of these values is inverted? Simply log your robot's
position and move it around. If either the X, Y, or both value(s) is/are
moving the wrong way (decreasing when it should be increasing or increasing
when it should be decreasing), you can use a modifier to correct the issue.
```java
public class ExampleModifier {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();
        odometry.setModifier((position) -> {
            return new PointXYZ(
                position.x() * -1, // invert this one
                position.y() * 1,  // don't invert this one
                position.z()       // don't invert this one
            );
        });
    }
}
```

##### X and Y are swapped
Although I've already included a modifier that swaps X and Y, there's no
harm in including it again, right? You can swap the X and Y values by
creating a new `PointXYZ` and inputting the following:

- X: `position.y()`
- Y: `position.x()`
- Z: `position.z()`

Notice how X and Y are simply swapped - yeah, that's just about it.

```java
public class ExampleModifier {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();
        odometry.setModifier((position) -> {
            return new PointXYZ(
                position.y(),
                position.x(),
                position.z()
            );
        });
    }
}
```

##### A combination of inversion and swapped axes
If neither an inversion nor a swap will fix your odometry issues, you might
have to resort to a combination of both of them. This modifier, for example,
will (1) swap X and Y values and then (2) invert the NEW Y values.
```java
public class ExampleModifier {
    public void testOdometry() {
        Odometry odometry = new ExampleOdometry();
        odometry.setModifier((position) -> {
            return new PointXYZ(
                position.y(),
                position.x() * -1,
                position.z()
            );
        });
    }
}
```

### Calibrating drive train
Drive train calibration is very similiar to odometry calibration. You just
need to make sure your robot goes forwards when you tell it to go forwards
and rightwards when you tell it to go rightwards... you get the point.

#### Verifying orientation
Did you know that motors can have different orientations? The motors on the
right side of a robot's chassis will have the opposite orientation of the
motors on the left side of the robot's chassis.

It's easy to verify orientation: simply write a program that slowly moves
each of the motors, one by one, so you can observe to see which motors are
aligned correctly and which motors are not aligned correctly.

#### Creating a drive train
Implementing the `Drive` interface isn't hard as there aren't very many
methods.
```java
public class ExampleDrive implements Drive {
    private Translation translation = new Translation(0, 0, 0);
    private Function<Translation, Translation> modifier = (t) -> t;

    public ExampleDrive() {

    }

    @Override
    public void setTranslation(Translation translation) {
        this.translation = translation;

        // there should also be code here that actually MOVES the robot
        // for wheeled robots, this is most often spinning a motor (or,
        // more accurately, several motors)
    }

    @Override
    public Translation getTranslation() {
        return translation;
    }

    @Override
    public void setModifier(Function<Translation, Translation> modifier) {
        this.modifier = modifier;
    }

    @Override
    public Function<Translation, Translation> getModifier() {
        return modifier;
    }
}
```

#### Drive train modifiers
These aren't anywhere near as useful as odometry modifiers, so I'm not going
to write too much on them. You can make a modifier that changes the inputted
translations, but there's not much of a reason to do that.

### Testing your calibration
Of course, you're going to need to test your new calibration! This calibration
test works by instructing the robot to move in the positive X direction and
waiting for it to move 2 units (probably inches, meters?) in that direction.
If it doesn't ever move there, the loop will continue infinitely. Afterwards,
it does the same, in the Y direction. After testing both positive X and
positive Y movement, we do the same thing, but backwards: a negative X
direction and a negative Y direction.
```java
public class ExampleCalibrationTest {
    private final Odometry odometry = new ExampleOdometry();
    private final Drive drive = new ExampleDrive();
    private PointXYZ lastPosition;

    public void runTest() {
        PointXYZ position = odometry.getPosition();

        drive.setTranslation(new Translation(1, 0, 0));
        while (position.x() < 2) position = odometry.getPosition();

        drive.setTranslation(new Translation(0, 1, 0));
        while (position.y() < 2) position = odometry.getPosition();

        drive.setTranslation(new Translation(-1, 0, 0));
        while (position.x() > 0) position = odometry.getPosition();

        drive.setTranslation(new Translation(0, -1, 0));
        while (position.y() > 0) position = odometry.getPosition();
    }
}
```
