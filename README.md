# pes_class_asic

**VLSI Physical Design for ASICs**

**Objective**

The objective of VLSI (Very Large Scale Integration) physical design for ASICs (Application-Specific Integrated Circuits) is to transform a logical design description (RTL - Register Transfer Level) into a physical layout that can be fabricated as an integrated circuit. This involves translating the high-level functional representation of the circuit into a physical implementation that meets design constraints, performance targets, and manufacturability requirements.

**SKILL OUTCOMES**

> Architectural Design


> RTL Design / Behavioral Modeling
    
> Floorplanning

> placement
    
> clock Tree Synthesis

> Routing

</details>

 <details>
 <summary> installation </summary>





   https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh



   
> Download the run.sh
    
> Open terminal
    
> cd Downloads
    
> ./run.sh

</details>

 



 <details>
 <summary> day1 </summary>


**DAY 1**



**Introduction to RISCV ISA and GNU Compiler Toolchain**



**Introduction to Basic Keywords**




**ISA (Instruction Set Archhitecture)**




   >>  ISA defines the interface between a computer's hardware and its software, specifically how the processor and its components interact with the software instructions that drive the execution of tasks.
    >> It encompasses a set of instructions, addressing modes, data types, registers, memory organization, and the mechanisms for executing and managing instructions.




**RISC-V (Reduced Instruction Set Computing - Five)**



    >> It is an open-source Instruction Set Architecture (ISA) that has gained significant attention and adoption in the world of computer architecture and semiconductor design.

    
    >> RISC architectures simplify the instruction set by focusing on a smaller set of instructions, each of which can be executed in a single clock cycle. This approach usually leads to faster execution of individual instructions.


![Screenshot from 2023-08-22 00-06-14](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e0c591c3-668d-42ca-b368-a45f4fbc4a49)



**From Apps to Hardware**


1.**Apps**: Application software, often referred to simply as "applications" or "apps," is a type of computer software that is designed to perform specific tasks or functions for end-users.

2.**System software**: System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs. System software plays a critical role in maintaining the overall functionality, security, and performance of a computer system.'

3.**Operating System:** The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction. Examples of operating systems include Microsoft Windows, macOS, Linux, and Android.

4.**Compiler**: A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.

5.**Assembler**: An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.



6.**RTL**: RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.

7.**Hardware**: Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks

**Detail Description of Course Content**

**Pseudo Instructions**: Pseudo-instructions are used to simplify programming, improve code readability, and reduce the number of explicit instructions a programmer needs to write. They are especially useful for common programming patterns that involve multiple instructions. Ex: li, mv.

**Base Integer Instructions**: The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations. Ex: add, sub, and, or, xor, sll.

**Multiply Extension Intructions**: The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations. Ex: mul, mulh, mulhu, mulhsu.

**Single and Double Precision Floating Point Extension**: The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.

**Application Binary Interface**: ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.

**Memory Allocation and Stack Pointer**: Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks.

The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack.




**Labwork for RISCV Toolchain**

**C Program**

We wrote a C program for calculating the sum from 1 to n using a text editor

![Screenshot from 2023-08-21 19-16-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ffc81637-f8e9-494c-ac0e-169d673ab8c4)


![Screenshot from 2023-08-21 19-17-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/17e9a727-b2f8-4239-bf47-dd0efd96e344)


**RISCV GCC Compiler and Dissemble**


> Using the riscv gcc compiler, we compiled the C program.

> riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum11.o sum11.c

> Using ls -ltr sum1ton.c, we can check that the object file is created.

> To get the dissembled ALP code for the C program,

> riscv64-unknown-elf-objdump -d sum11.o | less .

> In order to view the main section, type /main


When we use -O1 optimisation, we can see that the number of instructions have been reduced to 12



![Screenshot from 2023-08-21 19-23-35](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/017f42ec-9988-4e57-8e84-d959c502e323)



assembly for O1 optimisation:

![Screenshot from 2023-08-22 13-03-05](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/029cdcbc-da59-4b5e-ad39-f477f2937e5f)


When we use -Ofast optimisation, we can see that the number of instructions have been reduced to 12


![Screenshot from 2023-08-21 19-26-32](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e89cd311-404f-45fd-9af1-3eadbf64c7dd)

> onumber : level of optimisation required

> mabi : specifies the ABI (Application Binary Interface) to be used during code generation according to the requirements
> march : specifies target architecture
> 

In order to view the different options available for these fields, use the following commands

go to the directory where riscv64-unkonwn-elf is present

> O1 :  riscv64-unkonwn-elf --help=optimizer
> mabi : riscv64-unknown-elf-gcc --target-help
>  march : riscv64-unknown-elf-gcc --target-help

For different instances,

    > use the command riscv64-unknown-elf-objdump -d 1_to_N.o | less
    > use  /instance to search for an instance
    > press ENTER
    > press n to search next occurance
    > press N to search for p!
    > revious occurance.
    > use esc :q to quit



   ** Spike Simulation and Debug**

spike pk sum11.o is used to check whether the instructions produced are right to give the correct output.

   

![Screenshot from 2023-08-21 19-23-35](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7affce9d-f4e8-417e-ab68-baed0ff87564)




The contents of the registers can also be viewed.






![Screenshot from 2023-08-21 19-39-00](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/71d6f365-57d6-45aa-9583-d5b8f8f75bab)



    press ENTER : to show the first line and successive ENTER to show successive lines

    
    reg 0 a2 : to check content of register a2 0th core

    
    q : to quit the debug process


**Integer Number Representation**

**Unsigned Numbers**


    Unsigned numbers, also known as non-negative numbers, are numerical values that represent magnitudes without indicating direction or sign.
    Range: [0, (2^n)-1 ]


**Signed Numbers**


    Signed numbers are numerical values that can represent both positive and negative magnitudes, along with zero.
    Range : Positive : [0 , 2^(n-1)-1] Negative : [-1 to 2^(n-1)]


**Labwork**


We wrote a C program that shows the maximum and minimum values of 64bit unsigned numbers.






![Screenshot from 2023-08-21 19-53-08](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f731ee24-bac0-4204-8ad0-0771ec016e95)




We wrote a C program that shows the maximum and minimum values of 64bit signed numbers.




![Screenshot from 2023-08-21 19-49-12](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7150533a-ef8f-4219-90da-5d4c4faa8e1b)

</details>

 <details>
 <summary> day2 </summary>


**Application Binary Interface**


**Introduction to ABI**

An Application Binary Interface (ABI) is a set of rules and conventions that dictate how binary code interacts with and communicates with other binary code, typically at the level of machine code or compiled code. In simpler terms, it defines the interface between two software components or systems that are written in different programming languages, compiled by different compilers, or running on different hardware architectures.

The ABI is crucial for enabling interoperability between different software components, such as different libraries, object files, or even entire programs. It allows components compiled independently and potentially on different platforms to work seamlessly together by adhering to a common set of rules for communication and data representation.

**Memmory Allocation for Double Words**

64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly

1.**Little-Endian**: In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.

2.**Big-Endian**: In big-en
dian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.


**For example, consider the 64-bit hexadecimal value 0x0123456789ABCDEF.**
In Little-Endian representation, it would be stored as follows in memory:


![Screenshot from 2023-08-21 23-27-22](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f72a3ffd-d146-4032-9edd-6e43fb67a62f)

In Big-Endian representation, it would be stored as follows in memory:


![Screenshot from 2023-08-21 23-28-40](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f1f3dcf2-7767-4213-b8e3-6828c3171724)

**Load, Add and Store Instructions**

Load, Add, and Store instructions are fundamental operations in computer architecture and assembly programming. They are often used to manipulate data within a computer's memory and registers.

1.**Load Instructions**: Load instructions are used to transfer data from memory to registers. They allow you to fetch data from a specified memory address and place it into a register for further processing.

Example ld x6, 8(x5)

In this Example


    ld is the load double-word instruction.

    
    x6 is the destination register.


    
    8(x5) is the memory address pointed to by register x5 (base address + offset).

2.**Store Instructions**: Store instructions are used to write data from registers into memory.They store values from registers into memory addresses

Example sd x8, 8(x9)


In this Example

    sd is the store double-word instruction.

    
    x8 is the source register.
    8(x9) is the memory address pointed to by register x9 (base address + offset).





3.**Add Instructions**: Add instructions are used to perform addition operations on registers. They add the values of two source registers and store the result in a destination register.

Example add x9, x10, x11

In this Example

add is the add instruction.

x9 is the destination register

x10 and x11 are the source registers


**32-Registers and their ABI Names**

The choice of the number of registers in a processor's architecture, such as the RISC-V RV64 architecture with its 32 general-purpose registers, involves a trade-off between various factors. While modern processors can have more registers but increasing the number of registers could lead to larger instructions, which would take up more memory and potentially slow down instruction fetch and decode.

**ABI Names**

ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components.


![Screenshot from 2023-08-21 23-36-17](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/387ba4f6-d71a-404c-9665-9c011dd69a27)

**Labwork using ABI Function Calls**

**Algorithm for C Program using ASM**

Incorporating assembly language code into a C program can be done using inline assembly or by linking separate assembly files with your C code.

When you call an assembly function from your C code, the C calling convention is followed, including pushing arguments onto the stack or passing them in registers as required.

The program executes the assembly function, following the assembly instructions you've provided.



**Review ASM Function Calls**

We wrote C code in one file and your assembly code in a separate file.

In the assembly file, we declared assembly functions with appropriate signatures that match the calling conventions of your platform.


**C Program** custom1to9.c


![Screenshot from 2023-08-21 23-39-28](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/2dee77a1-ab06-4a65-8004-21a4470cd62b)


**Asseembly File** load.s



![Screenshot from 2023-08-21 23-41-15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/bf0538ef-136a-490e-b1b2-0af77ff21765)


**simulate C Program using Function Call**

**Compilation**: To compile C code and Asseembly file use the command

riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum13.o sum13.c load.s


this would generate object file sum13.o

**Execution**: To execute the object file run the command

spike pk sum13.o


![Screenshot from 2023-08-21 23-17-12](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/129488fb-9b4b-4d0f-94e4-add27f4e2049)

**Lab to Run C-Program on RISCV-CPU**

git clone https://github.com/kunalg123/riscv_workshop_collaterals.git

cd riscv_workshop_collaterals

ls -ltr

cd labs

ls -ltr

chmod 777 rv32im.sh

./rv32im.sh





![Screenshot from 2023-08-22 00-09-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a5778924-b954-4f9e-bee3-de0caf3a20ac

</details>

<details>
<summary> RTL design using Verilog with SKY130 Technology  </summary>

**RTL design using Verilog with SKY130 Technology**

- [Installation](#Installation)

- [Day-1-Introduction to Verilog RTL design and Synthesis](#Day-1--Introduction-to-Verilog-RTL-design-and-Synthesis)

- [Day-2-Timing libs,hierarchical,flat synthesis,efficient flop coding styles](#Day-2-Timing-libs-hierarchical-flat-synthesis-efficient-flop-coding-styles)

- [Day-3-Combinational and sequential optmizations](#day-3-Combinational-and-sequential-optmizations)

- [Day-4-GLS, blocking vs non-blocking and Synthesis-Simulation mismatch](#5-DAY4--GLS-blocking-vs-non-blocking-and-Synthesis-Simulation-mismatch)







## Installation


</details>	
	
 <details>
 <summary> Yosys </summary>
I installed Yosys using the following commands:
     
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
     
Below is the screenshot showing sucessful launch:

![Screenshot from 2023-08-27 12-53-36](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5c3149ca-f742-4ace-8482-ed3054d3e8e1)

</details>
<details>
<summary>Iverilog</summary>

 
**Iverilog**
    
I installed iverilog using the following command:

```
sudo apt-get install iverilog
```

Below is the screenshot showing sucessful launch:



![Screenshot from 2023-08-27 12-57-45](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/c483ee2a-cc49-47b3-9de9-0d4d51f3bf90)


</details>

<details>  
    
<summary> Gtkwave </summary>

I installed gtkwave using the following command:

```
sudo apt-get install gtkwave
```

Below is the screenshot showing sucessful launch:

![Screenshot from 2023-08-27 13-02-36](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/1384eb0f-2eab-438d-8287-7397311e46af)

</details>

# Day-1-Introduction to Verilog RTL design and Synthesis
<details>
<summary>Introduction to Verilog RTL design and Synthesis</summary>

 
**simulator**: tool used for checking the design.
here as per our requirement,we are using iverilog as simulator.

**RTL Design**: RTL esign is checked for implementing spec(required specifications) by simulating design.

**Design**: is actual verilog code or  set of verilog code which has intended functionality to meet with the required specifications

**Testbench**: is the setup to apply stimulus (test_vectors) to the designto check its functionality 
> no primary inputs and primary outputs.

**How simulator works?**

> simulators looks for the chnages on the input signals.



> up on the changes to the input ,the output is evaluated.

here is the representation:


![Untitled](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3598724c-3d53-48dd-a561-536312f3b7ca)




![Untitled1](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/84f67c59-8559-4bdd-a3a3-1920bc34f82c)

### Lab examples using iverilog and gtkwave


![Screenshot from 2023-08-27 13-52-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/827f4903-e4ce-4c4c-9a19-69f95caba993)

good_mux.v and tb_good_mux.v are already present in verilog_files.

**good_mux and tb_good_mux**<br />

	module good_mux (input i0 , input i1 , input sel , output reg y); 
		always @ (*)
		begin
			if(sel)
			y <= i1;
			else 
			y <= i0;
		end
	endmodule


	`timescale 1ns / 1ps
	module tb_good_mux;
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;
      		// Instantiate the Unit Under Test (UUT), name based instantiation
		good_mux uut (.sel(sel),.i0(i0),.i1(i1),.y(y));
		//good_mux uut (sel,i0,i1,y);  //order based instantiation
	initial begin
		$dumpfile("tb_good_mux.vcd");
		$dumpvars(0,tb_good_mux);
		// Initialize Inputs
		sel = 0;
		i0 = 0;
		i1 = 0;
		#300 $finish;
	end
	always #75 sel = ~sel;
	always #10 i0 = ~i0;
	always #55 i1 = ~i1;
	endmodule


**commands used to execute the gtkwave :**
> iverilog good_mux.v tb_good_mux.v

> ./a.out

> gtkwave tb_good_mux.vcd


![Screenshot from 2023-08-27 13-49-55](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/69849729-78ba-44bb-850f-585c877a412b)



**for extracting the file structure , use command:**
gvim tb_good_mux.v -o good_mux.v


![Screenshot from 2023-08-27 14-57-10](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/b4fb4392-355b-43cf-9bfe-5d38da79bb1c)


</details>

<details>
 <summary> Introduction to Yosys synthesizer </summary>

**synthesizer**: tool used for converting thr RTL to netlist
here we are using synthesizer called **yosys**

**netlist**: representation of design in the form of standard cells present in **.lib**

**.lib**contains standard cells to implement any boolean logic functionality.in other words we can say :
>  collection of logical modules


> includes basic logic gates like And ,or , not, etc


![Untitled4](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d1a91244-eb61-4d22-acff-aedd5f6197a5)





**flow:**

![Untitled2](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/6c4bdc5c-ee7f-4653-a1fb-83da5431cb51)


**yosys setup:**

![Untitled3](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/31c602bd-d703-44ea-bd00-3252efd281d0)

**commands:**


> read_verilog: to read the design



> read_liberty: to read .lib




> write_verilog: to write out the netlist file



**how to verify the synthesis:**


we go back to the simulator iverilog :
![Untitled1](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ea579bb3-3332-4b48-9d55-e937ab3821c5)

**NOTE:**


>   the stimulus should be same as out put observed during RTL simulation


>   the set of primary inputs /primary outpuuts will remain same between the RTL design and Synthesized netlist ,meaning "same test bench can be used for both RTL design and Synthesized  netlist"





**Introduction to loigc synthesis**:  

 **RTL design**
>  behavioral representation of the required specifications

**how to map RTL design to the circuit?**
--->  here comes the synthesis:

>  RTL to gate level translation is calles as **synthesis**


> the design is converted into gates and the connections are made between the gates,and this is given out as a file called netlist


![Untitled5](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/256328bb-d698-42bb-aadc-24b5aec11120)


**why faster nd slower cells?**

>  To meet set up time we want cells to be faster cells and we want slower cells  to meet the hold time 

**Faster Cells vs Slower Cells**: Load in digital circuit is of Capacitence. Faster the charging or dicharging of capacitance, lesser is the celll delay. However, for a quick charge/ discharge of capacitor, we need transistors capable of sourcing more current i.e, we need WIDE TRANSISTORS.

Wider transistors have lesser delay but consume more area and power. Narrow transistors are other way around. Faster cells come with a cost of area and power.

**Selection of the Cells**: We'll need to guide the Synthesizer to choose the flavour of cells that is optimum for implementation of logic circuit. Keeping in view of previous observations of faster vs slower cells,to avoid hold time violations, larger circuits, sluggish circuits, we offer guidance to synthesizer in the form of Constraints.

Below is an illustration of Synthesis.



![Screenshot from 2023-08-27 16-15-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0116516b-1a12-4c1a-ba87-57bfa5bbcf29)



### Labs on Yosys introduction
**Invoking Yosys:**


![Screenshot from 2023-08-27 16-21-05](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5fbfdb56-c2c9-41c3-8e84-34e7d9d5f582)


>  read_liberty -lib /path to .lib file/ // It reads all the components in the .lib file


![Screenshot from 2023-08-27 16-37-36](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/1e04c520-eb47-4323-8068-f080250b1f6d)


>  read_verilog good_mux.v // This will read the desgn verilog file



![Screenshot from 2023-08-27 16-42-23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/767f9f65-c56b-4734-b646-0d8855c9022b)

the command to synthesize the module sprcifies:
>    synth -top good_mux




![Screenshot from 2023-08-27 16-48-15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/86eaa210-1832-48f3-b883-24c56b52621e)

The command to generate the netlist file based on the .lib file mentioned
>  abc -liberty /path to .lib file

![Screenshot from 2023-08-27 17-25-47](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f65d5bda-8c7c-4963-b96a-7f4e5b5fedb4)

>  show command is used to see the synthesised output/netlist





![Screenshot from 2023-08-27 17-28-09](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/929e81de-2681-413a-bfc5-f3de2f62ad44)



the command to write the netlist :
>  write_verilog good_mux_netlist.v

![Screenshot from 2023-08-27 17-37-43](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/fcd28e01-98fe-4b88-9b6f-b39c864f0b7d)


**for extracting the file structure , use command:**
>  !gvim good_mux_netlist.v




![Screenshot from 2023-08-27 17-39-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/33304357-08c0-4b7b-9e30-68e75e62e119)


the command or switch to use ,to get netlist in simple way
>  write_verilog -noattr good_mux_netlist.v

and then, use command:

>  !gvim good_mux_netlist.v



![Screenshot from 2023-08-27 17-47-14](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a8d215e9-d5e1-4506-abd6-73712f444810)



![Screenshot from 2023-08-27 17-46-44](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ebfb8c29-ae5f-401d-bfe6-f4e33bca1cb0)



</details>

# Day-2-Timing libs, hierarchical, flat synthesis, efficient flop coding styles
<details>
<summary>Introduction to timing .libs</summary>

### LAB- Introduction to dot Lib


**command to extract .lib**

>  gvim /path

![Screenshot from 2023-08-27 22-35-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/b8dc818e-9de9-445c-8925-b49fd87e4da6)



![Screenshot from 2023-08-27 22-37-00](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/4cb62ba4-544d-4ea8-9ef1-dc6857f0359f)

use **syn off** command to vanish the color



 ![Screenshot from 2023-08-27 22-39-45](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/fc66d50e-2903-4740-aa27-91946dd3a2b6)

 as per above **.lib** file the first line represents the name of the library
 and the above library is 130nm .


 PVT -->  **P**rocess  **V**oltage **T**emperature ,important for design to work .
in the above library that is... 
 **sky130_fd_sc_hd__tt_025C_1v80**



 > **tt** stands for typical process




> **025c** tands for temperature




>  **1v80**stands for voltage


> technnology used --> CMOS





>> and the libreies are characterised to model these variations.



the command  **:/cell**  marks the main cells 


![Screenshot from 2023-08-27 22-55-26](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7521dcd7-c28b-4793-9111-ed4ad094d4b8)


example:if the command **:/cell .*and***  is given then,it highlights the cell called **and**


![Screenshot from 2023-08-28 05-29-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ecaf939a-e5a5-4cbd-9252-7b4f71eb7b33)



**what does the library contains?**


**here are some features:**

>  different flavour of different cells and different flavour of same cells.


> leakage_power


>  area number



>  power port information


> each input pin information


>transition and delay associated with the cell


> timing information


>   etc

![Screenshot from 2023-08-28 04-57-43](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d4a76142-a353-4c50-b414-c99c2a2bd4de)







![Screenshot from 2023-08-27 23-03-09](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/156cadfe-07b1-462c-96ab-bd3590a61d18)



To check equivalent verilog model of the particular cell use command **path.behavioral.v** (without power ports(pp))



**here is the different flavour of "and" cell:**





![Screenshot from 2023-08-28 05-42-24](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/63e3992d-9e70-41bf-b176-496e18c41536)


from here we can observe that in terms of area,power **and2_4 > and2_2 > and2_0**
and we can also observe that in term of delay **and2_4 < and2_2 < and2_0**

>  this means and2_4 has **wider transistors** hence cell **and2_4** is **fast** and has **more area**

>  and  and2_0 has **narrow transistors** hence cell **and2_0** is **slow** and has **less area**




</details>

 <details>
<summary> LAB- Hierarchical synthesis and flat synthesis </summary>

**multiple_module**<br />

	module sub_module2 (input a, input b, output y);
		assign y = a | b;
	endmodule
	
	module sub_module1 (input a, input b, output y);
		assign y = a&b;
	endmodule


	module multiple_modules (input a, input b, input c , output y);
	wire net1;
	sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
	sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
	endmodule

 command used:
 >  gvim multiple_modules.v

 


![Screenshot from 2023-08-28 06-34-54](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ab8abf80-7384-45ec-af9b-ac30de7136ed)


**commands used:**

> yosys --> to invoke yosys




> read_liberty -lib /path



> read_verilog multiple_modules.v




> synth -top multiple_modules





> abc -liberty /path




> show multiple_modules




![Screenshot from 2023-08-28 06-50-03](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/cf0c7276-48bd-4afc-b599-4794c181e2a2)





![Screenshot from 2023-08-28 06-50-48](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/793bc266-12e8-41aa-a363-7ca4e8f9cd8a)




![Screenshot from 2023-08-28 06-51-15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/793e503b-2cce-4db7-a0f7-c5ceb2919445)





![Screenshot from 2023-08-28 06-51-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/102b3923-d785-45b7-b8f7-84be72b83c6d)




 ![Screenshot from 2023-08-28 06-51-50](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/aa54ea61-eae6-4121-98cc-d27fe12e0904)



 




ideally we are expected to see **AND** and **OR** gates 




![Untitled7](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7ee80417-f2ac-474d-9c0d-e40fb5d1df16)











but we are getting it as **sub_module1**--u1 and **sub_module2**--u2 so, this what we call **Hierarchical synthesis**


![Screenshot from 2023-08-28 07-04-19](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e59481a5-17fa-4e72-9ffc-a2d4927b59e1)



**to view the netlist commands used:**


> write_verilog -noattr multiple_modules_hier.v


> !gvim multiple_modules_hier.v




![Screenshot from 2023-08-28 07-15-33](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f3ae9be0-82e8-46ea-80cd-6516c0f6b1eb)






![Screenshot from 2023-08-28 07-18-30](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a0c65c35-64b1-47bf-9d05-02264de63b95)


![Screenshot from 2023-08-28 16-19-17](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/aab1dd4d-e10a-4e3d-95c1-2ecae2b6d1b1)



--> hierarchies are preserved


**flatten** is the command to write flat netlist



![Screenshot from 2023-08-28 16-35-50](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/35ae3f48-73c9-4cf8-bebd-040b181ec29f)






![Screenshot from 2023-08-28 16-52-01](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/69a1fe8a-928f-4f0f-a9e4-719aa246b37a)





![Screenshot from 2023-08-28 16-38-55](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/2346d895-12b6-4b52-9319-1cd67623cd0c)


>  the hierarchies of sub_module1 and sub_module2 are preserved in **multiple_modules_hier.v**


>  whereas in the **multiple_modules_flat.v**  we dont see them ,we can see the single netlist meaning hierarchies are flattened off




![Screenshot from 2023-08-28 17-09-39](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/64a801ae-728b-4766-b57f-0a57b77d004e)


> since we have flattened the multiple_modules.v we dont see any **u1 sub_module1** and **u2 sub_module2** 

> when we flatten we directly see the structure completly



**To obtain only sub_module1 :**

> invoke yosys



> read_liberty -lib /path



> read_verilog multiple_modules.v


> **synth -top <module1_name>**


> abc -liberty /path


> show



![Screenshot from 2023-08-28 17-22-53](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f66f732f-4e11-470b-9a0d-b7b7f77e0924)

**we can observe synth -top sub_module1** is only providing the info about sub_module1



![Screenshot from 2023-08-28 17-25-23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/8453c19f-909c-4bb2-8164-5c0a776559d9)


**Reason why we use sub module level synthesis:**

> sub module level synthesis is used when we have multiple instance of same module

> divide and conquer


</details>
 
<details>
	<summary>Various Flop coding styles and optimization</summary>

 **why flops?**

>  if inputs are given ,ouputs appears after some propogation delay ,because of propogation delay the outputs will have some glitches.


>  more the number of combinational circuit more the glitch so ,we should avoid this glitch

> hence we need element to store the value of glitch ,and the element is called as **flops**


--> the output of the flop changes only on the edge of the clock,means if the input is glitching the output will be stable,meaning the stable output is given next combinational circuit then the output of the combinational circuit will also be stable.

**therefore this the main purpose of using flops in the digital circuit.**

**how to code the flops?**


> To initialize the flop ,there are control pins on the flop like **reset or set**

> these reset and set can either be **synchronous or asynchronous**

**module dff_asyncres**<br />


        module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
	    always @ (posedge clk , posedge async_reset)
	    begin
		      if(async_reset)
			    q <= 1'b0;
		      else	
			     q <= d;
	    end
        endmodule

**asynchronous reset:**

**Simulation**




![Screenshot from 2023-08-28 23-03-46](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/c2bd28bd-3dd1-4c0e-937d-290ed8fa767e)

      


![Screenshot from 2023-08-28 23-03-20](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0c024648-608b-4cb4-a34e-26605b85a75d)

**synthesis**:

![Screenshot from 2023-08-29 07-38-17](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/af7a6705-e68f-41a0-8232-21a2b4e5dbce)


![Screenshot from 2023-08-29 07-38-59](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/8870df11-3927-4c47-b061-840d3d2de542)


![Screenshot from 2023-08-29 07-41-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3f0d8242-554c-47da-8394-1996e481e806)

**asynchronous set:**


**module dff_asyn_set**<br />


             module module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
	         always @ (posedge clk )
	         begin
		           if (sync_reset)
			         q <= 1'b0;
		           else	
			         q <= d;
	         end
             endmodule


**simulation**






![Screenshot from 2023-08-28 23-21-24](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d7bfb2c3-6167-4fed-9893-b3c2b1bd8c71)





![Screenshot from 2023-08-28 23-21-08](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0de0514b-85f9-4f4a-889f-bc3f439bf7dd)

**synthesis**


![Screenshot from 2023-08-29 07-46-58](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/66f34fd1-4c1b-4bbe-a0f8-7164c4a8f235)



![Screenshot from 2023-08-29 07-48-52](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/63624db9-cc20-4808-8d6c-8ff62a2b6b37)




![Screenshot from 2023-08-29 07-49-34](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3f002be2-a3b1-48e2-8577-64eb34309a42)

**synchronous reset:**


**module dff_syncres**<br />

          module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
	         always @ (posedge clk )
	         begin
		    if (sync_reset)
			  q <= 1'b0;
		    else	
			  q <= d;
	          end
          endmodule

**simulation:**




![Screenshot from 2023-08-29 07-24-45](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/655170d2-e717-45fb-aa2c-0a819d8f280c)



![Screenshot from 2023-08-29 07-25-10](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/9044ab16-a2ea-4a5e-83b8-f169dcb2d7fe)



here even if reset went high output **q** is not going low immediately it is waiting for subsequent **clock edge** and then it is going low.means the reset is applied up on the positive edge of the clock  ---> synchronous reset


**synthesis**




 ![Screenshot from 2023-08-29 07-56-09](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0479467e-70d1-4aad-90af-458a7a89e2c3)







![Screenshot from 2023-08-29 07-55-47](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/1f825bcf-ce62-4bf3-883f-9b3cd8fc74b6)






![Screenshot from 2023-08-29 07-56-28](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5a547c19-d88e-444b-adee-b4bab099cc86)


**interesting optimization**

multiplying a number with 2 doesn't need any additional hardware and only needs connecting the bits from a to y and grounding the LSB bit of y is enough 


**module mul2**<br />

      module mul2 (input [2:0] a, output [3:0] y);
	      assign y = a * 2;
      endmodule

**synthesis:**


![Screenshot from 2023-08-29 08-14-18](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ed11e3b1-d0a4-45d8-acf1-e28b289d6a48)



**netlist**

![Screenshot from 2023-08-29 08-33-06](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/02d716a7-e646-46c4-9cdf-75fc9815eac9)


**special case**

take **a** as 2 bit number a[2:0] and y as 6 bit number y[6:0]

let the relation between them be **a*9=y**


**synthesis**:

![Screenshot from 2023-08-29 08-40-57](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/b142d2f5-fa15-4e42-967b-40548858dca1)


**netlist**:



![Screenshot from 2023-08-29 08-43-15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e4dad4a1-81ea-4a8d-99c7-643c0ff69b76)

</details>





# Day-3-combinational and sequential optmizations
<details>
<summary>introduction to optimizations</summary>


 **In digital logic we have two types logics,namely:**

 
 > combinational logic


 > sequential logic


**why combinational logic optimization?**

>  To squeez the logic to get the most optimized design



-->optimized design will be more efficient in terms of area and design


**Techniques used for combinational logic optimization**

> constant propagation --> direct optimization

> boolean logic optimization --> using techniques like K-map or  quine McKlusKey


**Example for Constant propogation** --> direct optimization


![Untitled10](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d4b54749-9992-49cd-bb07-03aa54c93144)

for example: **Y=(AB+C)'**

**realization in terms of CMOS**



![Untitled11](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ed36cc20-cab6-4523-99f0-c53e99bbe142)

for the example given we need 6 transistors but after simplifing we got inverter which has only two transistor that has less area and power .


**i.e., effectively the zero on A got propogated down the logic**



**Example for boolean logic optimization**


assign Y=a?(b/c:(c?a:0)):(!c)



![Untitled12](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/9d79c1b5-09a4-46c4-bad3-b88710ccbfde)





ternary operator is like **MUX**

output of MUX1 is **ac+c'.0=ac**

output of MUX2 is **b'ac+bc**

output of MUX3 is **z'c'+a[bc+b'ac]=a'c'+abc+ab'c =a'c'+ac[b+b'] =a'c'+ac**

Therefore the complicated equation  **Y=a?(b/c:(c?a:0)):(!c)** is simplified or optimized logic **a'c'+ac**


**sequential logic optimizations**

techniques:

>  basic

--> sequential constant propogation

> Advanced optimization

--> state optimization


--> retiming 


--> sequential logic cloning (floor plan Aware synthesis)

**sequential constant**

-- if there is a reset then Q=0

-- if reset is not there then also Q=0 because D=0


![Untitled13](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/99efbb6b-7d4b-422d-aa5a-5ec9a761a2da)


basically Q is always zero whether we apply clock or reset

and,

--y is always 1 irrespective of clock ,reset,Q because of sequential constant

>  if set clock connected to the circuit


**when we apply set**


![Untitled14](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a3edc2fe-928c-47ff-a1d9-8f8c446691ab)


-- when set is applied Q=1


-- when set is not applied and there is a clock Q=0

-- every flop with D input is not a sequential constant ,for clock to become sequential constant  Q pin should always take constabt value

**Advanced optimizations:**


**state optimization,cloning,retimimg**

-- optimization of unused state is called **state optimization**

--logic is done when we are doing physical aware synthesis **cloning**

--technique to improve performance of the circuit **retiming**

</details>

 <details>
<summary>LAB- combinational logic optimizations</summary>

### we are going to use opt files(*opt_check*) in this lab


command to do the optimizations is **opt_clean -purge**

1) **opt_check**<br />

        module opt_check (input a , input b , output y);
	        assign y = a?b:0;
        endmodule


   **synthesis**

   
![Screenshot from 2023-08-29 23-03-46](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/4b0f954b-cfb4-4b7b-b89c-ed2176b02a75)




![Screenshot from 2023-08-29 23-03-55](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/c6038f17-d119-4eed-8be3-494509e05d7d)





![Screenshot from 2023-08-29 22-23-03](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/c8f707ca-a40a-4e4f-ade0-a8ff9a0e8871)



2) **opt_check2**<br />


        module opt_check2 (input a , input b , output y);
	        assign y = a?1:b;
        endmodule


**synthesis**




![Screenshot from 2023-08-29 23-11-18](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5f92f1d5-e14d-41b4-b656-882ea67478e5)



![Screenshot from 2023-08-29 23-11-29](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f2d45181-c94e-47a4-b9db-ac9c9104a503)




![Screenshot from 2023-08-29 23-11-54](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/99a84b1b-f6d7-474c-84c0-f17a3d271703)


3) **opt_check3**<br />
           module opt_check3 (input a , input b, input c , output y);
	           assign y = a?(c?b:0):0;
           endmodule


**synthesis**

![Screenshot from 2023-08-29 23-18-11](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d30f4124-ae8f-4fa7-bf4c-6b5949ab7964)



4) **opt_check4**<br />


           module opt_check4 (input a , input b , input c , output y);
	           assign y = a?(b?(a & c ):c):(!c);
           endmodule


**synthesis**



![Screenshot from 2023-08-29 23-24-55](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ebeb90bc-500f-4ded-871d-5269a1457f29)


5) **multiple_modules_opt**<br />

	           module sub_module1(input a , input b , output y);
	                  assign y = a & b;
	           endmodule

	           module sub_module2(input a , input b , output y);
	            assign y = a^b;
	           endmodule

	           module multiple_module_opt(input a , input b , input c , input d , output y);
	           wire n1,n2,n3;
	           sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
	           sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
	           sub_module2 U3 (.a(b), .b(d) , .y(n3));

	           assign y = c | (b & n1); 
	           endmodule

synthesis with out **flatten**


![Screenshot from 2023-08-29 23-46-45](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/dd13a357-2a44-455d-9a47-74ea27e5dc2f)



![Screenshot from 2023-08-29 23-45-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/dee0f7d4-1073-4c03-a6cb-743d483c146d)



synthesis with **flatten**:

![Screenshot from 2023-08-29 23-53-15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/48a71d19-54e4-42c1-bd5c-25410d40460a)


![Screenshot from 2023-08-29 23-53-34](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0c1dba52-b427-4230-822f-e2a48e70760d)


6) **multiple_module_opt2**<br />

		                     module sub_module(input a , input b , output y);
			                     assign y = a & b;
		                     endmodule
		
		                     module multiple_module_opt2(input a , input b , input c , input d , output y);
			                    wire n1,n2,n3;
			                    sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
			                    sub_module U2 (.a(b), .b(c) , .y(n2));
			                    sub_module U3 (.a(n2), .b(d) , .y(n3));
			                    sub_module U4 (.a(n3), .b(n1) , .y(y));
		                     endmodule


synthesis without **flatten**


![Screenshot from 2023-08-29 23-59-14](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f85da66b-589a-4985-b43f-06e97cdb5b53)


synthesis with **flatten**


![Screenshot from 2023-08-30 00-01-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/268d6f00-bb1f-4b41-93a7-1f69d1edc313)



</details>

<details>
<summary>Lab-Sequential Logic Optimization with examples</summary>

files are present in **dff*const**

1) **dff_const1**<br />
		
		         module dff_const1(input clk, input reset, output reg q);
			         always @(posedge clk, posedge reset)
			         begin
				     if(reset)
				 	     q <= 1'b0;
				     else
					     q <= 1'b1;
			         end
		         endmodule

 **simulation:**


![Screenshot from 2023-08-31 05-41-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/82d11f90-80e7-4084-9811-358bce5a156e)


> up on reset Q is 0 and else Q is 1



>removal of reset doesnot mean that that Q is going to change Q will wait for next clock edge


![Screenshot from 2023-08-31 05-52-14](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/8c5806a7-83bf-4526-8181-cb98be9e0451)

> we canobserve that Q is waiting for nexst clock edge



**synthesis:**


**dfflibmap -liberty /path** command is going to tell what liberary it has to use

![Screenshot from 2023-08-31 06-14-09](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/96df8b61-4531-4ec7-a473-319c1f8a481d)

here  while printing the statistics it has infered a dff


![Screenshot from 2023-08-31 06-07-57](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e71f1a5a-4971-4646-a427-73fd8ef9e1fb)

> here the 2nd standard cell liberary is expecting reset to be low but we have active high  so the tool is infering the inverter

2) **dff_const2**<br />

		              module dff_const2(input clk, input reset, output reg q);
			              always @(posedge clk, posedge reset)
			              begin
				         if(reset)
					         q <= 1'b1;
				         else
					         q <= 1'b1;
			               end
		               endmodule


**simulation**:


![Screenshot from 2023-08-31 05-53-51](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a3c4993b-fed1-444c-9f79-e2b299de3341)



> flop which is have set

> here if there is reset instead of set it acts as set and changes the value of Q

> even if we remove the rest Q value continues to be in 1 and at the edge of the it continues to be in 1 sice d is 1


![Screenshot from 2023-08-31 05-59-00](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3e40a9c5-9648-425c-a750-ad344fe27012)

> we can observe value of Q is 1 irrespective of clock and reset

**synthesis:**



![Screenshot from 2023-08-31 06-18-23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/c1171e07-4420-451f-928e-6ce1f2082835)


here  while printing the statistics it has not infered a dff since Q value will change with respesct to reset or clock




![Screenshot from 2023-08-31 06-17-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/f4f734e2-3578-4b87-b6a9-70e2c0741b0d)

here we observe there is no flop.



3) **dff_const3**<br />

			module dff_const3(input clk, input reset, output reg q);
			reg q1;
		
			always @(posedge clk, posedge reset)
			begin
				if(reset)
				begin
					q <= 1'b1;
					q1 <= 1'b0;
				end
				else
				begin
					q1 <= 1'b1;
					q <= q1;
				end
			end
			endmodule


> up on reset Q there are two clock both are getting same clocks and reset



**simulaton**



 

![Screenshot from 2023-08-31 06-32-29](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7376c5ef-aa9e-4832-bba6-8b999b27755f)


**synthesis**

![Screenshot from 2023-08-31 06-39-42](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5f994540-8287-4350-8d92-494e0fda7079)



![Screenshot from 2023-08-31 06-34-53](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0043992b-94af-430c-bd2d-17a91ed5e6ec)





![Screenshot from 2023-08-31 06-34-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7cde2817-61fe-47a6-841e-c675c6b232f8)


4) **dff_const4**<br />
			module dff_const4(input clk, input reset, output reg q);
			reg q1;
		
			always @(posedge clk, posedge reset)
			begin
				if(reset)
				begin
					q <= 1'b1;
					q1 <= 1'b1;
				end
			else
				begin
					q1 <= 1'b1;
					q <= q1;
				end
			end
			endmodule






**simulation**

![Screenshot from 2023-08-31 19-53-48](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a83a7ec2-6613-48a7-ae4a-40b8b46790f1)


**synthesis**


![Screenshot from 2023-08-31 20-01-38](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/43a0d41b-1beb-4750-8270-105e225c02d4)


![Screenshot from 2023-08-31 20-02-19](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/d1ce1ee3-8103-42a3-8b29-add13dbf04fa)


5) **dff_const5.v**<br />
			module dff_const5(input clk, input reset, output reg q);
			reg q1;
			always @(posedge clk, posedge reset)
				begin
					if(reset)
					begin
						q <= 1'b0;
						q1 <= 1'b0;
					end
				else
					begin
						q1 <= 1'b1;
						q <= q1;
					end
				end
			endmodule


**simulatiom**



![Screenshot from 2023-08-31 20-05-55](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/5e372c9a-98bd-4fb5-b2a3-3a05cf28897b)

**synthesis**



![Screenshot from 2023-08-31 20-07-36](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/faebc123-27b1-49b1-a20c-38bda91c74d4)



![Screenshot from 2023-08-31 20-09-00](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/68a664fd-5155-462e-a991-3ed8d6bac950)




![Screenshot from 2023-08-31 20-08-50](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/9bc67241-a16f-4732-9280-5250d9574b0e)



</details>

<details>
<summary>Sequential optimizations for unused outputs</summary>
	
1) **counter_opt**<br />
			
				module counter_opt (input clk , input reset , output q);
				reg [2:0] count;
				assign q = count[0];
				always @(posedge clk ,posedge reset)
				begin
					if(reset)
						count <= 3'b000;
					else
						count <= count + 1;
				end
				endmodule

> there is only one flop even it is 3 bit counter

> only one output is used and other two are unused means there is no dependency of 3rd output on uther two outputs

> any logic which is not resulting in any realtionship with primary output  will be optimized



**simulation**



![Screenshot from 2023-09-01 10-36-24](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/601848d7-7c62-4195-ab8a-1705290ab01b)



**synthesis**


![Screenshot from 2023-09-01 10-45-10](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3e0dbf7a-cc45-45c6-b986-72558340b627)


![Screenshot from 2023-09-01 10-45-23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/025ac57b-2ea5-4376-bf1a-760068cb2f86)




![Screenshot from 2023-09-01 10-45-31](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/385321a8-63c6-4f65-adad-059cf3d3f000)

> here we can observe that q is not of Q

> unused bits are completely optimized  because they are not connected to any primary output.


2) **module counter_opt2**<br />

					module counter_opt (input clk , input reset , output q);
							reg [2:0] count;
							assign q = {count[2:0]==3'b100};
							always @(posedge clk ,posedge reset)
							begin
							if(reset)
								count <= 3'b000;
							else
								count <= count + 1;
							end
					endmodule
					


![Screenshot from 2023-09-01 10-56-12](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/53c1b5cc-f693-4ed5-aac5-4a0d52f36edf)


> here we can observe that it infered 3 dff 


 
![Screenshot from 2023-09-01 10-57-23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/0f26031a-1e0e-4e61-8b01-f99569bb9b93)

![Screenshot from 2023-09-01 10-56-54](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/3fe6f91c-998e-4f71-933f-f374f7321ad7)

> in the previous example only one bit i.e., c[0] was used


> where as here all the 3 bit are getting used and a;; the dff are preserved




</details>


## Day-4-GLS,blocking vs non-blocking and Synthesis-Simulation mismatch

<details> 
<summary>GLS, Synthesis-Simulation mismatch and Blocking, Non-blocking statements</summary>


### GLS concept and flow using Iverilog

**GLS - Gate Level Simulation**

**What is GLS?**


--> Running the test bench with netlist as design under test


> netlist is logically same as RTL code,input and output in netlist and RTL code are same therefore nerlist will fit in the testbench

> now we will plug the nelist in place of RTL file and run the simulation



**why GLS?**

>  verify the logical correctness of gesign after synthesis

> Ensuring the timing of the design is met

--> for this GLS needs to be run with delay annotation.

**GLS using Iverilog**


![Untitled15](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/59dc0a1c-bdef-4dca-989e-e8497e0f988a)


**NOTE**



if the Gate Level Models are delay annotated ,then we can use  GLS for timimg validation


the current GLS model what we are using are basic(functional) and not timing aware therefore we are not using the timing validation


 if the netlist is true representation of RTL,**why validation of functionality of netlist?**

--> here comes the concept called **Synthesis Ans Simulation Mismatch**


### Synthesis Ans Simulation Mismatch

why there is mismatch of synthesis and simulation

> missing sensitivity list

> blocking vs Non blocking Assignments

> Non standard verilog code


**Missing Sensitivity**

Example:<br />

		module mux(
		input i0,input i1,input sel,ouput reg y);
		always@(sel)
		begin
		if(sel)
		       y=i1;
		else
		       y=i0;
		end 
		endmodule


  here we can only when select is changing the output is changing.here when i1 and i0 is changing the output is not changing

  the RTL looks like latch 


   **this what we call as missing sensitivity list**



   ### Blocking and Non blocking statements in verilog

Blocking and Non blocking statements are inside the always block 

> **Blocking (=)**

-- executes the statements in the order it is written 


-- so the first statement is evaluated beforee the second statement

here behaviour is like c programming

> **Non-blocking (<=)**


-- executes parallely .order doesnot matches
-- executes all the RHS when always block is entered and assigns to LHS.


**Caveats with Blocking Statements**
<br />
		module code (input clk,input reset,input d,output regd);
		reg q0;
		always@(posedge clk,posedge reset)
		begin
		if(reset)
		begin
		   q0=1'b0;
		   q=1'b0;
		end
		else
		begin
		   q=q0
		   q0=d;
		end 
		endmodule

  this executes well! and it has two flops
  but,

  <br />

               module code (input clk,input reset,input d,output regd);
		reg q0;
		always@(posedge clk,posedge reset)
		begin
		if(reset)
		begin
		   q0=1'b0;
		   q=1'b0;
		end
		else
		begin
		   q0=d;
		   q=q0;
		end 
		endmodule

  here as we know executes the statements in the order it is written ,in the else part q0 is having value of d and q is having the value qo bot q0 since q0 is alreadt having the value assigned     and it provides only one flop. here comes the problem

  

  







   
   
			


