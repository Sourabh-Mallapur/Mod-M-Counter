# Mod-m-Counter
This Repo contains the design flow for MOD-13, synchronous, binary ‘up’ counter (using TannerEDA software for simulation purposes).
Design and Simulation done using S-Edit - An analog mixed-signal design flow providing design capture, simulation set-up, launch and results analysis verification.

For this Project we will design Mod-13 Up Counter

## Introduction
Typical Full-Custom IC Design Flow

![Dessignflow drawio](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/bc219e81-795f-4c3e-9019-e30362fbe898)

S-Edit Allows us to do Ciruit Design and Simulation

## Gate Level Circuit Design
MOD counters are defined based on the number of states that the counter will sequence through before returning back to its original value. In the case of mod-13 ‘up’ counter, the counter shall advance by one state, from 0 to 12 (12 states), before returning to its first state 0. The state changes are done in binary form, where each flip-flop stores 1-bit of the binary form. 

### Master-Slave D-Flip Flop
A master-slave flip-flop comprises two latches – a master latch, and a slave latch. This configuration eliminates any transparency in the flip-flop: a change occurring in primary inputs is never reflected directly to the outputs, since opposite phase clocks are used to activate the M and S latches.

![Picture2](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/2f0bdb46-62f5-4207-a4c8-b30de36e8d23)

In our project, we shall consider a MOD-13, synchronous ‘up’ counter using master slave D-Flip Flop.The computation of number of flip-flops, given by the relation 2^N ≥M, for a mod-M counter, has resulted in requirement of 4 ‘D master-slave’ flip-flops.

Example of 4-bit Counter

![Picture](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/67415f42-adee-4fb1-a8e7-37eed46d5b60)

### Design of a MOD-13 counter

#### The truth table is shown below:
![Untitled](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/cb6e7269-e04b-4b6b-9ab7-a2b5415ad2ac)

#### Karnaugh-maps for output expressions
The flip-flop output expressions can be obtained using Karnaugh-maps, as following:

1.Expression for D0 input of first flip-flop

![Capture1](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/be9ab599-1910-45cc-8d25-20405c462ef2)

2.	Expression for D1 input of second flip-flop

![Capture2](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/4da0c3fb-b423-41fb-81c1-84c0d51b9a6a)

3.	Expression for D2 of 3rd flip-flop

![Capture3](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/5259f71b-ab3d-4284-82a7-d6f5ba0fce4b)

4.	Expression for D3 of 4th flip-flop

![Capture4](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/46a3a53b-e9bc-481c-9c22-769a0bdab1d5)

### Simplified Gate level design

![g452](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/58fc6b0f-bcc8-4c9f-8a99-fc4f38a148da)

## Implementation in S-EDIT

Using 250nm technology transistors provided by S-EDIT standard library

### COMBINATIONAL LOGIC

CMOS INVERTER

![1](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/3d1db1fd-47a7-4f24-ae6e-978e117f7116)

2-INPUT AND GATE

![2](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/860f9768-4544-4231-b1e5-8df87ad871f1)

3-INPUT AND GATE

![3](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/1d74856b-338f-47c6-894d-4d661e4cd7c4)

2-INPUT OR

![4](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/06fbf7d5-875b-4e0e-be5c-754f4ff996a1)

3-INPUT OR GATE

![5](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/3f74b8ea-51d8-4b85-a5cd-1fd93221ec58)

2-INPUT XOR GATE

![6](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/942c48b6-85bf-41c6-b5b0-0c4ba282a095)

TRANSMISSION GATE 

![7](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/a2074559-5362-414b-8695-5462368b8d5c)

### SEQUENTIAL LOGIC

CMOS S-R LATCH

![8](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/7e9e8406-fc2b-4865-9a3a-118e00f35e80)

D – FLIP FLOP UTILISING MASTER-SLAVE FLIP FLOP LOGIC

![9](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/02a619e1-0063-4844-9132-a0d86e0c158c)

### Counter Inputs


D0

![11](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/9786bf80-29fb-4331-8693-45f4467b9274)

D1

![12](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/aadfc58f-9585-4625-b1e2-98d9d2a5065e)

D2

![13](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/7599e544-08e6-41ae-91fa-be53bd346470)

D3

![14](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/85c4764f-5c85-4685-9bcb-4b456b82aa99)

### Final Counter Schematic

![15](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/2917bd09-4d8b-4d97-a252-129424d03dfd)

## Simulation Results

![1](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/52835755-52c1-4f8d-94e0-34739debf28c)
