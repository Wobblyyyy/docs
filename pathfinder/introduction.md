---
layout: default
title: Video Guides
parent: Pathfinder
nav_order: 4
---

# Introduction
This page serves as an introduction to the core concepts behind Pathfinder. It's
suggested you read this page so you become familiar with the ideas driving the
operation of Pathfinder in a production environment. Although not required to create
a robot that utilizes Pathfinder's motion toolkit, these concepts will help to
accelerate development and make your codebase more accessible. 

##### TABLE OF CONTENTS
1. 
{:toc}

## Major Ideas
Pathfinder is largely composed of two components:
- Odometry (where is the robot)
- Drivetrain (how to move the robot)
Each of these components will be discussed in more detail in a moment.

### How These Ideas Connect
For the purpose of illustrating the concept behind Pathfinder's motion toolkit,
imagine odometry as an input of information on the robot's position and imagine
the drivetrain as an output of information on the robot's position. Assuming
odometry is always 100% accurate, and assuming a robot is capable of moving in
any direction, (holonomic) your robot is able to navigate to any position by
comparing the robot's current position and the robot's target position and calculating
the neccesary output to produce the desired motion. 

Pathfinder extends upon this simple concept by providing a vast array of
features you can use to fully customize your robot's motion. 

### Odometry
Odometry reports where the robot is. Odometry implementations are left up to
the end user, but several are provided within Pathfinder itself. 

### Drivetrain 
Drivetrain objects are responsible for providing an interface for moving the
robot. Several are bundled with Pathfinder.