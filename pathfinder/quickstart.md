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

##### TABLE OF CONTENTS
1. 
{:toc}

## Getting familiar with Pathfinder
Pathfinder is an odometry-enabled library that uses input from different configurations of odometry
tracking systems to determine the position of a robot and thus enable the robot to go to certain positions.

### Pathfinder, at its core
Pathfinder implements the ThetaStar pathfinding algorithm, which is a variation of the A* pathfinding algorithm.
Originally intended for usage in video games - think the controlling of bots (as a classical example, just take
a look at a Zombie from the popular game, Minecraft) - the A* algorithm is useful in a situation such as this to
enable a robot to find a path to a target on a two-dimensional playing field.

### Field-mapping
In addition to a ThetaStar algorithm, Pathfinder has its very own two-dimensional field-mapping system. Mapping a
playing field is done pretty simply - cartesian coordinates are used to represent various different shapes - most
notably, rectangles and circles. Obviously, there's no point in having a Pathfinding algorithm if there are no
points to find. If there aren't any zones to avoid, what's the point in using a pathfinder?

## Writing some code
If you're using Pathfinder for an FTC competition, do yourself a huge favor and use the Pathfinder-ftc library.
I promise you - it's so much easier to use for finding paths in an FTC scenario. As usual, I'll give you the
courtesy of linking it [here](with_ftc.md).

### Implementing Pathfinder.java
Pathfinder's main class is as follows:
`me.wobblyyyy.pathfinder.Pathfinder`
You should ABSOLUTELY go look at the JavaDocs for that file. You might be very (very) confused if you don't.