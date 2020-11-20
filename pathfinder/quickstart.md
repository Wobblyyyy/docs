---
layout: default
title: Pathfinder Quickstart
parent: Pathfinder
nav_order: 3
---

# Quickstart
First, you should go check out the installation guide. Unless you are entirely
confident you already know what you're doing, it's a great idea to go ahead and
read through the installation before you continue. The installation guide can be
accessed using the sidebar on the left.

# Writing some code
Just to make sure we're all on the same page here. All (or at least the very vast majority of (even private)) of the methods,
classes, and whatever in between, included in this library is documented. Of course, these JavaDocs are available in this
GitHub repo - check out [this page](https://pathfinder.wobblyyyy.github.io/web/docs/pathfinder) if you're interested in
those - and I'd suggest you familiarize yourself with as much of the documentation as you can, just so you have an easy time
figuring out how this library works. Also, if you're reading this, instead of watching a video, I mean... congrats, I'd
definitely pick the video, but anyways...

## Creating an odometry implementation
Included in this pathfinder library is an interface used for Odometry. If you're using ftc2, which you very definitely should
by the way, you can just use one of the prebuilt odometry implementations designed specificially for the robots of the First
Tech Challenge. However, if you're not using ftc, you should just continue reading this.

### Hardware-related stuff
Create a new class with whatever name you'd like. For the purpose of this tutorial, the class is named (and spoken of as)
the very simple `TwOdometry` (Three Wheel Odometry) and make sure it implements `Odometry` (which is of the package
`me.wobblyyyy.ftc2.ext`, so `me.wobblyyyy.ftc2.ext.Odometry`) and all the methods contained within it.
You need to make the following.
1. A way for the encoders to be initialized. 
2. A method (named `getPosition()`) that returns a `HeadingCoordinate<Double>`, representing the position of the robot.
HeadingCoordinate is of the package `me.wobblyyyy.pathfinder.fieldMapping.components` and represents a coordinate. It should
also be noted that this coordinate represents the very center of the robot. The heading is also stored in radians, not degrees.
If you're unfamilar with radians, you should do some research into radians and the unit circle before you keep going.
3. A lot of swag. Really, all the `Odometry` interface requires is a `getPosition()` method. Of course, if you're using the
`ftc2` library, which you definitely should be, by the way, this can all be streamlined into only a couple lines of code you
need to write. But if you don't want to budge, you can do it this way and it should work just as well.

### What the hell is a `Map`?
Maps are, put simply, virtualized representations of the playing field. It's very likely that you don't need to create your
own map - I try to keep maps updated all the time, and they can be used pretty easily. If, for example, you want to use the
map of the 2020-2021 season, you can just import the class `me.wobblyyyy.pathfinder.fieldMapping.maps.ultimategoal.UltimateGoalMap`
and get started from there by creating a new instance of MapApi with an instance of this map. Ex. 
```java
/**
 * An instance of the field's map.
 */
private final Map map = new UltimateGoalMap();

/**
 * An instance of the mapping system's API, using the field's
 * map in the constructor.
 */ 
private final MapApi mapApi = new MapApi(map);
```

##### Setting up the autonomous map functionality
It would be a bit tedious to have to manually update the position of the robot every single time it changed. Thankfully, I decided
to make this beautiful bit of code do that for us.
```java
    /**
     * Schedule an asynchronous updater to automagically update the
     * position of the robot's odometry subsystem for us.
     *
     * @param odometry the instance of odometry to use.
     * @param duration how long in between updates.
     */
    public void scheduleAsync(final Odometry odometry, int duration) {
        StringEvents.schedule(
                mappingName,
                duration,
                0,
                new Timed() {
                    @Override
                    public Runnable open() {
                        return new Runnable() {
                            @Override
                            public void run() {
                                update(odometry.getPose());
                            }
                        };
                    }
                },
                true
        );
    }
```
That'll just update the odometry asynchronously for us. This means that we can focus on the more interesting
part of the mapping interface - actually relating the robot to the map itself. So, in conclusion, in order to
actually schedule the asynchronous map updater, we have to do the following.
```java
// This is just an example constructor - MeccanumDrive should be whatever class you're using, not just this.
public MeccanumDrive() {
  waitForStart(); // if you're not using ftc2, you need to wait until everything actually starts happening
  mapApi.scheduleAsync(
    odometry, // this should be the name of whatever your odometry system is
    100 // this can be however long you'd like. note that this time is in ms
  );
}
```

##### Getting the position of the robot, using a Map
Now that we've set up the map, and it should be updating on it's own, we're going to want to get the position of
our robot. If we just want to get the position of the robot, we can just do this.
```java
telemetry.addData("Position", odometry.getPosition().asString()));
```
But, if we'd rather get the more complex position provided via `MapApi`, the position info that includes all of the
areas of the map the robot is currently inside, we can do the following.
```java
telemetry.addData("Position", mapApi.getPositionsString());
```
The `MapApi` file is available [here](https://github.com/Rumblebots/UltimateGoal/blob/master/TeamCode/src/main/java/org/_11253/lib/odometry/fieldMapping/MapApi.java), 
just for reference. This will return...
> @return the list of zones the robot is in
... which can then obviously be used to do some pretty cool things. 