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



   **INSTALLATION**


   https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh


   
> Download the run.sh
    
> Open terminal
    
> cd Downloads
    
> ./run.sh

**TABLE OF CONTENTS**

**DAY 1**

**Introduction to RISCV ISA and GNU Compiler Toolchain**



**Introduction to Basic Keywords**


**Introduction**



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


When we use -Ofast optimisation, we can see that the number of instructions have been reduced to 12



![Screenshot from 2023-08-21 19-26-32](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/e89cd311-404f-45fd-9af1-3eadbf64c7dd)

> onumber : level of optimisation required

> mabi : specifies the ABI (Application Binary Interface) to be used during code generation according to the requirements
> march : specifies target architecture

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




![Screenshot from 2023-08-22 00-09-56](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/a5778924-b954-4f9e-bee3-de0caf3a20ac)









