---
title: "Catalytic Converter : My Final Semester Project"
subtitle: "Multi-Physics Modeling with COMSOL in My Final Semester Project"
date: "2021-08-19"
---

## Final semster

Hey everyone! As I approach the end of final semester of my college journey, I wanted to take a moment to reflect on my experiences and share with you the exciting project that I've been working on.

College has been a transformative journey for me. From the first day I stepped onto campus, I was filled with a mix of excitement and nervousness. Over the years, I've had the opportunity to meet amazing people, learn from inspiring professors, and explore subjects that have expanded my horizons.

## Major Project

**In simpler terms, this thesis is all about creating a very detailed computer model to understand how a car's catalytic converter does its job. It's a bit like solving a complex puzzle, where we need to figure out how different pieces (like energy, movement, and substances) fit together.**


- We also need to understand how quickly a specific chemical change happens on the surface of the converter and how gases move through it, like water soaking into a sponge. This research can help us make catalytic converters work even better to reduce pollution from cars.

- Moving on to the specifics of my project, we have chosen to work with **COMSOL** Multiphysics 5.5, a versatile software package. This software allows us to conduct finite element analysis, solve partial differential equations, and perform multiphysics simulations. What's great about COMSOL is that it provides a unified workflow for a wide range of applications, including electrical, mechanical, fluid dynamics, acoustics, and chemical processes. Moreover, we can further analyze simulation results using MATLAB for more advanced post-processing.

This is the original thesis written by my group <a href="https://drive.google.com/file/d/14W1EIHBAkqYEOC81sF4yKQi6lG4B9AMw/view?usp=drive_link" target="_blank">[Major project]</a>

**In the end, we hope our research can help make cars pollute less and run better.**

## Project Summary

Now, let's get into the heart of our project, which revolves around something called "monolithic reactors." These things are pretty fascinating. Imagine a block of material with a bunch of tiny channels running through it, like a maze. These channels can be all sorts of shapes – circles, squares, triangles, you name it. What's really cool is that we're focusing on how these monolithic reactors can clean up car exhaust. They have a big advantage over the old-school catalyst beds because they don't slow down the flow of exhaust gases as much.

- The 3D Geometry used is taken from COMSOL Application Gallery. The monolithic
reactor has modular structure made up of reactive channel blocks and supporting walls.
The length of the reactor is 700mm and has a radius of 100mm.
![monolith](/images/monolith.png)

- In our research, we've been reading up on what others have discovered about **monolithic structures**. It turns out they have a bunch of benefits over the old-style catalyst pellets or powders. They're really good at moving stuff around (mass transfer), they don't cause too much of a traffic jam for the exhaust gases (low pressure drop), they can handle high temperatures, and they're pretty tough cookies when it comes to handling mechanical stress.

- We've also learned that the math behind how these reactions happen in monoliths can be a bit tricky. It's not a one-size-fits-all deal. The way stuff reacts depends on things like what kind of catalyst we're using, how thick the special coating inside the channels is, and even the shape of the channels themselves. We found a particular equation that helps us understand how carbon monoxide turns into carbon dioxide when it flows through those 1 mm square channels.

- Oh, and speaking of the reactions, we found out that **temperature plays a big role**. When it's chilly, the reactions are sluggish, but as things heat up, they really get cooking (literally). The hotter it gets, the faster those reactions happen. It's like how water boils faster on a hot stove.

- Now, what we're really aiming to do with our project is to **simulate how this conversion of carbon monoxide to carbon dioxide happens in those monolith catalysts**. We're looking specifically at square and triangular channels. And we want to see how things change when we tweak a couple of things – like the temperature of the gases going in and how fast they're flowing. It's like running experiments without actually getting our hands dirty.

- We hope our work can make the world a better place to live in the future.







