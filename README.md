# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
# AIM: 
 To simulate and synthesis multiplier using vivado.

# APPARATUS REQUIRED:
vivado 2023.1
  
# PROCEDURE:

STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# Logic Diagram:

# 2 bit Multiplier:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

# Verilog code:

module ha(a,b,s,c);

input a,b;

output s,c;

xor g1(s,a,b);

and g2(c,a,b);

endmodule

module bitmultiplier(a,b,c);

input [1:0]a,b;

output [3:0]c;

wire w1;

and g1(c[0],b[0],a[0]);

ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);

ha ha2(a[1]&b[1],w1,c[2],c[3]);

endmodule

# Output:

![2bit_multiplexer](https://github.com/Princyagnes/VLSI-LAB-EXP-3/assets/115100663/c91b5303-a8fe-4f14-ac71-641ea4e0caf9)


# 4 Bit Multiplier:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)


# Verilog code:

module ha(a,b,s,c);

input a,b;

output s,c;

xor (s,a,b);

and (c,a,b);

endmodule


module fa(a,b,c,sum,carry);

input a,b,c;

output sum,carry;

wire w1,w2,w3;

xor g1(w1,a,b);

xor g2(sum,w1,c);

and g3(w2,a,b);

and g4(w3,w1,c);

or g5(carry,w3,w2);

endmodule

module mul(x,y,z);

input [3:0]x,y;

output [7:0]z;

wire [17:1]w;

and (z[0],x[0],y[0]);

ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);

fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);

fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);

ha ha2(x[3]&y[1],w[3],w[7],w[4]);

ha ha3(w[5],x[0]&y[2],z[2],w[8]);

fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);

fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);

fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);

ha ha4(w[12],x[0]&y[3],z[3],w[15]);

fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);

fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);

fa fa8(w[4],x[3]&y[3],w[17],z[6],z[7]);

endmodule


# Output:

![four multiplier](https://github.com/Princyagnes/VLSI-LAB-EXP-3/assets/115100663/4ea34a36-29fb-4539-9a44-7b34b9b0e73e)


# Result:

Thus,the simulation and synthesis of multipliers by using vivado has been successfully excecuted and verified.


