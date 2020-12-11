---
layout: default
title: Pathfinder Installation
parent: Pathfinder
nav_order: 1
---

# Installation
Installation hopefully isn't too difficult to complete - regardless, best of luck.

##### TABLE OF CONTENTS
1. 
{:toc}

Not much else. Everything else Pathfinder uses should be bundled inside of the JAR itself. Certain `_1125c` distributions 
may include releases of Pathfinder, but assuming you've downloaded the two separately, these should both be added as Gradle
dependencies. ftc2 isn't exactly required, hence it's marked optional, but it's hugely useful in doing a bunch of stuff and
makes development and getting started with the library a couple hundred times easier.

## Adding Pathfinder
Pathfinder comes bundled with most of the essential code that you'll need to get started. PathfindingCore, the very
core of the pathfinding system that's in use here, is included, as well as OdometryCore. Not much else is needed.
If you're working in an FTC context, you're probably going to want to use Pathfinder-ftc, a much more inclusive library
that'll give you a whole hell of a lot of an easier time getting started.

### Adding an artifact to a module
I don't feel like writing documentation here, so... sucks for you.

### build.gradle
As of now, the only way to add Pathfinder to your project is by downloading an artifact, placing it in a lib folder,
and adding that to a Gradle file.

The two lines of code you'll need (depending on the library you've chosen to use) should be inserted in the dependencies
block of the Gradle file you're using.

#### Adding Pathfinder without Pathfinder-ftc
> implementation ('libs/Pathfinder.jar')

#### Adding Pathfinder with Pathfinder-ftc
> implementation ('libs/Pathfinder-ftc.jar')