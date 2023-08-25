# Synthosphere_design_hackathon
This documentation contains detailed explanation of design and synthesis of a digital delay timer used for generating programmable delay

# Note : Design file, testbench, post-synthesis design files, waveforms of pre-synthesis and post-synthesis and related files can be found in Design files folder.

Our goal is to perform pre-synthesis and post-sythesis on the design which in our case is a digital delay timer used for generating programmable delay. It consists of four operating modes : one-shot (OS), Delayed Operate (DO), Delayed Release(DR), Dual Delay (DD). Those four modes will be selected by inputs mode_a and mode_b.

The wb[7:0] are weighting bit inputs which are to program the delays according to given equations in the specification of the delay timer [This depends on the IC, the IC considered for this design is LS7212]. 

Depending upon the operating modes and tbe weighted bits the delay output will be prodouced which is being verified through the testbench. 

# Pre-synthesis

The tool used for execuitng the design file i.e .v file is iverilog and the waveforms can be seen on gtkwave platform.
Here is the command to generate a.out file and to see the output:
```
iverilog design_timer.v tb_desing_timer.v    // this will generate a.out file 
./a.out                                      // after executinon you will be able to see tb_delay_timer.vcd file
gtkwave tb_delay_timer.vcd                   // this command will open your waveform on gtkwave.
```
This step completes the pre-synthesis process.

Waveform of pre-synthesis:

![pic_1](https://github.com/rahulrathod10/Synthosphere_design_hackathon/assets/143223452/b4d13bab-62f2-42f2-be7e-950952c98b6d)





