Pedestrian Crossing Traffic Light Controller

Overview

This project implements a pedestrian crossing traffic light controller using Verilog. The design incorporates a hierarchical structure with three different modulo counters and a finite state machine (FSM) to manage traffic light states. The controller handles traffic lights for both pedestrians and vehicles, ensuring safety and efficient traffic management.

Project Structure

• Counters:
	• mod13counter: A modulo-13 counter that counts from 0 to 12. It resets when reaching 12 or when a reset signal is asserted.
	• mod8counter: A modulo-8 counter that counts from 0 to 7. It is configured to count till 6 for the specific use case.
	• mod2counter: A modulo-2 counter that toggles between 0 and 1. It resets when reaching 1 or when a reset signal is asserted.
• FSM:
	• The FSM module controls the behavior of the traffic lights based on states and transitions defined by the current state and the inputs from the counters.
	• It uses a Moore state machine approach, with 11 states encoded using one-hot encoding for simplified circuit implementation.
	• The FSM governs the transitions of the traffic lights, ensuring the correct operation in response to pedestrian and vehicle demands.
• Controller:
	• The controller module acts as the highest level of hierarchy, connecting the FSM to the inputs (such as clock, reset, and pedestrian request signals) and managing the outputs to control the traffic lights.

Modules Description

1. mod13counter:
	• Counts from 0 to 12 and resets afterward.
	• Inputs: clk, reset
	• Outputs: Q[3:0]
2. mod8counter:
	• Counts from 0 to 7, configured to reset after counting to 6.
	• Inputs: clk, reset
	• Outputs: Q[2:0]
3. mod2counter:
	• Toggles between 0 and 1 and resets afterward.
	• Inputs: clk, reset
	• Outputs: Q
4. FSM:
	• Manages the states and controls the traffic light outputs based on the state machine logic.
	• Inputs: clk, reset, SB
	• Outputs: TR, TY, TG, PR, PG
5. Controller:
	• The top-level module that integrates all components and controls the overall operation.
	• Inputs: clk, reset, NB, SB
	• Outputs: TR, TY, TG, PR, PG

Testbench

The testbench for this project simulates the operation of the controller under various conditions. It initializes the inputs, runs the simulation for 75 clock cycles, and monitors the outputs to ensure correct functionality.

How to Run

1. Simulation:
	• Use a Verilog simulation environment such as ModelSim or the provided link to EDAPLAYGROUND.
	• Run the testbench to verify the functionality of the traffic light controller.
2. Synthesis:
	• The Verilog code can be synthesized and implemented on FPGA boards or similar hardware platforms for real-world testing.