---
layout: post
title: "Human-intention-driven robot control in collaborative tasks"
categories: robotics
author:
- Luis Contreras
meta: "Robotics"
---

The application of robots in many fields has been extended rapidly in recent years; from industrial robots to space explorers, now we can find them performing home services.  A service robot is a robot that can assist humans to perform common daily tasks in shared environments, such as houses, offices or hospitals. To achieve this, a service robot must be capable of understanding spoken and visual commands in a natural way from humans, navigate in known and unknown environments while avoiding static and dynamic obstacles, recognize and manipulate objects, detect and identify people, among several other tasks that a person might request. 

However, many of the tasks a robot has to perform have been focused on individual operations, limiting the human-robot interaction to command understanding (by voice or gestures) or dynamic scene understanding (to avoid humans while navigating, for example). Nevertheless, given that robots are reaching stunning performances on human-like tasks, human-robot collaboration results inevitable; to do so, human intention inference becomes useful in many situations where the robot and human configuration spaces do not intersect or, in big task spaces, human and robot plans may differ to solve the same problem.

In our work "Multimodal human intention-driven robot motion control in collaborative tasks" we aim at developing a human-intention driven robot motion control in collaborative tasks. Specifically, a human and a robot have to move a table from position A to position B inside a room. To infer the human intention, we detect the force applied to the hand by a series of 6 axes force sensor mounted on the wrist and the human's motion direction and velocity using 2D laser readings; then, we average the weighted human's and robot's paths to generate a resulting collaborative motion.

We use the HSR, a standard service robot platform able to perform domestic tasks in indoors environments. In our setup, both a human and a robot hold a rigid object from opposite sides. The input to the control model is a force located in the center of the robot wrist; the force sensed at the wrist's center is the effect of a force applied by the human at the other end of the object. We consider three cases depending on the maximum resulting force:

* When the maximum force is over the X axis, a forwards/backwards linear movement 
* When the maximum force is over the Y axis, a rotational angular movement
* When the maximum force is over the Z axis, a vertical torso movement

Finally, the projected forces are normalized and then, they are scaled by a constant  that represents the maximum velocity that a joint can reach.

To estimate the human motion-direction we take a time window with consecutive position readings and apply a linear regression to fit a line on those points; we consider this line as the direction of the unit vector representing the human motion.

In our approach, human intention corresponds to a number of states mutually exclusive -- with Boolean state vector I and the states stop, motion_x, rotation_y, and motion_z -- where only one state is considered at a time. The resulting force that translates to a motion intention depends on the input force direction and the time that the force has being applied. To avoid intermittent state-transitions, we apply a low pass filter to each state where the probability of transition is directly proportional to a charge and discharge time model.

Given a target goal, robot dynamics is based on a standard path planning, the Robot_plan. Human-based robot dynamics is a result of the input force corresponding to a sequence of mutually exclusive states – only one state is active at a time: front, back, rotate clockwise, rotate anti-clockwise, and stop – as well as the human motion dynamics (direction, velocity, and acceleration), the Human_plan. The collaborative function is defined as weighted sum, with a factor alpha, a cooperation weight, with alpha=1 following the robot plan only and alpha=0 following the human plan only.
