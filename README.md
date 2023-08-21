# pes_class_asic

**VLSI Physical Design for ASICs**

**Objective**

The objective of VLSI (Very Large Scale Integration) physical design for ASICs (Application-Specific Integrated Circuits) is to transform a logical design description (RTL - Register Transfer Level) into a physical layout that can be fabricated as an integrated circuit. This involves translating the high-level functional representation of the circuit into a physical implementation that meets design constraints, performance targets, and manufacturability requirements.

**SKILL OUTCOMES**



    Architectural Design
    
    RTL Design / Behavioral Modeling
    
    Floorplanning
    
    placement
    
    clock Tree Synthesis
    
    Routing


   ** INSTALLATION**


   https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh


   
    Download the run.sh
    
    Open terminal
    
    cd Downloads
    
    ./run.sh

    **TABLE OF CONTENTS**

**DAY 1**

**Introduction to RISCV ISA and GNU Compiler Toolchain**



**Introduction to Basic Keywords**


**Introduction**



**ISA (Instruction Set Archhitecture)**




    ISA defines the interface between a computer's hardware and its software, specifically how the processor and its components interact with the software instructions that drive the execution of tasks.
    It encompasses a set of instructions, addressing modes, data types, registers, memory organization, and the mechanisms for executing and managing instructions.




**RISC-V (Reduced Instruction Set Computing - Five)**



    It is an open-source Instruction Set Architecture (ISA) that has gained significant attention and adoption in the world of computer architecture and semiconductor design.
    RISC architectures simplify the instruction set by focusing on a smaller set of instructions, each of which can be executed in a single clock cycle. This approach usually leads to faster execution of individual instructions.



![Uploading image.png…]()


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

**Memory Allocation and Stack Pointer**

    Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks.
    The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack.




  **  Labwork for RISCV Toolchain**

**  C Program**

We wrote a C program for calculating the sum from 1 to n using a text editor

#include<stdio.h>

int main(){
	int i, sum=0, n=111;
	for (i=1;i<=n; ++i) {
	sum +=i;
	}
	printf("Sum of numbers from 1 to %d is %d \n",n,sum);
	return 0;
}


![Screenshot from 2023-08-21 19-16-41](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/ffc81637-f8e9-494c-ac0e-169d673ab8c4)


![Screenshot from 2023-08-21 19-17-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/17e9a727-b2f8-4239-bf47-dd0efd96e344)


**RISCV GCC Compiler and Dissemble**


Using the riscv gcc compiler, we compiled the C program.

riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

Using ls -ltr sum1ton.c, we can check that the object file is created.

To get the dissembled ALP code for the C program,

riscv64-unknown-elf-objdump -d sum1ton.o | less .

In order to view the main section, type /main.

Here, since we used -O1 optimisation, the number of instructions are 15.





When we use -Ofast optimisation, we can see that the number of instructions have been reduced to 12



![Screenshot from 2023-08-21 19-26-32](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e89cd311-404f-45fd-9af1-3eadbf64c7dd)




    -Onumber : level of optimisation required
    -mabi : specifies the ABI (Application Binary Interface) to be used during code generation according to the requirements
    -march : specifies target architecture

In order to view the different options available for these fields, use the following commands

go to the directory where riscv64-unkonwn-elf is present

    -O1 :  riscv64-unkonwn-elf --help=optimizer
    -mabi : riscv64-unknown-elf-gcc --target-help
    -march : riscv64-unknown-elf-gcc --target-help

For different instances,

    use the command riscv64-unknown-elf-objdump -d 1_to_N.o | less
    use  /instance to search for an instance
    press ENTER
    press n to search next occurance
    press N to search for p!
revious occurance.
    use esc :q to quit



   ** Spike Simulation and Debug**

spike pk sum1ton.o is used to check whether the instructions produced are right to give the correct output.

   
![Screenshot from 2023-08-21 19-23-35](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/7affce9d-f4e8-417e-ab68-baed0ff87564)









