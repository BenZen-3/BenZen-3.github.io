---
layout: post
title:  "Humanoid Robotic Arm"
date:   2024-08-01 02:51:09 -0400
categories: project
icon: \assets\images\Humanoid_Arm_icon.png
summary: Ongoing project to build an anthropromorphic humanoid robotic arm. This arm has been designed for upcoming work on embodied machine learning and imitation learning. Design makes significant use of brushless motors with capstan drives to acheive a high torque density with good controlability and low cost.
---

<video autoplay muted loop width="1000" height="600">
  <source src="\assets\images\PewPewArm.MOV" type="video/mp4" >
  Your browser does not support the video tag.
</video>

"Armed and dangerous"

<h1> Overview </h1>

This project is still in progress, so I will update this as it progresses. It was started in June 2024 and the current progress is about 6 weeks of work which slowed down when the semester started and my availibility became more limited. The design takes inspiration from many places, but the design is completely my own.

The overarching goal for this arm is to create a humanoid arm for embodied machine learning and imitation learning. This yeields the mechanical goal to create an arm that mimics humanoid size and capabilities while maintaining controlability. These requirements are difficult to manage while maintaining low cost, so the design requires a lot careful attention Just to list a few requirements: anthropromorphic morphology, high speed, high torque, backdrivability/torque transparency, precise position and velocity control, and decent torque control.

The current design of the arm encompasses everything up to the wrist joint. Since a human arm is 7 DoF and the wrist is 2 DoF, this design is for 5 DoF. The wrist joints and hand will be completed later once this portion of the project is complete. The hand in the pictures is a model I found online as a placeholder. The arm that I have pictures of only implements 4 joints. The shoulder is 3 rotational joints, but only 2 are active because the one joint contained by the body is not currently needed.

<img src="\assets\images\Humanoid_Arm.jpg" style="width:500px;height:600px;">

<h1> Major features </h1>

The arm makes ample use of capstan drives. These joints are ideal for their high backdrivability and ease of use. Unlike strainwave gearing or cycloidals, they have excellent backdrivability and are very cheap and do not require machining or expensive components.

One of the goals was to keep all the wires inside the arm. This is possible because capstan actuators can be made as hollow shaft actuators. This is one of the few ways to do this cleanly (or at least without using expensive multi-channel slip rings). The elbow joint is a special type of joint that is more akin to a block and tackle joint. A very similar mechanism is found in the <a class="custom-link" href="https://www.youtube.com/watch?v=jM5Sy5Eu9pA">LIMS robot</a>. 

The joints make use of moteus r4.11 motor controllers for their excellent field orriented control characteristics. These give position, velocity, and torque control. Combined with the highly backdrivable capstan drives, this setup theoretically gives a great controlability while still remaining low cost. These joints use 8108 KV90 brushless motors for their good torque and performance. Few motors are readily availible in low KV ratings (gimble motors don't count). The torque can be approximated by 8.3*I_max/KV (<a class="custom-link" href="https://things-in-motion.blogspot.com/2018/12/how-to-estimate-torque-of-bldc-pmsm.html">source</a>). The controllers can output 11A without thermal management, and 22A with thermal management (<a class="custom-link" href="https://mjbots.com/products/moteus-r4-11">source</a>). This means that I can expect about .9Nm without thermals and 1.8Nm with thermals. I won't go into the details here because I will need to produce a full report on this later, but the best solution I came up with was to use thermal management to maximize torque and minimize my gear ratio. The small gear ratio allows everything to be more backdrivable, and permits the use of low ratio capstan drives.

For manufacturing, this design makes extensive use of 3D printing. Although I know I could have milled some of these parts, many of these would be practically impossible to machine (the design for manufacturing assumed 3D printing). Eventually, I plan to switch from PLA to CF-nylon to increase rigidity and toughness. For the curious, I use a different PLA color every week so that I know which week the prints are from. When I just use black, its difficult to tell if a particular print is the newest one. This leads to a rainbow effect as I switch colors throughout the design.

<div class="image-container">
    <img src="\assets\images\DoubleShoulderActuator.png" style="width:600px;height:600px;">
    <img src="\assets\images\Humanoid_Arm_Half.png" style="width:720px;height:600px;">
</div>



<h1> Results to Date </h1>

<video autoplay muted loop width="1000" height="600">
  <source src="\assets\images\Anthro_Arm_Move.MOV" type="video/mp4" >
  Your browser does not support the video tag.
</video>
The arm is absolutely ready to throw hands. This is approximately 17% of maximum speed. Although to be fair I believe that max speed would break the PLA parts until I can upgrade them to CF-nylon.


The arm so far has proven to be extremely backdrivable and controllable. 

This arm is a combination of lessons from the past large projects that I have undertaken. It takes a lot of the electrical knowledge about motor control that I picked up while developing the robotic quad actuators and merges it with the lessons I got from the rover arm. The final element that I'm actively working on right now is the integration of machine learning. I am hoping to integrate a vision language model with this arm so that I can request it to grab specific objects. This project is in-progress and this will be updated occassionally as progess is made.


10/10 would build again, or I guess keep building.