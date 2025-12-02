---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

My FPGA VGA Driver project was developed on the Basys3 Board which is a FPGA, configured using Verilog and Vivado 2025.1. The project was to attempt to implement a VGA driver to display graphics on a monitor. 

## **Template VGA Design**
### **Project Set-Up**
My project adapted on the given code to generate three moving stripes that cycle through 3 states by a state machine: RED, GREEN and BLUE (RGB). This was done using HSYNC, VSYNC for timing and directly controlled pixel positions using a counter variable. 

<img src="https://raw.githubusercontent.com/dohertyjr0/fpga-vga-verilog/main/Project_Summary_SS.png">

### **Template Code**
In the Verilog project, I have files labelled VGATop, VGASync and VGAColourStripes. Within the VGASync file this was a preloaded file given to us by our lecturer Michelle. This file is used to initialise HSYNC and VSYNC signals and allows me to track the current pixel position and overall control what is displayed on the monitor. 

The VGAColourStripes.v file is where I wrote code to interface with the monitor in the lab. I implemented my own state machine that can switch between the colours red, green and blue, where cycling speed is managed by the counter variable. A 21 bit counter variable is used to control movement speed and cycling of states, I set my counter to 2^21 cycles or counter[20:0] in order to significantly reduce cycling speed for demonstarting purposes. This makes the counter reduce state at about 0.08 seconds at 25MHz clock. *The code is seen below:*
<img src="https://raw.githubusercontent.com/dohertyjr0/fpga-vga-verilog/main/docs/assets/images/counter_code.png">
My VGAColourStripes file mainly consists of if and else if statements in order to set the logic to dictate the 3 stripes visually moving in a loop. I initialised 3 positions labelled under 'drop?_pos' at positions '11'd?', with the positions being 11 bit wide and using 'd' for decimal I can pick how far apart I would like the stripes to be. Now the main part of my logic is using nested if statements so that when a col is greater than position 11'd? and less than another position AND if the row is at a greater position than previously initialised position 'drop?_pos' then move position and change state. *As seen below:*
<img src="https://raw.githubusercontent.com/dohertyjr0/fpga-vga-verilog/main/docs/assets/images/stripe_position_code.png">
### **Simulation**
Cannot run simulation, causing Vivado to crash
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
<img src="https://raw.githubusercontent.com/dohertyjr0/fpga-vga-verilog/main/docs/assets/images/Simulation_Schematic.png">
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">