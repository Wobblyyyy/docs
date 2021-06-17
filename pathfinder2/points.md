---
layout: default
title: Points
parent: Pathfinder2
---

# Points (PointXY and PointXYZ)
Ahh. How lovely. An entire page dedicated exclusively to
little tiny dots or something like that. Right?

##### TABLE OF CONTENTS
1. 
{:toc}

## Types of Points
There's two main types of points.
- `PointXY`
- `PointXYZ`

The first of those types - `PointXY` - is a simple point with an 
X and Y coordinate. 

The second of those types - `PointXYZ` - is a (also simple) point with
an X coordinate, a Y coordinate, and a Z value. This Z value is an
`Angle` - in other words, it's literally just an angle. That angle 
typically represents a heading.

## Point Functionality
All types of points are immutable, meaning the objects cannot be
modified after being created. This is done to ensure there's no
confusing code with points. If you'd like to find a new point,
you can create a new point instead of simply modifiying an original
point. 

## Point Methods

### Add
Add two points together. For PointXY instances, this method will
return a new point with an X value equal to the sum of the two provided
points' X and Y values. For PointXYZ instances, this method will do the
same, but also add the Z values.

### Multiply 
There's two types of multiplication methods.

#### Multiply by point
This method will do the following.
- New X = X1 * X2
- New Y = Y1 * Y2
- New Z = Z1 * Z2

#### Multiply by number 
This method will multiply the X, Y, and Z values of the point by
whatever number is provided.

### Avg / Midpoint
Get the midpoint between two points. I mean, this one's pretty
simple, right? Average the X and Y values and return a point. If
this method is performed on a PointXYZ instance, it'll also average
the headings. 

### Zero
Create a new `PointXY` or `PointXYZ` with X, Y, and possibly Z values
of zero. This method will always create a new point.

### Distance 
Get the distance between two points. This method uses the distance formula,
something you can feel free to Google on your own time. It's not incredibly
difficult to figure out, and it works. Usually, that is.

### Distance X
Get the difference in X values between two points. This method does not make
use of the distance formula, or any trig, for that manner. Rather, this method
simply subtracts the first X value from the second X value. That's it.

### Distance Y
Get the difference in Y values between two points. This method does not make
use of the distance formula, or any trig, for that manner. Rather, this method
simply subtracts the first Y value from the second Y value. That's it.

### Angle To 
Get the angle to another point. For example, if you have a point at `(0, 0)`
and you perform the "angle to" method on a point at `(1, 0)`, the value
you'll get is 0 degrees. If you do it with `(0, 1)` you'll get 90 degrees.
Makes sense? Hopefully, because my hands hurt and I'm not writing any more
documentation. Sucks to suck, doesn't it?

### In Direction
Create a new point a given distance away in a given direction from an
original point. I mean, the name is pretty self-explanatory, right?

### Is near 
Alright. Look. You can figure this one out yourself.

### Rotate around
Rotate a point around an origin point by a given angle.

### Are collinear
Are three points collinear (on the same line)?

### Zero if null
If the provided point is null, return a point with X/Y/Z values of 0.
If the point isn't null, return that point.