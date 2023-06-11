# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
1.Create a new project in QuartusII software.

2.Name the project as uc for upcounter and dc for down counter.

3.Create a new verilog hdl file in the project file.

4.Name the module as dc and uc for down counter and up counter.

5.Within the module declare input and output variables.

6.Create a loop using if-else with condition parameter as reset value.

7.End the loop.

8.End the module.

### PROGRAM 
```
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: SIVABALAN S
RegisterNumber:  212222240100
*/
UPCOUNTER:
module upc(clk,A);
input clk;
output reg[0:3]A;
always@(posedge clk)
begin
		A[0]=((((A[1])&(A[2]))&A[3])^A[0]);
		A[1]=(((A[2])&(A[3]))^A[1]);
		A[2]=((A[3])^A[2]);
		A[3]=1^A[3];
end
endmodule

DOWNCOUNTER:
module downc(clk,A);
input clk;
output reg[0:3]A;
always@(posedge clk)
begin
	A[0]=((((~A[1])&(~A[2]))&A[3])^A[0]);
	A[1]=(((~A[2])&(~A[3]))^A[1]);
	A[2]=((~A[3])^A[2]);
	A[3]=1^A[3];
end
endmodule
```

### RTL LOGIC UP COUNTER AND DOWN COUNTER  

![243101427-16273893-4ae3-4d91-96c2-8d0907f287cb](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/3bfc77e5-3e6a-445a-8fe1-473b1d25331e)
![243101425-8e514bc5-6212-49e5-91bc-318ee8a6363d](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/155f39dc-acec-4ff3-aed6-c1be8cd13912)

### TIMING DIGRAMS FOR COUNTER  

![243101421-cb26f8da-2aa1-4dfb-a549-ce1d392d8596](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/a80c4df6-7cc1-4a9e-869e-6ea728e42506)
![243101419-8ba6f646-9d15-4889-93e2-063f1c074364](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/3a71fa93-3f90-4c54-9c1b-57147a79c726)

### TRUTH TABLE 

![243101418-35121f9e-b814-42d3-94d3-0a5229be708f](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/6080f414-3aff-4bd7-8971-cbc4c17a11a6)
![243101413-ec48d8d3-01ea-4741-94bc-e4d72a346754](https://github.com/sivabalan28/Exp-7-Synchornous-counters-/assets/113497347/8af31ecb-55ba-4e46-9a84-ff3dd3e93e28)

### RESULTS 
Thus, 4 bit up and down counters are implemented and its functionality is validated successfully.

