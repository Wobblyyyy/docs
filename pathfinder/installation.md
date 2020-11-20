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

Not much else. Everything else that Pathfinder uses should be bundled inside of the JAR itself. Certain `ftc2` distrubtions 
may include releases of Pathfinder, but assuming you've downloaded the two separately, these should both be added as Gradle
dependencies. ftc2 isn't exactly required, hence it's marked optional, but it's hugely useful in doing a bunch of stuff and
makes development and getting started with the library a couple hundred times easier.

## Installation
Installation is as much a breeze as any other Gradle library. A quick list of steps, for those unfamilar with using Gradle,
is below. Enjoy! As I'm sure you will. :)

### Getting started
> Open your working project using [IntelliJ IDEA](https://www.jetbrains.com/idea/) or [Android Studio](https://developer.android.com/studio).
> If you're not using IDEA already and are still sticking to Android Studio (gross), you should definitely check out IDEA.

### Finding the Gradle file
> Open the file `TeamCode/build.release.gradle`, navigate to the `dependencies` section, and add the following.

### Adding implementations 
> - If you don't already have OdometryCore, you need to add...
>   - `implementation com.tejasmehta.OdometryCore:core:0.0.1`
> - If you don't already have ftc2, you (should) add...
>   - `implementation me.wobblyyyy.ftc2:core:0.1.0`