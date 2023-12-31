# Mod-m-Counter
This Repo contains the design flow for MOD-13, synchronous, binary ‘up’ counter (using TannerEDA software for simulation purposes).
Design and Simulation done using S-Edit - An analog mixed-signal design flow providing design capture, simulation set-up, launch and results analysis verification.

For this Project we will design Mod-13 Up Counter

## Introduction
Typical Full-Custom IC Design Flow

![Dessignflow drawio](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/bc219e81-795f-4c3e-9019-e30362fbe898)

S-Edit Allows us to do Ciruit Design and Simulation

## MOD-m counter
MOD counters are defined based on the number of states that the counter will sequence through before returning back to its original value. In the case of mod-13 ‘up’ counter, the counter shall advance by one state, from 0 to 12 (12 states), before returning to its first state 0. The state changes are done in binary form, where each flip-flop stores 1-bit of the binary form. 

### Master-Slave D-Flip Flop
A master-slave flip-flop comprises two latches – a master latch, and a slave latch. This configuration eliminates any transparency in the flip-flop: a change occurring in primary inputs is never reflected directly to the outputs, since opposite phase clocks are used to activate the M and S latches.

![Picture2](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/2f0bdb46-62f5-4207-a4c8-b30de36e8d23)

In our project, we shall consider a MOD-13, synchronous ‘up’ counter using master slave D-Flip Flop.The computation of number of flip-flops, given by the relation 2^N ≥M, for a mod-M counter, has resulted in requirement of 4 ‘D master-slave’ flip-flops.

Example of 4-bit Counter

![Picture](https://github.com/Sourabh-Mallapur/Mod-m-Counter/assets/106715050/67415f42-adee-4fb1-a8e7-37eed46d5b60)

### Design of a MOD-13 counter

The truth table is shown below:
	Present state	Next state
|No	|Q3	|Q2	|Q1	|Q0	|D3	|D2	|D1	|D0|
|0	|0	|0	|0	|0	|0	|0	|0	|1|
|1	|0	|0	|0	|1	|0	|0	|1	|0|
|2	|0	0	1	0	0	0	1	1
|3	|0	0	1	1	0 	1 	0 	0
|4	|0	1	0	0	0	1	0	1
|5	|0	1	0	1	0	1	1	0
|6	|0	1	1	0	0	1	1	1
|7	|0	1	1	1	1	0 	0	0
|8	|1	0	0	0	1	0	0	1
|9	|1	0	0	1	1	0 	1	0
|10	|1	0	1	0	1	0 	1	1
|11	|1	0	1	1	1	1	0	0
|12	|1	1	0	0	0	0	0	0
|13	|1	1	0	1	x	x	x	x
|14	|1	1	1	0	x	x	x	x
|15	|1	1	1	1	x	x	x	x

Karnaugh-maps for output expressions
The flip-flop output expressions can be obtained using Karnaugh-maps, as following:

1.	Expression for D0 input of first flip-flop

D0	Q1Q0
Q3Q2
		00	01	11	10
00	1	0	0	1
01	1	0	0	1
11	0	X	X	X
10	1	0	0	1

Simplifying the Boolean expression, we get:
D0= (Q0)̅((Q3)̅+ (Q2)̅)


2.	Expression for D1 input of second flip-flop

D1	Q1Q0
Q3Q2
		00	01	11	10
00	0	1	0	1
01	0	1	0	1
11	0	X	X	X
10	0	1	0	1

Simplifying the expression,
D1= (Q1)̅⊕(Q0)̅

3.	Expression for D2 of 3rd flip-flop
D2	Q1Q0
Q3Q2
		00	01	11	10
00	0	0	1	0
01	1	1	0	1
11	0	X	X	X
10	0	1	1	0


Simplifying the expression,
D2= (Q2)̅Q1Q0+ (Q3)̅Q2((Q1)̅ + (Q0)̅)

4.	Expression for D3 of 4th flip-flop

D3	Q1Q0
Q3Q2
		00	01	11	10
00	0	0	0	0
01	0	0	1	0
11	0	X	X	X
10	1	1	1	1

Simplifying the expression,
D3=Q3(Q2)̅+Q2Q1Q0
