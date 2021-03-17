---
layout: default
title: Tuning
parent: Pathfinder
nav_order: 5
---

# Tuning your Robot
Pathfinder itself is simply a library for manipulating input and output information
to get the robot to perform a specified goal. Such, Pathfinder doesn't care about
what units are what units or which direction the robot needs to move to do whatever.
As a result of this abstraction, it's often neccesary to tune your robot.

##### TABLE OF CONTENTS
1. 
{:toc}

## Drivetrain Tuning
Tuning the drivetrain is a must. Here's some guidelines on how you can tune your
drivetrain's configuration like the professional you are.

### Tuning a Meccanum or Tank Drive
Meccanum and tank drives are both very easy to tune. The core concept here that you
need to recognize is that tuning is designed to make sure that each motor spins in
the correction direction when given a certain power value. The kinematics provided
in Pathfinder doesn't account for the possibility that a motor might be inverted.
If you tell a robot to move forwards using Pathfinder, Pathfinder will say that every
drive wheel should get 1.0 power - max speed forwards, that is. However, if your
robot hasn't been tuned whatsoever, your robot won't turn forwards - rather, it'll
do donuts until you turn it off. This is because (on most robots, at least) the left
(or right, it depends) half of your drivetrain spins in the opposite direction as
the other side. Thankfully, there's a pretty easy fix to this problem.
- Flip the robot on its side (or upside-down, just be careful not to break it!)
- Create a basic program that sets the power of each motor to 0.3.
- Every motor should be spinning forwards now. If they're not, you need to invert it.
- Write down each motor and the direction it was spinning.
- In your code, make sure that the motors that should be inverted have the power
  values they recieve multiplied by negative 1 before setting power to the motor.
- Run the four-wheel-forwards test again. Each wheel should spin in the same
  direction now.