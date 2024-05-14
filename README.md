**SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS**

**AIM:**

 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Vivado 2023.3.

**APPARATUS REQUIRED:**

Vivado 2023.3
  
**PROCEDURE:**

STEP:1 Start the Vivado, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.



**SR FLIPFLOP:**

**LOGIC DIAGRAM:**


![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

**VERILOG CODE:**


```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```

**OUTPUT:**


![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/1ddf9fde-7e6a-4fa9-a862-a0903d8731e5)


**JK FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

**VERILOG CODE:**

```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/96460c18-ceea-4489-abe1-14a667e0ba1c)


**T FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

**VERILOG CODE:**

```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/f9875498-e47a-405c-8e56-d09763dea255)


**D FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

**VERILOG CODE:**

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/e6d0ddc3-6bd0-45d1-890d-58bbef6fddc2)

**COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

**UPDOWN COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/316655aa-1f4e-4956-a5d2-f985952dabc3)


**VERILOG CODE:**

```
module udc(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/50804c8c-87a4-4b98-b405-ab13ac0d6a0b)

**MOD-10 COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/2364bc0f-bb79-4c46-a7a9-7f1c76c97884)


**VERILOG CODE:**

```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/7a2d63af-48c2-42d6-a6fe-810526798f44)

**RIPPLE CARRY COUNTER:**

**LOGIC DIAGRAM:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/29b024b6-5526-4d9e-9c78-5285a7b92a8e)


![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/efc3d8a0-8e0c-4501-ae4c-6a87cbc5bb8c)



**VERILOG CODE:**

```
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule

module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-4/assets/160568690/05ac7475-7dd9-4a9b-9e0c-332e90fc3017)


**RESULT:**

 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Vivado 2023.2


