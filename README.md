# Digital_Clock
This digital clock is designed using Logisim.

## 1. Circuits I used

I used several circuits which I made them into integrated circuits :

* 7 segments 1 digit
* Synchronous counter divide by 10
* Synchronous counter divide by 6
* synchronous counter divide by 2
* Synchronous counter divide input
* Clock chip
* Main

I will discuss in the following section what are these IC and explain why
I built them.

## 2. Circuits

* 7 segments 1 digit :This is a simple 7 segments 1 digit circuit (0 to 9), built using the build circuit tool
in Logisim where I only entered the input table (0 to 9 in binary) and the
output are 7 segments (a to g).

* Synchronous counter divide by 10 : Also called in my simulation file ”counter div 10”, this is a normal synchronous
4 bits counter using 4 JK flip flops, usually this counter stops at
the number 15 (1111 in binary) and starts again from 0 (0000 in binary),
but using the clear method ,we take the bits that will be 1 when the output
of the counter is 10 (1010 in binary) which are Q1 and Q3, put them through
an AND gate and all the way to the clear inputs of all the JK flip flops so we
get a divider by 10 that counts from 0 to 9.

* Synchronous counter divide by 6 : Also called in our simulation file ”counter div 6”, same explanation as the
counter div 10, but we stop when the output of the counter is 6 (0110) so we
take to the AND gate Q2 and Q3.

* Synchronous counter divide by 2 : Also called in our simulation file ”counter div 2”, simple synchronous 2 bits
counter using JK flip flops and we want the counter to count only from 0 to
2 so we take into the input of the AND gate the bits that will be 1 when the
output of the counter is 3 (11) so Q1 and Q2, all the way to the clear inputs
of all the JK flip flops.

* Synchronous counter divide input : Also called in our simulation file ”counter div input”, this is basically same
as explained in section 2.2, it is a synchronous counter div 10, but also it
can be a divider for another number which is when the clock’ hours become
more then 20 hours, we have to rest the clock at 23 hours 59 minutes and 59
seconds to 0 hours 0 minutes and 0 seconds. So this IC takes an input which
will be HIGH when the hour’s first digit is 2 and the second one becomes
4, both the AND gate for the divide by 10 and this new input divider go
through an OR gate and all through the clear inputs of all the JK flip flops.

* Clock Chip : In this circuit we are going to use 6 7 segments 1 digit circuits, 2 counters
div 10, 2 counters div 6, 1 counter div input and 1 counter div 2. Note
that every counter has an input called ”pause”, which pauses the counter
while its a LOW input. first we start by a counter div 10 for the seconds
(the pause will be always HIGH), we take from the output of the counter
the 2 bits which represents the 1’s in 10 (1010) through an AND gate so it
enters the pause input into a counter div 6 next to it (the other digit of the
seconds).Same applied for the counter div 6 , we take the output of counter
which represents the 1’s in 6 (0110) through an AND gate to be the pause
for a counter div 10 (first digit of the minutes), then again same we use a
counter div 6 (for the other digit of the minutes) and the pause application
is the same as before we take the bits (1’s) of 6 (0110) through an AND gate
all through the pause input of a counter div input for the first digit of the
hours, for the divide input of this counter we take an AND gate that takes
the 1’s of this counter when the output is 4 (0100) and the 1’s of the other
hour’s digit when the output is 2 (0010). For the last counter of the other
hour’s digit we use a counter div 2 we take the pause as the output of an OR
gate that takes 2 inputs, the previous AND gate and an AND gate taking
the 1’s of the previous counter when the output is 10 (1010).

###### PS: all the counters takes as input the same clock at 1Hz frequency.

* Main : For  this  final  circuit  we  take  the  clock  chip  which  outputs  6  7  segments  1digit  circuits  ( a_i , b_i , c_i , d_i , e_i , f_i , g_i )
i  going  from  1  to  6.
All  theseoutputs go through 6 7-segments display and of course we give the clock chipa clock input
