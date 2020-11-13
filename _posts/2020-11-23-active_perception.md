---
layout: post
title: "Towards active perception in service robots"
categories: robotics
author:
- Luis Contreras
meta: "Robotics"
---

The application of robots in many fields has been extended rapidly in recent years; from industrial robots to space explorers, now we can find them performing home services.  A service robot is a robot that can assist humans to perform common daily tasks in shared environments, such as houses, offices or hospitals. To achieve this, a service robot must be capable of understanding spoken and visual commands in a natural way from humans, navigate in known and unknown environments while avoiding static and dynamic obstacles, recognize and manipulate objects, detect and identify people, among several other tasks that a person might request.

In one of our lines of investigation, we have shown how active perception in low-level behaviours (such as "move the robot to a target pose relative to the edge of the table" or "position the gripper at a given distance to the target object") helps to solve the task without changing the plan by actively updating the state of the robot and the environment when executing a sub-task and or reacting when an unexpected situation arises [1].

In addition, we have proposed robot competitions as a benchmark to objectively evaluate service robots' performance in a well defined setup. Through the Tidy-Up task, we have presented our results in the object manipulation problem where error-detection and fast error-recovery as well as continuous environment update result a fundamental feature to complete a task with the best performance.

In the object manipulation problem, after the object detection and recognition steps, the robot has to plan the grasping trajectory such as it avoids collisions, and therefore the robot pose is limited by the arm's configuration space (i.e. all the possible poses the arm may take at a given robot pose, considering the obstacles in the range). Localisation systems are able to update their map dynamically when changes are detected and accurately pose the robot in a safe position to grasp an object. However, when changes are small or they happen after the robot reached the destination, an active perception system is desirable to update its knowledge and perform the requested action successfully.

In our previous work we have proposed an active object manipulation systems using a 5-DOF RGBD camera (XYZ position, and pan and tilt orientation) on top of a service robot and a 6-axis force sensor in the hand. Through these sensors, the robot is able to detect the obstacle's position and orientation in robot coordinates while the different states of the manipulation process take place [2][3]. We have also presented and evaluated a series of object recognition strategies for service robots in indoors environments. More specifically, we propose three robot-object observation strategies: random-distance, close-distance, and hand-distance. Results shown an increase in performance when a constant observation strategy (hand-distance) is used [4].

We aimed to introduce two key concepts to continue the discussion in the Manipulation Intelligence problem. First, we favour active perception in behaviour-based systems over action-specific systems, that can be seen as black-box solutions where, for a slightly different new task or conditions, our current understanding doesn't allow us to adjust the given solution by only modifying a parameter or a set of parameters and instead we need to fine-tune or re-train such black-box solution. Second, although the skills required to solve a given problem are reaching amazing performances individually, we propose the evaluation of such individual solution in fully integrated robot systems tested in scenarios like those proposed in international robotic competitions.

We assume that CNN is the state of the art for task-specific object recognition problems and therefore we work towards improving their performance when using service robots by adding active reasoning before recognition; this includes testing several points of view, by moving the robot's base and or head and by first grasping the object and then observe it at a fixed distance in the robot's hand. The reason for that is that lately, it seems that robots are being seen as external agents that move around an environment and not as intelligent agents that can actually interact in it and even alter it to it's best convenience (sometimes in a way a human can't do) when performing (and if allowed by) a given task, and we intend to promote research towards it.

[1] A Motion-Planning System for a Domestic Service Robot (2018). SPIIRAS Proceedings 60, 5–38  
[2] Multimodal feedback for active robot-object interaction (2018). IEEE/RSJ IROS Workshops  
[3] Visual feedback for active robot-object interaction (2018). The 36th Annual Conference of the Robotics Society of Japan  
[4] Robot-object interaction strategies for object recognition (2019). The 37th Annual Conference of the Robotics Society of Japan  
