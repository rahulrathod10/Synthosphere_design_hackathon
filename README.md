# Synthosphere_design_hackathon
This documentation contains detailed explanation of design and synthesis of a digital delay timer used for generating programmable delay

# Note : Design file, testbench, post-synthesis design files, waveforms of pre-synthesis and post-synthesis and related files can be found in Design files folder.

Our goal is to perform pre-synthesis and post-sythesis on the design which in our case is a digital delay timer used for generating programmable delay. It consists of four operating modes : one-shot (OS), Delayed Operate (DO), Delayed Release(DR), Dual Delay (DD). Those four modes will be selected by inputs mode_a and mode_b.

The wb[7:0] are weighting bit inputs which are to program the delays according to given equations in the specification of the delay timer [This depends on the IC, the IC considered for this design is LS7212]. 

Depending upon the operating modes and tbe weighted bits the delay output will be prodouced which is being verified through the testbench. 

# Pre-synthesis

The tool used for execuitng the design file i.e .v file is iverilog and the waveforms can be seen on gtkwave platform.
Execute the commads given line by line the terminal to generate the waveform :
```
iverilog design_timer.v tb_desing_timer.v    // this will generate a.out file 
./a.out                                      // after executinon you will be able to see tb_delay_timer.vcd file
gtkwave tb_delay_timer.vcd                   // this command will open your waveform on gtkwave.
```
This step completes the pre-synthesis process.

Waveform of pre-synthesis:

![pic_1](https://github.com/rahulrathod10/Synthosphere_design_hackathon/assets/143223452/b4d13bab-62f2-42f2-be7e-950952c98b6d)

#Post-synthesis 
We are using yosys an open-source tool to perform synthesis. Synthesis is a process to convert your design in the form of gates and flip-flops.

After performing synthesis, we generated "netlist_delay_timer1.v" file .

Here is the netlist and number of gates used to sythesize the design :

![top_pic](https://github.com/rahulrathod10/Synthosphere_design_hackathon/assets/143223452/fb081649-8c59-49ba-81c2-1da3e0e413d7)

Here is the output after mapping the design to all the flip-flops :

![abc_pic](https://github.com/rahulrathod10/Synthosphere_design_hackathon/assets/143223452/05763d90-5b97-4c79-820a-5eac85130690)

The post-synthesis process is carried out on the "netlist_delay_timer.v" file and waveforms of both pre-synthesis and post-synthesis is compared. If both the waeforms are same then synthesis is successful.

Repeat the same that we did for pre-synthesis, but this replace the file with "netlist_delay_timer1.v" and add the necessary files so that the tool knows from the design is derived. 

Execute the commands line by line to get the post-synthesis waveform :
```
iverilog netlist_design_delay_timer1.v ../verilog_model/primitives.v ../verilog_model/sky130_fd_sc_hd_edited.v tb_desing_timer.v    // this will generate a.out file 
./a.out                                      // after executinon you will be able to see tb_delay_timer.vcd file
gtkwave tb_delay_timer.vcd
```

Waveform of post-synthesis :

![pic_2](https://github.com/rahulrathod10/Synthosphere_design_hackathon/assets/143223452/d759d98d-8fea-4fd9-b9b6-99138c708043)

On comparing the waveforms of pre-synthesis and post-synthesis we obeserve that both the waveforms are same, which implies that the synthesis was successful.





