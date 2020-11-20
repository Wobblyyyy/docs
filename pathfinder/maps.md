---
layout: default
title: Pathfinder Maps
parent: Pathfinder
nav_order: 2
---

# Maps Guide
Maps are most likely the most confusing topic in this library. I'm fairly certain that just about
anybody who's competent enough to use code understands what a map is. Just in case you didn't know...
> a diagrammatic representation of an area of land or sea showing physical features, cities, roads, etc.
Now you know. Regardless, maps, in this context, have an even cooler definition.
> A set of `Zone`s, composed of the even simpler `Shape`s, which indicate the extents and bounds of 
> different areas of the field.
Maps use Euclidian geometry, of course. So how do we make our own?

## A quick disclaimer
Unless you absolutely have to, you really shouldn't be making your own map. There's just about a million
maps for a million different scenarios already included in this library, under the maps package in this
library. For that reason, I'm going to expect that if you're continuing along in effort to create your own
map, you're willing to read the documentation and do your own research on what's going on.

## Creating a new map class
Below is an example of a class that extends map with nothing in it.
```java
public class ExampleMap extends Map {
  public ExampleMap() {

  }
}
```
Now, obviously, we need to add stuff to the map. The method we call to do so is...
```java
fieldZones.add();
```

## Creating a shape and a zone
Let's define a [zone](https://github.com/Rumblebots/UltimateGoal/blob/master/TeamCode/src/main/java/org/_11253/lib/odometry/fieldMapping/zones/Zone.java).
In case you couldn't tell, you can click on that link if you're confused as to what a zone is. Anyways.
```java
public class ExampleZone extends RectangleZone {
  @Override
  public String getName() {
    // The name of the zone, used for mostly debugging purposes. 
    return "ExampleZone";
  }

  @Override
  public Shape getParentShape() {
    // A two-dimensional virtualized Euclidian shape, designed to
    // outline the extents/bounds of the zone in question.
    // In effort to save myself a bit of typing, here's what the parameters mean,
    // taken directly from the JavaDocs.
    /*
     * @param drawCorner           which corner the rectangle should be drawn from. This is NOT
     *                             always the same corner which the rectangle will be rotated from,
     *                             however - just the corner it'll be drawn from. X and Y are relative
     *                             to this corner, meaning top right's Y draw would have a different
     *                             impact than bottom left's Y draw - one (top right) would be negative,
     *                             and the other (bottom left) would be positive.
     * @param rotateCorner         the corner which the rectangle will be rotated from. You don't need
     *                             to rotate the rectangle, by the way - it's an entirely optional step.
     *                             If you don't want to rotate the rectangle, you can use any corner
     *                             (CENTER or maybe your drawCorner) as the corner of rotation, and set
     *                             the rotation angle to 0, representing a net change of zero rotation.
     * @param startingPoint        the coordinate where the shape will be drawn from. This point is
     *                             directly correlative to drawCorner - having a drawCorner of top right
     *                             means that this code will interpret the starting point as the top right
     *                             corner of the rectangle, and thus draw the rectangle as so. Make sure that
     *                             this is the correct corner. Assuming you're familiar with something such as
     *                             JavaScript's "canvas" functionality, you will (most often) want to use the
     *                             top left corner as a starting point and figure out the coordinate of
     *                             said corner.
     * @param xDraw                how far, in the X dimension, the rectangle should be drawn. Note that this
     *                             is relative to which corner the rectangle is being drawn from. Having a draw
     *                             corner of top left means that both X and Y draws are negative.
     * @param yDraw                how far, in the Y dimension, the rectangle should be drawn. Note that this
     *                             is relative to which corner the rectangle is being drawn from. Having a draw
     *                             corner of the top left means that both X and Y draws are negative.
     * @param rotationalAngle      the angle at which the entire rectangle should be rotate from. I believe that
     *                             this angle is in radians, and any code you write using this angle should reflect
     *                             that. If you have an angle which is in degrees, Java's native math class should
     *                             include a function for converting degrees to radians.
     * @param isCollidableExterior whether or not the exterior of the rectangle is collidable. A collidable shape
     *                             is recognized by the collision detection system, and the robot will intentionally
     *                             not steer right into an exterior collidable object.
     * @param isCollidableInterior whether or not the robot can still move while inside a shape. For example, the main
     *                             field of the FTC challenge has a non-collidable interior, meaning the robot can
     *                             still move while inside of the shape / zone.
     */
    return new Rectangle(
      Rectangle.Corners.BACK_LEFT, // drawCorner 
      Rectangle.Corners.CENTER,    // rotateCorner 
      new Coordinate<>(0.0, 72.0), // startingPosition
      Geometry.tileSide,           // the width of one tile 
      Geometry.tileSide,           // the width of one tile 
      0,                           // the angle the rectangle should be rotated at 
      false,                       // whether or not the exterior is collidable 
      false                        // whether or not the interior is collidable 
    );
  }

  @Override
  public int getZonePriority() {
    // The priority the zone has. Remember, higher numbers mean higher
    // priority and will override the effects/names of other zones. 
    return 1;
  }
}
```
That code above us will create a brand-new zone with a brand-new rectangle. The zone will be offset
vertically by 72 inches and will have the width and height of one tile.

## Adding zones to the map
Assuming we already have the zone created, we can just add some code to our constructor, so it now
looks like this.
```java
public class ExampleMap extends Map {
  public ExampleMap() {
    fieldZones.add(
      new ExampleZone()
    );
  }
}
```

## Using your new map
Follow the quickstart guide if you're confused about to use maps. Just create an instance of the map
you've created, instead of an instance of one you... well, haven't.